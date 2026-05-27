# Installation & Setup

## Requirements

- Java 17+
- Bukkit/Spigot/Paper server
- Economy plugin if using `VAULT` or another external economy
- Optional: PlaceholderAPI

## Install

1. Put `ZaminShop.jar` into `plugins/`.
2. Start the server once.
3. Stop the server.
4. Edit generated files.
5. Start again.
6. Run validation.

## Validation flow

```text
/zaminshop validate
/zaminshop risk list
```

If validation reports errors, fix the YAML before opening the shop publicly.

## Recommended first config edits

```yaml
economyTypes:
  - VAULT

startup-log:
  debug: false
  show-shop-breakdown: true

transaction-safety:
  enabled: true

risk-guard:
  enabled: true
```

## Player permissions

Give normal players:

```text
zaminshop.player.*
```

Or selectively:

```text
zaminshop.player.shop
zaminshop.player.search
zaminshop.player.favorite
zaminshop.player.recent
zaminshop.sellgui
zaminshop.player.worth
```
