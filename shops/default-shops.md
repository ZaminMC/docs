# Bundled Default Pack

ZaminShop ships with a bundled starter pack that can be copied into a registered pack folder.

## Bundled categories

The bundled category set includes:

- `armor.yml`
- `blocks.yml`
- `drops.yml`
- `dyes.yml`
- `farming.yml`
- `food.yml`
- `miscellaneous.yml`
- `ores.yml`
- `tools.yml`

## Bundled main menu

The bundled pack also includes:

```text
default-shop/main.yml
```

At runtime, that file is copied into a registered pack folder as the pack's `main.yml` when needed.

## What the starter pack is for

Use the bundled pack as a starting point when:

- you want a working first shop quickly
- you want examples of category buttons
- you want examples of shared menu links like favorites, recent, and sell GUI

## Important note

The bundled files are just starter content.

If you rename the pack folder, update `config.yml -> shops` to match the new folder name. ZaminShop will not keep loading an old `default` folder unless you still register it.
