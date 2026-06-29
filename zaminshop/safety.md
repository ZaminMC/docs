# Safety

ZaminShop includes checks for menus, shop loading, prices, transactions, suspicious selling, and sell limits.

Keep safety enabled unless you are debugging a specific issue.

## Validation

ZaminShop validates menu and shop YAML while loading.

It checks common problems such as:

* unknown menu keys
* missing required amount selector actions
* malformed actions
* invalid sounds
* invalid materials
* broken shop resources

Use:

```text
/zaminshop check
```

## Transaction Checks

```yaml
safety:
  transactions:
    enabled: true
    per-player-lock: true
    lock-timeout-ms: 5000
    click-cooldown-ms: 150
    block-while-inventory-open: false
    debug-failures: false
```

| Option | Description |
| ------ | ----------- |
| `enabled` | Enables transaction safety checks. |
| `per-player-lock` | Prevents overlapping transactions for one player. |
| `lock-timeout-ms` | Timeout for transaction locks. |
| `click-cooldown-ms` | Cooldown for GUI transaction clicks. |
| `block-while-inventory-open` | Blocks configured transaction paths while another inventory is open. |
| `debug-failures` | Logs more transaction failure details. |

## Price Checks

```yaml
safety:
  price-protection:
    enabled: true
    block-unsafe-shop-items: true
    notify-admins: true
    require-confirmation: true
    max-sell-buy-ratio: 0.8
    allow-sell-higher-than-buy: false
```

ZaminShop checks unsafe prices and profit loops through its price protection service.

The public config path is `safety.price-protection`.

## Suspicious Transactions

```yaml
safety:
  suspicious-transactions:
    enabled: false
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

This watches rapid sell behavior and can warn admins or temporarily block selling.

## Sell Limits

```yaml
limits:
  sell:
    enabled: false
    reset-timezone: "server"
    daily:
      enabled: false
      max-money: 50000
      max-items: 50000
    weekly:
      enabled: false
      max-money: 500000
      max-items: 500000
```

Sell limits can cap money and item volume daily or weekly.

## GUI Click Safety

```yaml
safety:
  gui:
    log-suspicious-clicks: true
    close-on-invalid-session: true
    strict-holder-validation: true
    strict-inventory-reference-validation: true
```

These options protect ZaminShop inventories from invalid session and click state.
