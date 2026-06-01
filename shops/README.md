# Build Shop Packs

This section is where ZaminShop becomes your server's shop system instead of just a plugin that loaded successfully.

Shop packs are the heart of the plugin.

## What a pack is

A shop pack is a folder with:

- one main menu
- one categories folder
- one internal pack id from `config.yml`

This makes it possible to keep separate shop experiences for different parts of your server.

Examples:

- survival shop
- donor shop
- event shop
- prison shop

## How packs are loaded

Packs are registered manually in `config.yml`.

Example:

```yaml
shops:
  survival:
    folder: survival_shop
    enabled: true
    file: main.yml
```

Only packs listed there are loaded.

ZaminShop does **not** auto-discover every folder under `plugins/ZaminShop/shops/`.

## Pack folder structure

Example:

```text
plugins/ZaminShop/shops/survival_shop/
  main.yml
  categories/
    blocks.yml
    food.yml
    ores.yml
```

## What each part does

### `main.yml`

This is the entry menu for the pack.

It usually contains:

- category buttons
- sell menu button
- favorites button
- recent button
- profile or balance items

### `categories/*.yml`

These are the actual shop menus where transactional items live.

They control:

- displayed items
- prices
- pagination
- category-specific messages
- category-specific menu actions

## Best way to learn this section

Read these pages in order:

1. [First Shop Pack Walkthrough](first-shop-pack.md)
2. [Shop Pack File Format](shop-file-format.md)
3. [Adding Shop Items](shop-items.md)
4. [Bundled Starter Pack](default-shops.md)
5. [Limited Items](limited-items.md)

## Validation behavior

If a registered pack is broken:

- missing folder -> pack is skipped
- missing `main.yml` -> pack is skipped
- invalid category file -> that category is skipped

Always run:

```text
/zaminshop validate
```

after pack changes.
