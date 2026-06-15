---
description: Complete commented reference for currency providers, currency selection, and transaction value safety.
---

# currency.yml Reference

`plugins/ZaminShop/currency.yml` registers currency providers. Shop packs choose which registered provider IDs they expose, and shop items may define different prices for each provider.

## Complete shipped file

```yaml
# Provider used when a shop or item does not select another provider.
default-provider: vault

providers:
  vault:
    # Economy implementation used by this provider ID.
    type: VAULT

    # Disabled providers are not registered and cannot be used by shops.
    enabled: true

    # Player-facing name used by the currency selection menu.
    display-name: Vault

    # Icon displayed in the currency selection menu.
    icon:
      material: EMERALD

    # Text placed before and after formatted values.
    prefix: "$"
    suffix: ""

  playerpoints:
    type: PLAYER_POINTS
    enabled: false
    display-name: PlayerPoints
    icon:
      material: NETHER_STAR
    prefix: ""
    suffix: " points"

  item:
    type: ITEM
    enabled: false
    display-name: Coins
    icon:
      material: EMERALD
    prefix: ""
    suffix: " Coins"

    # Decimal precision represented by the smallest physical denomination.
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

currency-selection:
  # Show a provider menu when more than one provider can complete an action.
  enabled: true

  # Show provider selection before the normal amount selector.
  open-before-amount-selector: true

  # Keep the selected provider for the same item and action after a transaction.
  remember-last-provider: true

  menu:
    title: "&8Choose Currency"

    # Clamped to one through six rows.
    rows: 3

    # Sound key or sound name played when the menu opens.
    open-sound: UI_BUTTON_CLICK

    # Provider icons are placed in this order.
    slots:
      - 11
      - 13
      - 15

    filler:
      material: GRAY_STAINED_GLASS_PANE
      display-name: "&r"

safety:
  # Master currency-value validation switch.
  enabled: true

  # Global accepted transaction precision.
  decimal-places: 2

  # Reject prices with more decimals than the configured precision.
  reject-prices-with-too-many-decimals: true

  # Smallest accepted non-zero transaction value.
  minimum-transaction-value: 0.01

  # Normalize balances before affordability comparisons.
  normalize-player-balances-for-checks: true

  # Reject NaN and positive or negative infinity.
  block-nan-infinity: true

  # Largest accepted transaction value.
  max-transaction-value: 1000000000000
```

## Provider IDs and types

The child name under `providers` is the provider ID used by packs and item prices. In:

```yaml
providers:
  voting:
    type: VOTING_PLUGIN
    enabled: true
```

`voting` is the provider ID and `VOTING_PLUGIN` is the implementation type.

Provider IDs are normalized to lowercase and underscores become hyphens.

Supported types:

```text
CUSTOM
EXP
EXP_LEVELS
EXCELLENT_ECONOMY
COINS_ENGINE
GEMS_ECONOMY
ITEM
MYSQL_TOKENS
PLAYER_POINTS
TOKEN_ENCHANT
TOKEN_MANAGER
VAULT
VOTING_PLUGIN
```

## Provider icon options

The selection menu reads:

```yaml
providers:
  vault:
    display-name: Vault
    description:
      - "&7Use your server balance."
    icon:
      material: EMERALD
      display-name: "&a%currency_name%"
      lore:
        - "&7Balance: &f%currency_balance%"
        - "&7Provider: &f%currency_id%"
```

Available values:

```text
%currency_id%
%currency_name%
%currency_balance%
%currency_icon%
%currency_description%
```

When `icon.lore` is empty, ZaminShop uses the provider `description`, adds a blank line, and adds the balance line automatically.

## Legacy compatibility

The current file is `currency.yml`. The loader still reads legacy `config.yml` keys such as `economyTypes`, `economyType`, `item-currency`, `currency-safety`, and `currencies` as compatibility fallbacks.

New installations and new documentation should use `currency.yml`.

## Reloading

Configuration changes are loaded by:

```text
/zaminshop reload
```

Restart after installing, removing, or replacing an external economy plugin.
