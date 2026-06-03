# First Shop Pack Walkthrough

This walkthrough shows the clean way to build a pack from scratch.

## Goal

Build a pack called `survival_shop` with:

- one pack main menu
- a `/shop` command
- category pages such as blocks and ores
- links to shared menus such as sell and favorites

## Step 1: create the folder

Create:

```text
plugins/ZaminShop/shops/survival_shop/
```

Inside it, create:

```text
plugins/ZaminShop/shops/survival_shop/main.yml
plugins/ZaminShop/shops/survival_shop/categories/
```

## Step 2: create `main.yml`

Example:

```yml
enabled: true
shop_name: "Survival Shop"
menu_title: "&8Survival Shop"
size: 54
open_command:
  - shop

items:
  category_blocks:
    type: SHOP_CATEGORY
    material: GRASS_BLOCK
    slot: 20
    display-name: "&eBlocks"
    shop: blocks

  category_ores:
    type: SHOP_CATEGORY
    material: DIAMOND
    slot: 24
    display-name: "&eOres"
    shop: ores

  sell_menu:
    type: CUSTOM
    material: HOPPER
    slot: 49
    display-name: "&aSell Items"
    left_click_actions:
      - "[open] sell"
```

What this does:

- enables the pack
- gives it a friendly name
- opens it with `/shop`
- renders category buttons
- links to the shared sell menu

## Step 3: add a category

Create:

```text
plugins/ZaminShop/shops/survival_shop/categories/blocks.yml
```

Example:

```yml
menu_title: "&8Blocks"
rows: 6

pagination:
  shop-item-slots:
    single-page:
      - 10-16
      - 19-25
      - 28-34
    first-page:
      - 10-17
      - 19-26
      - 28-35
    middle-page:
      - 9-17
      - 18-26
      - 27-35
    last-page:
      - 9-17
      - 18-26
      - 27-34

items:
  previous-page:
    type: PREVIOUS_PAGE
    material: ARROW
    slot: 45
    display-name: "&ePrevious Page"
    show-when-unavailable: false

  back:
    type: BACK
    material: BARRIER
    slot: 49
    display-name: "&cBack"

  next-page:
    type: NEXT_PAGE
    material: ARROW
    slot: 53
    display-name: "&eNext Page"
    show-when-unavailable: false

  stone:
    type: SHOP_ITEM
    material: STONE
    quantity: 64
    buy-price: 32
    sell-price: 8

  oak_planks:
    type: SHOP_ITEM
    material: OAK_PLANKS
    quantity: 64
    buy-price: 48
    sell-price: 12
```

## Step 4: reload and validate

Run:

```text
/zaminshop reload
/zaminshop validate
```

This gives you:

- live pack loading
- validation diagnostics
- early warning if commands, menu links, or item formats are wrong

## Step 5: add more categories

Repeat the category pattern for:

- ores
- food
- farming
- tools
- armor

## Step 6: decide command strategy

You have three common choices:

### Pack root only

Players use:

```text
/shop
```

and browse categories from the main menu.

### Direct category commands

Define `open_command` in a category for something like:

```text
/blocks
```

### Pack-scoped subcommands

Define `open_sub_command` for:

```text
/shop blocks
```

This is usually the cleanest choice when the category belongs tightly to the pack.

## Common mistakes

### Putting shop items in `main.yml`

`main.yml` is usually for pack navigation, not the full store catalog.

### Forgetting pagination controls

If the category can exceed one page, configure page slots and navigation items intentionally.

### Overusing root commands

Not every category needs its own standalone command.

## Related pages

- [Shop Pack File Format](shop-file-format.md)
- [Adding Shop Items](shop-items.md)
- [Built-in Menus](../gui/built-in-menus.md)
