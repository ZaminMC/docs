# config.yml Reference

This page covers the most important runtime sections from the current bundled `config.yml`.

## `language`

```yaml
language: "en_US"
```

Controls the active language file under `plugins/ZaminShop/lang/`.

## `database`

```yaml
database:
  type: sqlite
  mySQLHost: localhost
  mySQLPort: 3306
  mySQLDatabase: db
  mySQLUser: root
  mySQLPassword: ""
```

Used for player data, favorites, recent transactions, and related storage.

## `economyTypes`

```yaml
economyTypes:
  - VAULT
```

This list is ordered. The first valid provider becomes the default shop currency unless a shop overrides it.

## `transaction-safety`

Controls the runtime protection layer around buy and sell actions.

Important keys:

- `enabled`
- `per-player-lock`
- `lock-timeout-ms`
- `click-cooldown-ms`
- `block-while-inventory-open`
- `debug-failures`

## `transaction-audit`

Optional transaction logging layer.

Use this if you want a structured audit trail for suspicious actions or debugging.

## `currency-safety`

Prevents invalid money values from entering the economy pipeline.

Important keys:

- `decimal-places`
- `reject-prices-with-too-many-decimals`
- `minimum-transaction-value`
- `block-nan-infinity`
- `max-transaction-value`

## `risk-guard`

Checks dangerous pricing setups such as unsafe sell-to-buy ratios.

Important keys:

- `enabled`
- `block-critical-shops`
- `notify-admins`
- `require-confirmation`
- `max-sell-buy-ratio`
- `allow-sell-higher-than-buy`

## `sell-limits`

Optional daily and weekly sell caps.

Works together with the PlaceholderAPI counters documented on the PlaceholderAPI page.

## `suspicious-transactions`

Optional alerting system for abnormal selling behavior.

Includes thresholds such as:

- transactions per 10 seconds
- money earned per minute
- items sold per minute
- repeated sales of the same item

## `search`

```yaml
search:
  enabled: true
  fuzzy: true
  max-results: 45
  search-on-unknown-shop-command: false
```

Controls the `/shop search` system.

## `gui_menus`

Maps built-in shared menu ids to file paths.

Example:

```yaml
gui_menus:
  amount-selector:
    file: guis/amount-selector.yml
  favorites:
    file: guis/favorites.yml
  sell:
    file: guis/sell.yml
```

If you move a shared GUI file, update the path here.

## `shops`

Manual shop pack registration lives here.

Example:

```yaml
shops:
  survival:
    folder: survival_shop
    enabled: true
    file: main.yml
```

Meaning:

- `survival` is the internal pack id
- `folder` is the folder inside `plugins/ZaminShop/shops/`
- `enabled` controls whether the pack loads
- `file` is the main menu file name inside that folder

ZaminShop only loads packs listed here.

## Other important gameplay settings

### `disableMainMenu`

Blocks the default main menu path when enabled.

### `disableShopsInGamemodes`

Prevents normal shop access from selected gamemodes.

### `disableShopsInWorlds`

Prevents normal shop access from selected worlds.

### `sudoAllowAllShopsAccess`

Changes how admin-opened shop sessions bypass normal access checks.

### `disableCommands.sell`

Prevents the `/sell` command from being registered. This requires a full restart, not just a reload.
