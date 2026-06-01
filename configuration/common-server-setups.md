# Common Server Setups

This page gives you practical starting points instead of forcing you to design everything from scratch.

These are not the only correct setups. They are sensible starting baselines.

## Survival setup

Good for:

- SMP servers
- general survival communities
- servers where shops are convenience, not the entire game loop

Suggested direction:

```yaml
economyTypes:
  - VAULT

search:
  enabled: true
  fuzzy: true
  max-results: 45

transaction-safety:
  enabled: true
  per-player-lock: true
  click-cooldown-ms: 150

risk-guard:
  enabled: true
  block-critical-shops: true
  require-confirmation: true

sell-limits:
  enabled: false
```

Why:

- players get the convenience features
- safety stays strong
- sell limits stay off unless the economy starts getting abused

## Farm-heavy survival setup

Good for:

- mob farms
- large crop systems
- servers where selling is a major money source

Suggested direction:

```yaml
sell-limits:
  enabled: true
  daily:
    enabled: true
    max-money: 50000
    max-items: 50000

suspicious-transactions:
  enabled: true
  notify-admins: true
  log-console: true
```

Why:

- caps the worst sell spikes
- gives admins visibility before the economy drifts too far

## Multi-pack server setup

Good for:

- survival + donor shop separation
- separate themed stores
- events or seasonal packs

Suggested direction:

```yaml
shops:
  survival:
    folder: survival_shop
    enabled: true
    file: main.yml

  donor:
    folder: donor_shop
    enabled: true
    file: main.yml
```

Why:

- clear pack ownership
- easier troubleshooting
- safer than dropping random folders and hoping the plugin guesses correctly

## Strict-economy setup

Good for:

- prison economies
- tightly balanced servers
- stores where bad pricing would be catastrophic

Suggested direction:

```yaml
currency-safety:
  enabled: true
  reject-prices-with-too-many-decimals: true
  block-nan-infinity: true

risk-guard:
  enabled: true
  block-critical-shops: true
  require-confirmation: true
  allow-sell-higher-than-buy: false

transaction-audit:
  enabled: true
  log-failures: true
```

Why:

- bad pricing is caught earlier
- failures leave more evidence
- staff has fewer silent mistakes to chase
