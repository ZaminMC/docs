---
description: Expose multiple registered currencies in one shop pack and define prices per provider.
---

# Multi-Currency Shops

Version `1.20.0` lets one shop pack expose several registered provider IDs. Players choose a currency only when more than one provider can complete the selected buy or sell action.

## 1. Register providers

In `plugins/ZaminShop/currency.yml`:

```yaml
default-provider: vault

providers:
  vault:
    type: VAULT
    enabled: true
    display-name: Money
    icon:
      material: EMERALD
    prefix: "$"
    suffix: ""

  points:
    type: PLAYER_POINTS
    enabled: true
    display-name: Points
    icon:
      material: NETHER_STAR
    prefix: ""
    suffix: " points"
```

`vault` and `points` are provider IDs. They are the values used by shop packs and item price keys.

## 2. Expose providers in the pack

In `plugins/ZaminShop/shops/survival_shop/main.yml`:

```yaml
menu_title: "&8Survival Shop"
open_command:
  - shop

# Only these registered provider IDs are available to this pack.
currencies:
  - vault
  - points

size: 54
```

Unknown or disabled provider IDs produce a shop-pack warning and are not added to the pack.

## 3. Price an item for both providers

In a category file:

```yaml
menu_title: "&8Minerals"
rows: 3

items:
  diamond:
    type: SHOP_ITEM
    material: DIAMOND
    slot: 13
    quantity: 1

    # Price used by the vault provider ID.
    vault-buy-price: 1000
    vault-sell-price: 250

    # Price used by the points provider ID.
    points-buy-price: 20
    points-sell-price: 5
```

Provider-specific price keys use:

```text
<provider-id>-buy-price
<provider-id>-sell-price
```

## Pin one item to one provider

```yaml
items:
  point_crate:
    type: COMMAND
    material: CHEST
    slot: 14
    quantity: 1

    # This item never opens currency selection.
    currency-provider: points
    points-buy-price: 100

    commands:
      - "crate key give %player% vote 1"
```

An item-level `currency-provider` takes priority over the pack provider list.

## Selection rules

ZaminShop resolves currencies in this order:

1. item `currency-provider`;
2. pack `currencies`;
3. provider IDs found in the item's provider-specific prices;
4. provider matching the category's legacy `economy`;
5. `currency.yml` `default-provider`.

A provider is offered only when:

- it is registered and enabled;
- the item resolves to a positive price for the current action.

Buy and sell may therefore display different provider choices.

## Important fallback behavior

When an item has any provider-specific prices, a provider without its own price resolves to zero for that item. The generic `buy-price` and `sell-price` are not used as a fallback for missing provider-specific prices in that case.

Use complete provider-specific pricing:

```yaml
items:
  iron_ingot:
    type: SHOP_ITEM
    material: IRON_INGOT
    slot: 12
    vault-buy-price: 50
    vault-sell-price: 10
    points-buy-price: 2
    points-sell-price: 1
```

## Currency selection menu

The menu appears only when more than one provider can complete the action and the item is not pinned to one provider.

Configure it in [currency.yml](../configuration/currency-yml.md).

## Price modifiers

Player price modifiers are applied after the provider-specific base price is selected.

## Overwatcher

Static auditing and Runtime Shield compare prices within the same provider ID. A Vault purchase is not compared directly with a PlayerPoints sale because the plugin has no exchange rate between them.

## Reloading

Run:

```text
/zaminshop reload
```

Then read both automatic console reports. Restart when an external economy plugin was installed or removed.
