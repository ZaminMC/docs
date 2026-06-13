# Common Questions

## Which command should players use?

Normally:

```text
/shop
```

That is the main player entry point.

## Which command should staff use?

For admin tasks:

```text
/zaminshop
```

That gives access to reload, validation, risk, language, and modifier tools.

## Where are the files I actually edit?

Most servers will work with four areas:

- `config.yml`
- `guis/*.yml`
- `shops/<pack>/main.yml`
- `shops/<pack>/categories/*.yml`

## Does ZaminShop auto-load every folder inside `plugins/ZaminShop/shops/`?

Yes, when the folder contains an enabled `main.yml`. A folder without `main.yml`, a disabled pack, or a pack with invalid YAML is skipped with a validation or startup message.

## What is the difference between `guis/` and `shops/`?

`guis/` contains shared menus used across the plugin.

`shops/` contains the actual pack main menus and category shop menus.

## Why does the plugin have both validation and risk guard?

Because they solve different problems.

- validation checks whether the files are structurally usable
- risk guard checks whether the prices are economically dangerous

You want both.

## How do players open the sell GUI?

Usually with:

```text
/shop sell
```

The player also needs the `zaminshop.player.sell-gui` permission and `sellGui.enabled` must be `true` in `guis/gui-settings.yml`.

## Are favorites and recent menus per-shop or global?

They are global player convenience features.

Search is pack-scoped, but favorites and recent history are not tied to just one category file.

## Can I move built-in menu files?

Yes, but update the path in `config.yml -> gui_menus`.

If the path is wrong, the plugin will not guess where you moved the file.

## What should I run after editing configs?

Run:

```text
/zaminshop validate
```

If you changed pricing or opened a new economy path, also check:

```text
/zaminshop risk list
```

## What if only operators can use the shop?

That is usually a permissions issue.

Start with:

- `zaminshop.player.shop`
- `zaminshop.player.search`
- `zaminshop.player.favorite`
- `zaminshop.player.recent`
- `zaminshop.player.sell-gui`

Or grant the full player group:

```text
zaminshop.player.*
```
