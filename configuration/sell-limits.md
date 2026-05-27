# Sell Limits & Suspicious Transactions

## Sell limits

```yaml
sell-limits:
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

Use this to stop players from dumping unlimited items into the economy.

## Suspicious transactions

```yaml
suspicious-transactions:
  enabled: false
  notify-admins: true
  log-console: true
  cooldown-between-alerts-seconds: 60
```

Thresholds:

```yaml
thresholds:
  transactions-per-10-seconds: 20
  money-earned-per-minute: 1000000
  items-sold-per-minute: 50000
  same-item-sales-per-10-seconds: 15
```

Actions:

```yaml
actions:
  warn-admins: true
  temporarily-block-selling: false
  block-duration-seconds: 30
```
