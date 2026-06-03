# config.yml Reference

This page explains the global configuration file.

`config.yml` controls global runtime behavior. It does **not** define individual shop items or category content.

## What belongs here

Use `config.yml` for:

- database selection
- default economy types
- startup logging
- transaction safety
- risk guard
- suspicious transaction thresholds
- sell limits
- GUI file paths
- command registration toggles
- number and currency formatting

## Language

```yml
language: "en_US"
```

Controls the active language file under `plugins/ZaminShop/lang/`.

## Database

```yml
database:
  type: sqlite
```

ZaminShop supports SQLite and MySQL-style setups depending on your deployment needs.

Use SQLite if:

- you run a single server
- you want the easiest setup

Use MySQL if:

- you manage a larger network
- you want data outside a local file

## Economy types

```yml
economyTypes:
  - VAULT
```

The first entry becomes the default economy for shops unless a shop or integration path overrides it.

Common use:

- `VAULT` for normal money economies
- alternative providers for token or custom currencies

## Startup logging

```yml
startup-log:
  banner: true
  debug: false
  show-shop-breakdown: false
```

Useful while building packs:

- turn `debug` on temporarily
- validate changes
- turn it off after stabilization

## Transaction safety

```yml
transaction-safety:
  enabled: true
  per-player-lock: true
```

This is one of the most important sections in the plugin.

It protects:

- overlapping clicks
- duplicated actions
- invalid concurrent transaction paths

Keep this enabled unless you are doing controlled debugging.

## Currency safety

```yml
currency-safety:
  decimal-places: 2
  reject-prices-with-too-many-decimals: true
```

Controls price normalization and sanity checks.

Important effects:

- invalid floating-point values are blocked
- excessive decimal precision can be rejected
- transaction values can be normalized consistently

## Risk guard

```yml
risk-guard:
  enabled: true
  block-critical-shops: true
  require-confirmation: true
```

Risk guard helps catch:

- impossible buy/sell relationships
- direct arbitrage
- cross-category arbitrage
- cross-pack arbitrage
- compaction and crafting loops

If you care about economy integrity, keep this enabled.

## Sell limits

Sell limits cap how much value or item volume can be sold across a defined period.

Use them when:

- you want to slow farm-heavy monetization
- you want a daily or weekly economic ceiling

## Suspicious transactions

This system watches player behavior patterns rather than static item definitions.

Use it when:

- players can generate large item volume
- you want alerts before an exploit fully matures

## Search and recent menu behavior

```yml
search:
  enabled: true
recent-menu:
  enabled: true
```

These let you enable or tune the supporting player experience around the core shop.

## GUI menu file locations

```yml
gui_menus:
  amount-selector:
    file: guis/amount-selector.yml
```

This is where you point ZaminShop to shared menu files.

If you move a built-in GUI file to a different path, update it here.

## Shop pack registration

Modern ZaminShop does not register packs under `config.yml`.

Instead:

- packs are discovered from `plugins/ZaminShop/shops/<pack>/main.yml`
- categories are loaded from `plugins/ZaminShop/shops/<pack>/categories/*.yml`

## Sell command behavior

`sellHand` and `sellAll` sections control:

- allowed quantities
- armor slot exclusions
- off-hand exclusions
- summary behavior
- whether free items are included

## Number format

Controls:

- decimal separator
- grouping separator
- fraction visibility
- short-scale numbering

This affects how values are shown to players in messages and GUI output.

## Common mistakes

### Treating `config.yml` like the whole plugin

It is only the global layer. Packs and menus live elsewhere.

### Turning off safety systems too early

Leave them on until you have a specific debugging reason.

### Editing GUI file paths without moving the actual files

If the path changes here, the file has to exist there.

## Related pages

- [Files and Folder Layout](files-and-folders.md)
- [Safety, Risk Guard, and Audit](safety.md)
- [Shop Pack File Format](../shops/shop-file-format.md)
