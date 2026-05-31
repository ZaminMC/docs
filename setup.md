# Install and Launch Your First Shop

This page is the fastest path from jar file to a working `/shop`.

## Requirements

- Java 17 or newer
- Bukkit, Spigot, or Paper
- at least one supported economy provider
- PlaceholderAPI if you want external placeholders inside menus or messages

## Step 1: install the jar

Put the ZaminShop jar into your server's `plugins/` folder and start the server once.

This first boot generates the plugin folder and bundled files.

## Step 2: stop the server and open the files

After the first startup, you should have:

```text
plugins/ZaminShop/
  config.yml
  guis/
  shops/
  lang/
```

At this point, do not start editing random files yet. Begin with `config.yml`.

## Step 3: choose your default economy

In `config.yml`, set the main economy list:

```yaml
economyTypes:
  - VAULT
```

The first valid provider becomes the default economy for the plugin unless a shop overrides it.

## Step 4: register a shop pack

ZaminShop uses manual pack registration.

Example:

```yaml
shops:
  survival:
    folder: survival_shop
    enabled: true
    file: main.yml
```

This tells ZaminShop to load:

```text
plugins/ZaminShop/shops/survival_shop/main.yml
plugins/ZaminShop/shops/survival_shop/categories/*.yml
```

If the folder exists but is not registered here, it is ignored.

## Step 5: confirm the pack files exist

Your pack should look like this:

```text
plugins/ZaminShop/shops/survival_shop/
  main.yml
  categories/
    blocks.yml
    food.yml
    ores.yml
```

## Step 6: start the server again

On the second startup, verify:

- the selected economy provider loaded
- the registered pack was detected
- no YAML errors were logged
- `/shop` opens the expected main menu

## Step 7: validate before going public

Run:

```text
/zaminshop validate
/zaminshop risk list
```

Why both?

- `validate` checks menu and shop configuration issues
- `risk list` shows pricing setups that may be dangerous even if the YAML syntax is valid

## Recommended first edits

After the plugin boots cleanly, most servers will want to review:

- `config.yml -> transaction-safety`
- `config.yml -> risk-guard`
- `config.yml -> search`
- `config.yml -> sell-limits`
- `guis/sell.yml`
- your pack `main.yml`

## Common mistakes

### The pack folder exists but the plugin ignores it

It is probably not registered under `config.yml -> shops`.

### `/shop` opens the wrong thing

Check the pack `main.yml` and confirm it is the pack currently tied to the `shop` command scope.

### The plugin loads but menus are broken

Run `/zaminshop validate` immediately. Many menu problems are configuration issues, not startup failures.

### A menu file was moved

If you moved a shared GUI file, update `config.yml -> gui_menus` so the plugin can still find it.
