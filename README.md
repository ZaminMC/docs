# ZaminShop Wiki

Welcome to the **source-accurate ZaminShop documentation**.

This wiki was written against the provided source ZIP, not guessed from a generic shop plugin template.

## Source facts

| Item | Value |
|---|---|
| Plugin | `ZaminShop` |
| Version | `1.6.0` |
| Main class | `com.zamin.zaminshop.bootstrap.ZaminShopPlugin` |
| Runtime | Bukkit / Spigot / Paper, with Folia-compatible scheduling bridge |
| Java target | Java 17 |
| Default config version | `2` |
| Public API package | `com.zamin.zaminshop.api` |
| Main player command | `/shop` |
| Main admin command | `/zaminshop` |
| Sell command | `/sell` |

## What ZaminShop actually contains

ZaminShop is a configurable economy shop plugin with:

- YAML shop files in `shops/`
- YAML menu files in `guis/`
- configurable shop directory, search, favorites, recent, amount selector, bulk buy/sell, and sell GUI menus
- configurable economy providers
- transaction safety locking
- transaction audit logging
- currency safety validation
- risk guard for dangerous buy/sell price setups
- sell limits
- suspicious transaction alerts
- PlaceholderAPI expansion
- public Java API
- SQLite/MySQL player data storage
- migration-friendly legacy command/permission support

## Read this first

1. Install the plugin.
2. Start the server once.
3. Edit `config.yml`, `shops/*.yml`, and `guis/*.yml`.
4. Use `/zaminshop validate`.
5. Use `/zaminshop risk list`.
6. Confirm or fix any reported issues.
7. Reload with `/zaminshop reload`.

Do not publish a shop setup without running `validate` and checking risk guard.
