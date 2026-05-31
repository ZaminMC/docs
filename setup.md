# Installation & Setup

## Requirements

- Java 17 or newer
- Bukkit, Spigot, or Paper
- at least one supported economy provider
- PlaceholderAPI if you want external placeholders in menus and messages

## First install

1. Put the ZaminShop jar into `plugins/`
2. Start the server once
3. Stop the server after files are generated
4. Edit `config.yml`
5. Register at least one shop pack in `config.yml -> shops`
6. Start the server again
7. Run `/zaminshop validate`

## Minimal global setup

The plugin ships with this default pattern in `config.yml`:

```yaml
economyTypes:
  - VAULT

shops:
  default:
    folder: default
    enabled: true
    file: main.yml
```

If you rename the bundled pack folder, update the `folder` value as well.

## Recommended first checks

After the second startup, verify:

- the chosen economy provider loaded
- your registered shop pack folder exists
- the pack contains `main.yml`
- the pack contains `categories/*.yml`
- `/shop` opens the expected pack main menu

Then run:

```text
/zaminshop validate
/zaminshop risk list
```

## Common first-time mistakes

### The pack folder exists but does not load

Make sure it is registered under `config.yml -> shops`. ZaminShop does not auto-discover random folders under `plugins/ZaminShop/shops/`.

### `/shop` opens nothing useful

Check the pack's `main.yml` and make sure its `open_command` includes `shop`, or use the dynamic pack command defined there.

### A menu file was moved

If you move a built-in shared GUI file, update its entry under `config.yml -> gui_menus`.
