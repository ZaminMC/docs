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
  mode: SMART
  max-results: 45

transaction-safety:
  enabled: true
  per-player-lock: true
  click-cooldown-ms: 150

overwatcher:
  enabled: true
  block-critical-shops: true
  notify-admins: true
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

Suggested directory structure:

```text
plugins/ZaminShop/shops/survival_shop/main.yml
plugins/ZaminShop/shops/survival_shop/categories/
plugins/ZaminShop/shops/donor_shop/main.yml
plugins/ZaminShop/shops/donor_shop/categories/
```

Why:

- clear pack ownership
- easier troubleshooting
- each folder is discovered as a pack when it contains an enabled `main.yml`

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

overwatcher:
  enabled: true
  block-critical-shops: true
  notify-admins: true
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
