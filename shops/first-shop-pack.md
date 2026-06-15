---
description: Build a complete two-category shop pack using files that can be pasted directly.
---

# Build Your First Shop Pack

This example creates:

- `/shop` as the pack entry;
- a main category menu;
- a blocks shop;
- an ores shop;
- back and page navigation;
- buy and sell prices.

It uses only standard Bukkit materials and the shipped `vault` provider.

Before using this pack, install Vault and a Vault-compatible economy, or replace `vault` with another enabled provider ID from `currency.yml`.

## Folder structure

Create:

```text
plugins/ZaminShop/shops/starter_shop/main.yml
plugins/ZaminShop/shops/starter_shop/categories/blocks.yml
plugins/ZaminShop/shops/starter_shop/categories/ores.yml
```

## main.yml

```yaml
enabled: true
shop_name: "Starter Shop"
menu_title: "&8Starter Shop"
size: 27
open_command:
  - shop
currencies:
  - vault

items:
  filler:
    type: CUSTOM
    material: GRAY_STAINED_GLASS_PANE
    slots:
      - 0-26
    display-name: "&r"
    priority: 100

  blocks:
    type: SHOP_CATEGORY
    material: GRASS_BLOCK
    slot: 11
    display-name: "&aBuilding Blocks"
    lore:
      - "&7Buy and sell common blocks."
      - ""
      - "&eClick to open"
    shop: blocks
    priority: 1

  ores:
    type: SHOP_CATEGORY
    material: DIAMOND
    slot: 15
    display-name: "&bOres and Minerals"
    lore:
      - "&7Buy and sell mined resources."
      - ""
      - "&eClick to open"
    shop: ores
    priority: 1

  sell-menu:
    type: CUSTOM
    material: HOPPER
    slot: 22
    display-name: "&eSell Inventory"
    lore:
      - "&7Open the shared sell menu."
    left-click-actions:
      - "[open] sell"
    priority: 1
```

## categories/blocks.yml

```yaml
menu_title: "&8Building Blocks"
rows: 6
open_sub_command:
  - blocks

pagination:
  shop-item-slots:
    - 10-16
    - 19-25
    - 28-34
    - 37-43

items:
  filler:
    type: CUSTOM
    material: GRAY_STAINED_GLASS_PANE
    slots:
      - 0-53
    display-name: "&r"
    priority: 100

  stone:
    type: SHOP_ITEM
    material: STONE
    quantity: 64
    buy-price: 32
    sell-price: 8
    priority: 1

  cobblestone:
    type: SHOP_ITEM
    material: COBBLESTONE
    quantity: 64
    buy-price: 24
    sell-price: 6
    priority: 1

  oak-planks:
    type: SHOP_ITEM
    material: OAK_PLANKS
    quantity: 64
    buy-price: 48
    sell-price: 12
    priority: 1

  glass:
    type: SHOP_ITEM
    material: GLASS
    quantity: 32
    buy-price: 40
    sell-price: 8
    priority: 1

  previous-page:
    type: PREVIOUS_PAGE
    material: PAPER
    slot: 48
    display-name: "&ePrevious Page"
    show-when-unavailable: false
    priority: 1

  back:
    type: BACK
    material: BARRIER
    slot: 49
    display-name: "&cBack to Starter Shop"
    priority: 1

  next-page:
    type: NEXT_PAGE
    material: PAPER
    slot: 50
    display-name: "&eNext Page"
    show-when-unavailable: false
    priority: 1
```

## categories/ores.yml

```yaml
menu_title: "&8Ores and Minerals"
rows: 6
open_sub_command:
  - ores

pagination:
  shop-item-slots:
    - 10-16
    - 19-25
    - 28-34
    - 37-43

items:
  filler:
    type: CUSTOM
    material: BLACK_STAINED_GLASS_PANE
    slots:
      - 0-53
    display-name: "&r"
    priority: 100

  coal:
    type: SHOP_ITEM
    material: COAL
    quantity: 16
    buy-price: 48
    sell-price: 12
    priority: 1

  iron-ingot:
    type: SHOP_ITEM
    material: IRON_INGOT
    quantity: 8
    buy-price: 160
    sell-price: 40
    priority: 1

  gold-ingot:
    type: SHOP_ITEM
    material: GOLD_INGOT
    quantity: 8
    buy-price: 240
    sell-price: 60
    priority: 1

  diamond:
    type: SHOP_ITEM
    material: DIAMOND
    quantity: 1
    buy-price: 500
    sell-price: 125
    priority: 1

  previous-page:
    type: PREVIOUS_PAGE
    material: PAPER
    slot: 48
    display-name: "&ePrevious Page"
    show-when-unavailable: false
    priority: 1

  back:
    type: BACK
    material: BARRIER
    slot: 49
    display-name: "&cBack to Starter Shop"
    priority: 1

  next-page:
    type: NEXT_PAGE
    material: PAPER
    slot: 50
    display-name: "&eNext Page"
    show-when-unavailable: false
    priority: 1
```

## Load the pack

Run:

```text
/zaminshop reload
```

Read the automatic Validation and Overwatcher reports in the console before testing.

Test:

```text
/shop
/shop blocks
/shop ores
```

The first command opens the pack main menu because `shop` is a built-in ZaminShop root. The category `open_sub_command` values create the two subcommand routes.

## Permissions

Players need the root command permission:

```text
zaminshop.player.shop
```

Each category also checks its generated shop permission:

```text
zaminshop.player.shops.starter_shop:blocks
zaminshop.player.shops.starter_shop:ores
```

Complete LuckPerms setup for the default group:

```text
/lp group default permission set zaminshop.player.shop true
/lp group default permission set zaminshop.player.shops.starter_shop:blocks true
/lp group default permission set zaminshop.player.shops.starter_shop:ores true
/lp group default permission set zaminshop.player.sell-gui true
```

## Next changes

- Add item metadata from [Item construction](item-options.md).
- Add external items from [Custom item providers](../integrations/custom-items.md).
- Add access conditions from [Permissions and access control](access-control.md).
- Change clicks and navigation with [Actions](../gui/actions.md).
