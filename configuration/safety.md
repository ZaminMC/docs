# Safety, Risk Guard, and Audit

This page covers the systems that keep the shop from damaging the economy or duplicating bad behavior under load.

## Transaction safety

Transaction safety exists to stop race conditions and broken click flows from turning into inventory or economy inconsistencies.

Main controls:

- per-player transaction lock
- click cooldown
- invalid amount blocking
- rollback-aware commit flow

Use it to protect:

- rapid clicking
- overlapping purchase attempts
- repeated GUI interactions during unstable state

## Currency safety

Currency safety normalizes money values before they are used in a live transaction.

It helps prevent:

- invalid decimal precision
- NaN or infinite values
- absurd transaction values
- mismatched balance comparisons

This is especially important if:

- prices are dynamic
- modifiers are active
- placeholders affect pricing

## Risk guard

Risk guard is the main economic protection layer for bad pricing.

It can block or flag:

- buy and sell relationships that make no sense
- same-item arbitrage
- cross-category arbitrage
- cross-pack arbitrage
- known compaction and crafting loops

If a finding is critical, the plugin can block the affected item or shop until an admin confirms it.

## Suspicious transaction monitoring

This system watches player behavior patterns over time.

It is meant to detect:

- extremely high sale frequency
- very large money generation bursts
- repeated same-item sale loops

Use it when your server has:

- farms
- grinders
- token or money-heavy progression

## Sell limits

Sell limits are not exploit detection. They are economy shaping.

Use them when you want to cap:

- daily money generation
- weekly money generation
- raw item sale volume

This is useful for:

- balancing farms
- slowing inflation
- preventing one activity from dominating the economy

## Validation

Validation is your first safety check before players ever touch a broken menu.

It helps catch:

- bad YAML
- broken menu links
- invalid category targets
- command conflicts
- unsupported metadata
- pagination issues

Use validation before reloads on important production changes.

## Best practice

### Keep safety enabled by default

Do not disable safety systems unless you are debugging a very specific issue.

### Treat warnings as real signals

If risk guard or validation warns you, assume the issue matters until proven otherwise.

### Re-check the whole economy after item changes

A new item in one category can create a problem in another pack.

## Related pages

- [Sell Limits and Suspicious Transactions](sell-limits.md)
- [config.yml Reference](config-yml.md)
- [Commands](../commands.md)
