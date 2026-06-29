# Categories

Category files hold the items players buy and sell.

They live inside a shop pack:

```text
plugins/ZaminShop/shops/packs/survival_shop/categories/
```

## Example

```yaml
menu_title: "ZaminShop ➜ Building Blocks"
size: 54

items:
  stone:
    type: SHOP_ITEM
    material: STONE
    slot: 10
    buy-price: 16
    sell-price: 4

  oak_log:
    type: SHOP_ITEM
    material: OAK_LOG
    slot: 11
    buy-price: 24
    sell-price: 6

  previous:
    type: PREVIOUS_PAGE
    material: PAPER
    slot: 48
    display-name: "&ePrevious page"

  back:
    type: BACK
    material: BARRIER
    slot: 49
    display-name: "&cBack"

  next:
    type: NEXT_PAGE
    material: PAPER
    slot: 50
    display-name: "&eNext page"
```

## Options

| Option | Description |
| ------ | ----------- |
| `menu_title` | Category inventory title. |
| `size` | Inventory size. Use a multiple of 9. |
| `rows` | Alternative to `size`. |
| `items` | Items, buttons, and navigation entries. |
| `open_command` | Optional command for menus that support command registration. |
| `open-sub-command` | Supported by the menu root validator. Use only after testing in your setup. |
| `pagination` | Pagination layout options. |

## Shop Items

`SHOP_ITEM` entries are buy/sell items.

```yaml
diamond:
  type: SHOP_ITEM
  material: DIAMOND
  slot: 13
  buy-price: 250
  sell-price: 50
```

## Navigation

Use these item types for normal category navigation:

```yaml
previous:
  type: PREVIOUS_PAGE
  material: PAPER
  slot: 48
  display-name: "&ePrevious page"

back:
  type: BACK
  material: BARRIER
  slot: 49
  display-name: "&cBack"

next:
  type: NEXT_PAGE
  material: PAPER
  slot: 50
  display-name: "&eNext page"
```

## Category Titles

Category menu titles can use current context placeholders:

```yaml
menu_title: "Shop ➜ %zaminshop_current_category%"
```
