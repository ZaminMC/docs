# Files & Folders

This is the current runtime layout used by ZaminShop.

## Root plugin folder

```text
plugins/ZaminShop/
```

Important files:

```text
config.yml
pricemodifiers.yml
lang/en_US.yml
```

## Shared GUI files

Shared menus live under:

```text
plugins/ZaminShop/guis/
```

Bundled files:

```text
amount-selector.yml
bulk-buy.yml
bulk-sell.yml
favorites.yml
gui-settings.yml
recent.yml
search.yml
sell.yml
```

The actual file paths are controlled by `config.yml -> gui_menus`.

## Shop packs

Shop packs live under:

```text
plugins/ZaminShop/shops/
```

Each pack is a folder registered manually in `config.yml -> shops`.

Example:

```text
plugins/ZaminShop/shops/survival_shop/
  main.yml
  categories/
    blocks.yml
    food.yml
    ores.yml
```

## What loads automatically

ZaminShop loads only:

- GUI files mapped under `config.yml -> gui_menus`
- shop packs registered under `config.yml -> shops`

It does **not** auto-discover random folders under `plugins/ZaminShop/shops/`.
