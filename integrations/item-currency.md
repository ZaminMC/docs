---
description: Use exact inventory items as money through ZaminShop's built-in ITEM economy.
---

# Item Currency

The `ITEM` economy treats configured item stacks as denominations of one physical currency. It is built into ZaminShop and does not require Vault.

## Complete configuration

The default configuration uses emeralds:

```yaml
economyTypes:
  - ITEM

item-currency:
  display-name: Coins
  decimal-places: 0
  denominations:
    emerald:
      value: 1
      item:
        material: EMERALD
    emerald-block:
      value: 9
      item:
        material: EMERALD_BLOCK
```

This configuration is directly usable. One emerald is worth one Coin and one emerald block is worth nine Coins.

## Options

| Path | Meaning |
| --- | --- |
| `item-currency.display-name` | Currency name appended to formatted values. Defaults to `Coins` when blank. |
| `item-currency.decimal-places` | Number of decimal places represented by the smallest atomic unit. Valid range: `0` through `6`. |
| `item-currency.denominations.<id>.value` | Positive value of one denomination item. |
| `item-currency.denominations.<id>.item` | Item definition loaded through ZaminShop's normal item parser. |

Denomination IDs such as `emerald` are internal configuration identifiers. They do not appear on the physical item and do not need to match a material.

## Validation rules

The loader rejects the item currency when:

- `item-currency` is missing;
- `decimal-places` is below `0` or above `6`;
- there are no denominations;
- a denomination has no `value` or `item`;
- a value is zero, negative, too precise, invalid, or too large;
- an item resolves to air;
- two denominations produce identical items;
- no denomination is worth exactly one atomic unit.

With `decimal-places: 0`, an atomic unit is `1`. With `decimal-places: 2`, an atomic unit is `0.01`.

## Inventory scope

Only slots `0` through `35` of the player's normal inventory are counted.

ZaminShop deliberately excludes:

- armor slots;
- the off-hand;
- the ender chest;
- items inside shulker boxes or other containers;
- the cursor item.

## Exact item matching

Denominations are matched with Bukkit's `ItemStack#isSimilar` behavior after stack amount is normalized to one. Material and item metadata therefore matter.

This makes a named, modeled, enchanted, or custom-tagged currency distinct from an ordinary item of the same material.

## Deposits, withdrawals, and change

Before changing a balance, ZaminShop:

1. snapshots the 36 storage slots;
2. counts all recognized denominations;
3. calculates the target value;
4. removes recognized currency stacks from the planned inventory;
5. reconstructs the balance using denominations from highest to lowest value;
6. commits the complete plan.

If the reconstructed balance does not fit, the transaction fails with `Insufficient inventory space for item currency`. If inventory writing fails, ZaminShop attempts to restore the snapshot.

{% hint style="warning" %}
A player may need empty inventory slots to receive change or sale proceeds. Existing non-currency items are preserved, but recognized currency stacks can be recomposed into different denominations.
{% endhint %}

## Shop example

`plugins/ZaminShop/shops/survival/categories/item_market.yml`:

```yaml
shop:
  menu_title: "&8Item Market"
  rows: 3
  economy: ITEM

items:
  diamond:
    type: SHOP_ITEM
    material: DIAMOND
    slot: 13
    buy-price: 18
    sell-price: 9
```

With the default emerald currency, one diamond costs two emerald blocks and sells for one emerald block.

## Decimal currency example

```yaml
economyTypes:
  - ITEM

item-currency:
  display-name: Tokens
  decimal-places: 2
  denominations:
    gold-token:
      value: 0.01
      item:
        material: GOLD_NUGGET
    gold-bar:
      value: 1.00
      item:
        material: GOLD_INGOT
```

## Reloading

Run:

```text
/zaminshop reload
```

Then run:

```text
/zaminshop validate
```

Do not leave players trading while changing denomination identity or values. Existing physical items are not migrated when the definition changes.
