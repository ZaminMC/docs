---
description: Files and categories created by ZaminShop's bundled survival_shop pack.
---

# Bundled Starter Pack

When `plugins/ZaminShop/shops/` has no pack folders, ZaminShop creates:

```text
plugins/ZaminShop/shops/survival_shop/
```

It copies the bundled main menu and category resources only when no pack folder already exists.

## Files

```text
shops/
└── survival_shop/
    ├── main.yml
    └── categories/
        ├── building_blocks.yml
        ├── colorful_blocks.yml
        ├── food.yml
        ├── minerals.yml
        ├── miscellaneous.yml
        ├── mob_drops.yml
        ├── redstone_items.yml
        └── spawners.yml
```

## Main menu

The bundled `main.yml` contains:

- `/shop` as its open command;
- links to all eight categories;
- buttons for the sell, favorites, and recent menus;
- a balance display using an external Vault placeholder;
- decorative filler and selection items.

## Category behavior

The categories use:

- `SHOP_ITEM` entries;
- automatic shop-item pagination slots;
- `CUSTOM` filler items;
- previous, back, and next controls;
- buy and sell prices where configured.

Some products contain only a buy price in the bundled resources. The current missing-price loader behavior has a documented source contradiction; review [Buying and selling](buying-selling.md) before relying on omission to disable selling.

## Pack discovery

There is no `config.yml -> shops` registration section. Every folder under `plugins/ZaminShop/shops/` is inspected:

- missing `main.yml`: skipped with a warning;
- `enabled: false`: ignored;
- valid enabled `main.yml`: loaded as a pack;
- category YAML under `categories/`: loaded into that pack.

## Editing the starter

The copied files are normal server configuration files. ZaminShop does not overwrite existing copies when starting.

After editing:

```text
/zaminshop reload
```
