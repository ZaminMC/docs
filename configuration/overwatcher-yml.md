---
description: Complete commented reference for static economy auditing and Runtime Shield.
---

# overwatcher.yml Reference

`plugins/ZaminShop/overwatcher.yml` controls price auditing and Runtime Shield.

```yaml
# Run the static price audit after startup and successful reloads.
enabled: true

# Block items involved in unconfirmed critical findings.
block-critical-shops: true

# Notify online administrators when findings exist.
notify-admins: true

# Keep confirmation behavior enabled for guarded operations.
require-confirmation: true

# Warn when sell price divided by buy price exceeds this ratio.
max-sell-buy-ratio: 0.8

# Allow an item's sell price to exceed its buy price.
allow-sell-higher-than-buy: false

runtime-shield:
  # Master Runtime Shield switch.
  enabled: true

  # Add a signed ZaminShop purchase fingerprint to delivered items.
  track-purchased-items: true

  # Reject profitable resale of the exact tracked items.
  block-unsafe-reselling: true

  lock-exploitable-items:
    # Temporarily lock the source and destination listings after a violation.
    enabled: true

    # Duration accepts seconds, minutes, hours, or days.
    duration: 10m

  notify:
    # Write blocked resale attempts to the console.
    console: true

    # Notify online players with zaminshop.admin.overwatcher.
    admins: true

  messages:
    player-blocked: "This item cannot be sold right now."
```

## Duration format

Supported suffixes:

```text
s = seconds
m = minutes
h = hours
d = days
```

Examples:

```yaml
duration: 30s
duration: 10m
duration: 2h
duration: 1d
```

A value without a suffix is interpreted as seconds. Values are at least one second. Invalid values fall back to ten minutes.

## What the static audit finds

Overwatcher checks each physical `SHOP_ITEM` per currency provider for:

- a sell price above its buy price;
- a sell-to-buy ratio above the configured warning threshold;
- profitable direct resale between matching items in different shops;
- profitable supported crafting or compaction conversions.

Critical findings can block both sides of a profitable conversion until confirmed.

## What Runtime Shield does

Runtime Shield signs items delivered by ZaminShop with their source pack, shop, item, unit price, total price, amount, and currency provider.

When the player attempts to sell a matching item:

1. the signature is verified;
2. the current sell unit price is compared with the signed purchase unit price;
3. the comparison is made only within the same currency provider;
4. a profitable resale or invalid signature is blocked;
5. affected listings may be temporarily locked.

The signature is ignored for normal item matching, so enabling Runtime Shield does not make a purchased item fail its configured metadata comparison.

## Storage compatibility

The fingerprint service selects a storage backend compatible with the running Minecraft version. Current code includes persistent-data, NBT, and legacy NBT storage implementations.

## Confirmation storage

Confirmed static findings are stored in:

```text
plugins/ZaminShop/overwatcher-confirmations.yml
```

Do not edit this generated file while the server is running. Use the Overwatcher commands.
