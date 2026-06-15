# Common Server Setups

These are complete starting profiles using the current `1.20.0` file layout.

## Survival with Vault

`currency.yml`:

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

currency-selection:
  enabled: true
  open-before-amount-selector: true
  remember-last-provider: true
  menu:
    title: "&8Choose Currency"
    rows: 3
    open-sound: UI_BUTTON_CLICK
    slots:
      - 13
    filler:
      material: GRAY_STAINED_GLASS_PANE
      display-name: "&r"

safety:
  enabled: true
  decimal-places: 2
  reject-prices-with-too-many-decimals: true
  minimum-transaction-value: 0.01
  normalize-player-balances-for-checks: true
  block-nan-infinity: true
  max-transaction-value: 1000000000000
```

Pack `main.yml`:

```yaml
menu_title: "&8Survival Shop"
open_command:
  - shop
currencies:
  - vault
size: 54
```

## Money and PlayerPoints

`currency.yml`:

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

currency-selection:
  enabled: true
  open-before-amount-selector: true
  remember-last-provider: true
  menu:
    title: "&8Choose Currency"
    rows: 3
    open-sound: UI_BUTTON_CLICK
    slots:
      - 11
      - 15
    filler:
      material: GRAY_STAINED_GLASS_PANE
      display-name: "&r"

safety:
  enabled: true
  decimal-places: 2
  reject-prices-with-too-many-decimals: true
  minimum-transaction-value: 0.01
  normalize-player-balances-for-checks: true
  block-nan-infinity: true
  max-transaction-value: 1000000000000
```

Pack `main.yml`:

```yaml
menu_title: "&8Survival Shop"
open_command:
  - shop
currencies:
  - vault
  - points
size: 54
```

Category item:

```yaml
items:
  diamond:
    type: SHOP_ITEM
    material: DIAMOND
    slot: 13
    vault-buy-price: 1000
    vault-sell-price: 250
    points-buy-price: 20
    points-sell-price: 5
```

## Farm-heavy survival

Add to `config.yml`:

```yaml
sell-limits:
  enabled: true
  reset-timezone: "server"
  daily:
    enabled: true
    max-money: 50000
    max-items: 50000
  weekly:
    enabled: false
    max-money: 500000
    max-items: 500000

suspicious-transactions:
  enabled: true
  notify-admins: true
  log-console: true
  cooldown-between-alerts-seconds: 60
  thresholds:
    transactions-per-10-seconds: 20
    money-earned-per-minute: 1000000
    items-sold-per-minute: 50000
    same-item-sales-per-10-seconds: 15
  actions:
    warn-admins: true
    temporarily-block-selling: false
    block-duration-seconds: 30
```

## Strict economy protection

Keep the shipped `overwatcher.yml`:

```yaml
enabled: true
block-critical-shops: true
notify-admins: true
require-confirmation: true
max-sell-buy-ratio: 0.8
allow-sell-higher-than-buy: false

runtime-shield:
  enabled: true
  track-purchased-items: true
  block-unsafe-reselling: true
  lock-exploitable-items:
    enabled: true
    duration: 10m
  notify:
    console: true
    admins: true
  messages:
    player-blocked: "This item cannot be sold right now."
```

Also enable transaction audit in `config.yml`:

```yaml
transaction-audit:
  enabled: true
  log-success: false
  log-failures: true
  include-inventory-summary: false
```

## Applying a profile

1. Install every external provider required by the profile.
2. Restart the server.
3. Apply the YAML sections to their named files.
4. Run `/zaminshop reload`.
5. Read the automatic Validation and Overwatcher reports.
6. Test with a non-op player.
