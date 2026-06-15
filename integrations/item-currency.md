---
description: Use exact inventory items as a registered physical currency provider.
---

# Built-in Item Currency

The `ITEM` provider treats configured item stacks as denominations of one physical currency. It does not require Vault.

## Complete configuration

`plugins/ZaminShop/currency.yml`:

```yaml
default-provider: coins

providers:
  coins:
    # Enable the built-in inventory-backed provider.
    type: ITEM
    enabled: true

    # Player-facing selection-menu details.
    display-name: Coins
    icon:
      material: EMERALD
    prefix: ""
    suffix: " Coins"

    # Number of decimal places represented by one atomic unit.
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

`plugins/ZaminShop/shops/survival_shop/main.yml`:

```yaml
menu_title: "&8Survival Shop"
open_command:
  - shop
currencies:
  - coins
size: 54
```

This directly usable setup values one emerald at one Coin and one emerald block at nine Coins.

## Validation rules

The provider is rejected when:

- `decimal-places` is below `0` or above `6`;
- there are no denominations;
- a denomination has no `value` or `item`;
- a value is zero, negative, too precise, invalid, or too large;
- an item resolves to air;
- two denominations produce identical items;
- no denomination is worth exactly one atomic unit.

With `decimal-places: 0`, one atomic unit is `1`. With `decimal-places: 2`, one atomic unit is `0.01`.

## Inventory scope

Only slots `0` through `35` of the normal player inventory are counted.

Excluded:

- armor;
- off-hand;
- ender chest;
- items inside containers;
- cursor item.

## Exact item matching

Denominations use Bukkit item similarity after stack amount is normalized to one. Material and metadata therefore matter.

A named, modeled, enchanted, or custom-tagged token is distinct from an ordinary item of the same material.

## Deposits, withdrawals, and change

Before changing a balance, ZaminShop:

1. snapshots the 36 storage slots;
2. counts recognized denominations;
3. calculates the target value;
4. removes recognized currency from the planned inventory;
5. rebuilds the balance from highest denomination to lowest;
6. commits the complete inventory plan.

If the rebuilt balance does not fit, the transaction fails. If writing fails, ZaminShop attempts to restore the snapshot.

{% hint style="warning" %}
Players may need empty inventory slots to receive change or sale proceeds. Recognized currency can be recomposed into different denominations.
{% endhint %}

## Shop item example

```yaml
items:
  diamond:
    type: SHOP_ITEM
    material: DIAMOND
    slot: 13
    coins-buy-price: 18
    coins-sell-price: 9
```

The price prefix uses the provider ID `coins`, not the type `ITEM`.

## Decimal example

```yaml
providers:
  tokens:
    type: ITEM
    enabled: true
    display-name: Tokens
    icon:
      material: GOLD_INGOT
    suffix: " Tokens"
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

Stop trading activity before changing denomination identity or values, then run:

```text
/zaminshop reload
```

Existing physical items are not migrated when a denomination changes.
