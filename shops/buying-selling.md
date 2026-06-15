---
description: How ZaminShop calculates quantities, prices, inventory changes, command side effects, and sell matching.
---

# Buying and Selling

This page explains what happens after a player clicks a transactional shop item.

## Transaction quantity

`quantity` is the base unit for a shop entry:

```yaml
items:
  'diamond_bundle':
    type: SHOP_ITEM
    material: DIAMOND
    quantity: 16
    buy-price: 2400
    sell-price: 800
```

One normal purchase buys 16 diamonds for 2400 currency units. One normal sale sells 16 matching diamonds for 800.

## Buy-only and sell-only intent

The current loader defaults an omitted price to `0`. A zero price is a free transaction, not a disabled direction.

{% hint style="warning" %}
**Needs verification in code:** a loader diagnostic says omitting a price disables that direction, but the inspected implementation currently returns `0` for a missing price. Validate the exact build before publishing buy-only or sell-only entries.
{% endhint %}

## Buying a physical item

The transaction service checks, among other things:

* the shop and item are accessible;
* the player is not already inside a conflicting transaction;
* a registered provider and positive price resolve for the action;
* the amount and price pass `currency.yml` safety rules;
* Overwatcher does not block the shop/item;
* the economy can withdraw the price;
* the inventory can accept the result;
* configured sell limits and suspicious-transaction controls do not refuse the operation;
* event listeners do not cancel the transaction.

After success:

* the item is added;
* the economy is charged;
* Runtime Shield can stamp delivered physical items;
* recent history can be updated;
* audit and transaction logs can be written;
* configured player and console commands can run;
* a post-transaction event is fired.

If the operation fails after changing money or inventory, the transaction layer attempts rollback.

## Selling a physical item

Selling requires a matching `SHOP_ITEM`. The match uses:

* material;
* integrated provider identity where applicable;
* metadata when `compare-meta` is enabled;
* model data when `compare-model` is enabled;
* damage when `compare-damage` is enabled;
* NBT when `compare-nbt` is enabled;
* repair cost when `compare-repair-cost` is enabled.

Hooked providers compare their own IDs. For example, HeadDatabase compares the HeadDatabase ID on both stacks.

Before a matching physical item is sold, Runtime Shield can verify its ZaminShop purchase fingerprint and block a profitable resale within the same currency provider.

## Currency resolution

The transaction provider is resolved in this order:

1. item `currency-provider`;
2. pack `currencies`;
3. provider IDs present in provider-specific item prices;
4. the category's legacy `economy`;
5. `currency.yml` `default-provider`.

When several providers have a positive price for the action, the currency selection menu opens.

See [Multi-Currency Shops](multi-currency.md).

## Per-entry GUI behavior

```yaml
items:
  'diamond':
    type: SHOP_ITEM
    material: DIAMOND
    quantity: 1
    buy-price: 500
    sell-price: 125
    close-gui-on-click: false
    enable-buy-gui: true
    enable-sell-gui: true
    enable-buy-more-gui: true
    enable-sell-more-gui: true
```

These values override the category and global settings for this entry.

## Per-entry messages

```yaml
items:
  'diamond':
    type: SHOP_ITEM
    material: DIAMOND
    quantity: 1
    buy-price: 500
    sell-price: 125
    message-buy: "&aPurchased %amount%x %item% for %price%."
    message-sell: "&aSold %amount%x %item% for %price%."
    message-sell-all: "&aSold all %amount%x %item% for %price%."
    message-cannot-afford: "&cYou need %price%."
```

When absent, category-level messages are used. When category messages are absent, language defaults are used by the transaction flow.

## Commands around transactions

Commands can run on click, after a buy, or after a sale.

Player commands:

```yaml
commands-on-click:
  - "me inspected the diamond offer"
commands-on-buy:
  - "me purchased diamonds"
commands-on-sell:
  - "me sold diamonds"
```

Console commands:

```yaml
commands-on-click-console:
  - "say %player% inspected the diamond offer"
commands-on-buy-console:
  - "say %player% purchased diamonds"
commands-on-sell-console:
  - "say %player% sold diamonds"
```

Do not include a leading slash.

## Per-item sale limits

```yaml
items:
  'diamond':
    type: SHOP_ITEM
    material: DIAMOND
    quantity: 1
    buy-price: 500
    sell-price: 125
    maximum:
      money:
        by:
          selling:
            player:
              can:
                make: 10000
      items:
        player:
          can:
            sell: 64
```

The loader reads these exact paths:

```text
maximum.money.by.selling.player.can.make
maximum.items.player.can.sell
```

Both default to `-1`, meaning no per-entry limit.

## Bulk and amount selectors

Global switches:

```yaml
enableBulkBuyGUI: true
enableBulkSellGUI: true
enableBuyMoreGUI: true
enableSellMoreGUI: true
openBulkGuiImmediately: false
```

Shared GUI behavior:

```yaml
enableBuyGUI: true
enableSellGUI: true
enableSellAll: true
enableSellGUISellAll: true
returnToShop: true
quickBuySell: false
```

Player permissions:

```text
zaminshop.player.buy-more
zaminshop.player.sell-more
```

## Click shortcuts

The bundled GUI settings map:

```yaml
clickActions:
  LEFT: BUY
  RIGHT: SELL
  SHIFT_RIGHT: SELL_ALL
  MIDDLE: Favorite
```

Inventory shortcut processing is separately controlled in `config.yml`:

```yaml
inventoryClickShortcuts:
  enabled: true
  mainMenu: false
  shopMenu: true
  amountSelector: false
  bulkBuy: false
  bulkSell: false
```

## Sell commands

See [Commands](../commands.md) for:

* `/sell hand [quantity]`;
* `/sell handall`;
* `/sell all [shop] [player]`.

Command behavior is additionally controlled by `sellHand` and `sellAll` in `config.yml`.

## Sell GUI

The sell GUI accepts player inventory items into configured sell slots. It can:

* sell valid items on close;
* return invalid or unsold items;
* accept shift-clicks;
* accept drag operations into sell slots;
* play configured feedback sounds;
* show a sale summary.

See [Sell GUI](../gui/sell-gui.md).

## Transaction safety

Do not disable safety controls solely to work around a bad shop definition. Reload, read the automatic validation report, then use:

```text
/zaminshop overwatcher list
```

before opening a new pack to players.

See [Transaction Safety and Overwatcher](../configuration/safety.md).
