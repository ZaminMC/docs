# Shop Packs

ZaminShop now uses a pack-based shop layout.

## How packs are loaded

Packs are registered manually in `config.yml`:

```yaml
shops:
  survival:
    folder: survival_shop
    enabled: true
    file: main.yml
```

Only packs listed in `config.yml -> shops` are loaded.

ZaminShop does **not** auto-discover every folder under `plugins/ZaminShop/shops/`.

## Pack folder structure

Each pack folder should look like this:

```text
plugins/ZaminShop/shops/survival_shop/
  main.yml
  categories/
    blocks.yml
    food.yml
    ores.yml
```

## What each file does

- `main.yml`: the pack entry menu
- `categories/*.yml`: the actual category shop menus

## Validation behavior

If a registered pack is broken:

- missing folder -> pack is skipped
- missing `main.yml` -> pack is skipped
- invalid category file -> that category is skipped

Use:

```text
/zaminshop validate
```

after editing a pack.
