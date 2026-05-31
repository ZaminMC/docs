# Sell Limits and Suspicious Transactions

This section exists for servers where uncontrolled selling can distort the economy.

If your players can mass-farm crops, mobs, drops, or automated inventory loops, you should read this page carefully.

## Sell limits

Global sell limits are configured in `config.yml`.

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

### What they do

These limits cap how much a player can extract from the sell economy over time.

They are useful for:

- survival servers with large farms
- prison or grinding servers
- event economies where one item can flood the market

### Daily vs weekly

- daily limits stop short bursts
- weekly limits stop long-term abuse

Use both if your server has serious sell volume.

## Suspicious transactions

This is the alerting and optional blocking layer for abnormal sell behavior.

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

### What it is for

Use this when you want to detect:

- extreme sell bursts
- repeated identical item dumping
- possible exploit behavior
- player automation that is too aggressive for your economy

### Recommended rollout

Start with:

- warnings enabled
- temporary blocking disabled

Watch the logs first. Then enable temporary blocking only after you understand normal player behavior on your server.

## Per-item limits

ZaminShop also supports item-level sell caps inside shop item definitions.

That is useful when only a few items are risky instead of the whole economy.
