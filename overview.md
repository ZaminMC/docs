# Overview

ZaminShop is built around three core pieces:

- `config.yml` for global behavior
- `guis/*.yml` for shared menus
- `shops/<pack>/` for pack-specific shop menus

## How the plugin is structured

### Global configuration

`plugins/ZaminShop/config.yml` controls:

- enabled economies
- database backend
- transaction safety
- search behavior
- menu file paths
- registered shop packs

### Shared menus

Files under `plugins/ZaminShop/guis/` define menus used across the plugin, including:

- amount selector
- bulk buy
- bulk sell
- favorites
- recent
- search
- sell GUI

### Shop packs

Each shop pack is registered manually in `config.yml` and points to a folder under:

```text
plugins/ZaminShop/shops/<folder>/
```

Each pack contains:

- `main.yml` for the pack entry menu
- `categories/*.yml` for the actual category shops

## Safety systems

ZaminShop does more than open inventories. It also includes:

- per-player transaction locks
- click cooldown protection
- currency validation
- risk guard
- suspicious transaction detection
- sell limits
- GUI-owned item cleanup

Those systems are documented in the configuration section because they affect runtime behavior as much as menu design.
