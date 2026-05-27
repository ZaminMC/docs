# Safety, Risk Guard & Audit

ZaminShop has several config-level safety systems.

## transaction-safety

```yaml
transaction-safety:
  enabled: true
  per-player-lock: true
  lock-timeout-ms: 5000
  click-cooldown-ms: 150
  block-while-inventory-open: false
  debug-failures: false
```

This protects transaction execution from spam clicks and overlapping operations.

## transaction-audit

```yaml
transaction-audit:
  enabled: false
  log-success: false
  log-failures: true
  include-inventory-summary: false
```

Turn this on when debugging suspicious behavior.

## currency-safety

```yaml
currency-safety:
  enabled: true
  decimal-places: 2
  reject-prices-with-too-many-decimals: true
  minimum-transaction-value: 0.01
  normalize-player-balances-for-checks: true
  block-nan-infinity: true
  max-transaction-value: 1000000000000
```

This blocks impossible or dangerous money values.

## risk-guard

```yaml
risk-guard:
  enabled: true
  block-critical-shops: true
  notify-admins: true
  require-confirmation: true
  max-sell-buy-ratio: 0.8
  allow-sell-higher-than-buy: false
```

Risk guard catches bad economy setups, especially where sell prices are too close to or higher than buy prices.

Useful commands:

```text
/zaminshop risk list
/zaminshop risk confirm <riskId>
/zaminshop risk reset
```
