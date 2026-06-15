# Install and Launch Your First Shop

This page walks through a clean first installation and the minimum steps required to get a working shop online.

## Requirements

ZaminShop is designed for Bukkit-family servers.

Recommended baseline:

- Spigot, Paper, or a compatible fork
- Vault if you want money-based prices
- PlaceholderAPI if you want PlaceholderAPI values in menus and messages

Some integrations are optional and only matter if you are using that plugin on your server.

## Step 1: install the plugin

1. Stop the server.
2. Place the ZaminShop jar in `plugins/`.
3. Start the server once.

On first boot, ZaminShop creates:

- `plugins/ZaminShop/config.yml`
- `plugins/ZaminShop/currency.yml`
- `plugins/ZaminShop/overwatcher.yml`
- `plugins/ZaminShop/lang/`
- `plugins/ZaminShop/guis/`
- `plugins/ZaminShop/shops/`

If no pack folders exist yet, the plugin seeds a default starter pack.

## Step 2: check the startup log

On a healthy startup, confirm:

- the plugin enabled successfully
- your selected economy provider was detected
- no critical validation errors were reported
- the starter shop pack loaded

If the plugin reports YAML problems, the new loader should point to the line and give a readable suggestion instead of a raw parser dump.

## Step 3: choose your command entry

By default, the starter pack main menu includes:

- `open_command: shop`

That means players can use:

```text
/shop
```

You can change that in the pack’s `main.yml`.

## Step 4: understand the file layout

The shop runtime is split intentionally.

### Global config

`plugins/ZaminShop/config.yml`

Use this for:

- database
- startup logging
- transaction safety
- sell limits
- suspicious transaction settings
- GUI file locations

### Currency providers

`plugins/ZaminShop/currency.yml`

Use this for:

- registered economy providers;
- provider display names and icons;
- physical item denominations;
- currency selection;
- currency-value safety.

### Overwatcher

`plugins/ZaminShop/overwatcher.yml`

Use this for:

- static price auditing;
- critical finding blocking;
- Runtime Shield purchase tracking;
- unsafe resale protection.

### Shared menus

`plugins/ZaminShop/guis/`

Use this for:

- amount selector
- bulk buy
- bulk sell
- favorites
- recent
- search
- sell menu
- GUI settings

### Shop packs

`plugins/ZaminShop/shops/<pack>/`

Each pack contains:

- `main.yml`
- `categories/*.yml`

## Step 5: test the default pack

Before editing anything, test the default flow:

1. open `/shop`
2. open at least one category
3. buy an item
4. sell an item
5. open favorites
6. run a search

If all of that works, your base install is good.

## Step 6: replace the starter content

Do not build everything in the default starter categories unless that is your final plan.

For a real deployment:

1. decide your pack structure
2. rename or create pack folders
3. update each pack `main.yml`
4. build category files around your actual economy

Follow [First Shop Pack Walkthrough](shops/first-shop-pack.md) for the clean path.

## Recommended first configuration changes

### Economy

If you use Vault, keep the shipped `providers.vault` entry enabled in `currency.yml` and make sure a Vault economy is installed.

### Overwatcher

Leave Overwatcher and Runtime Shield enabled unless you are diagnosing a specific conflict.

### Search

Keep search enabled unless your shop is intentionally tiny.

### Startup logging

Set `startup-log.debug: true` temporarily while building your first pack, then turn it back off once stable.

## Common early mistakes

### Editing the wrong file

Global behavior belongs in `config.yml`.
Pack behavior belongs in `shops/<pack>/main.yml`.
Category items belong in `shops/<pack>/categories/*.yml`.

### Forgetting that packs are self-contained

Newer ZaminShop setups do not register packs under `config.yml -> shops`.
The pack folder and its `main.yml` are the source of truth.

### Using unsupported item metadata on an older runtime

If the server version cannot represent a material or item feature, ZaminShop warns instead of silently faking support.

### Ignoring automatic validation

Read the Validation and Overwatcher console reports after every startup and reload.

## Next steps

- [First Shop Pack Walkthrough](shops/first-shop-pack.md)
- [config.yml Reference](configuration/config-yml.md)
- [currency.yml Reference](configuration/currency-yml.md)
- [Automatic Validation](validation.md)
- [Built-in Menus](gui/built-in-menus.md)
