# Safety, Risk Guard, and Audit

This is one of the most important parts of ZaminShop.

Many shop plugins can render menus. The harder problem is keeping the economy and item flow safe when players spam clicks, sell huge volumes, or expose a bad price setup.

## Transaction safety

`transaction-safety` protects the execution path for buy and sell actions.

```yaml
transaction-safety:
  enabled: true
  per-player-lock: true
  lock-timeout-ms: 5000
  click-cooldown-ms: 150
  block-while-inventory-open: false
  debug-failures: false
```

### What it does

- stops overlapping actions from the same player
- reduces spam-click race conditions
- gives the transaction layer one consistent authority path

### When to change it

Most servers should leave this enabled.

Only tune the timings if:

- players feel locked out by cooldowns that are too aggressive
- you are debugging a transaction timing issue

## Transaction audit

`transaction-audit` controls structured logging for transaction results.

```yaml
transaction-audit:
  enabled: false
  log-success: false
  log-failures: true
  include-inventory-summary: false
```

### When to use it

Turn this on when you need to investigate:

- disappearing items
- failed deposits
- rollback behavior
- suspicious reports from players

For normal production use, failure logging is often enough.

## Currency safety

`currency-safety` is the money validation layer.

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

### Why it exists

Economy bugs are not always caused by the economy plugin. Sometimes they come from:

- bad YAML prices
- impossible decimal precision
- broken modifiers
- invalid math results

This section blocks those cases before they hit the transaction pipeline.

## Risk guard

Risk guard is the economic sanity checker.

```yaml
risk-guard:
  enabled: true
  block-critical-shops: true
  notify-admins: true
  require-confirmation: true
  max-sell-buy-ratio: 0.8
  allow-sell-higher-than-buy: false
```

### What it protects against

It catches setups like:

- sell price too close to buy price
- sell price higher than buy price
- other pricing relationships that can damage the economy

### Why this matters

A YAML file can be valid and still be economically dangerous.

That is why `validate` and `risk list` are separate tools.

### Admin commands

```text
/zaminshop risk list
/zaminshop risk confirm <riskId>
/zaminshop risk reset
```

### Recommended default

Public servers should keep:

- `enabled: true`
- `block-critical-shops: true`
- `require-confirmation: true`

## Practical advice

If you are unsure whether a price setup is safe:

1. run `/zaminshop validate`
2. run `/zaminshop risk list`
3. fix the warning instead of immediately confirming it
