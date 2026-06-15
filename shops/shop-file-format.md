# Shop Pack File Format

This page explains how pack `main.yml` files and category shop files are structured.

## Pack `main.yml`

This is the top-level menu for a pack.

Typical example:

```yml
enabled: true
shop_name: "Survival Shop"
menu_title: "&8Survival Shop"
size: 54
open_command:
  - shop
currencies:
  - vault

items:
  category_blocks:
    type: SHOP_CATEGORY
    material: GRASS_BLOCK
    slot: 20
    display-name: "&eBlocks"
    shop: blocks
```

## Common top-level keys

### `enabled`

Enables or disables the pack.

### `shop_name`

Friendly pack name used for display context.

### `menu_title`

Inventory title for the pack main menu.

### `rows` or `size`

Controls inventory size.

### `open_command`

Standalone root commands for the pack.

Example:

```yml
open_command:
  - shop
  - survivalshop
```

### `currencies`

Lists provider IDs registered in `currency.yml` that the pack exposes:

```yaml
currencies:
  - vault
  - points
```

Provider IDs are not economy type names. See [Multi-Currency Shops](multi-currency.md).

### `items`

Defines the rendered items in the pack main menu.

## Category files

Category files live in:

```text
shops/<pack>/categories/*.yml
```

These are full shop pages.

Typical example:

```yml
menu_title: "&8Blocks"
rows: 6

pagination:
  shop-item-slots:
    single-page:
      - 10-16
      - 19-25
      - 28-34

items:
  next-page:
    type: NEXT_PAGE
    material: ARROW
    slot: 53
    display-name: "&eNext Page"

  stone:
    type: SHOP_ITEM
    material: STONE
    quantity: 64
    buy-price: 32
    sell-price: 8
```

## Category-specific commands

Category files can define:

- `open_command`
- `open_sub_command`

Use `open_command` when the category should open directly:

```yml
open_command:
  - blocks
```

Use `open_sub_command` when it belongs under the pack root:

```yml
open_sub_command:
  - blocks
```

That gives:

```text
/shop blocks
```

when the pack root is `shop`.

## Item definitions

Items inside these files can be:

- `SHOP_ITEM`
- `SHOP_CATEGORY`
- `CUSTOM`
- `BACK`
- `PREVIOUS_PAGE`
- `NEXT_PAGE`

and other supported menu item types depending on the menu context.

## Page-aware item visibility

Items can be limited to pages using rules such as:

```yml
display-page: 2
```

or:

```yml
only-show-on-page: 1-3
```

Use this for:

- custom fillers
- page-specific instructions
- decorative edge items
- only-on-last-page navigation or status elements

## Best practice

### Keep main menus simple

The pack main menu should route the player, not contain the whole economy.

### Keep categories focused

Each category should represent one clear gameplay slice.

### Make navigation obvious

Always configure back and page controls intentionally once a category can exceed one page.

## Related pages

- [Adding Shop Items](shop-items.md)
- [Multi-Currency Shops](multi-currency.md)
- [Menu File Format](../gui/menu-file-format.md)
- [Built-in Menus](../gui/built-in-menus.md)
