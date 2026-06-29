# Menus

Menus are YAML inventories.

ZaminShop uses standalone menus, shop pack menus, category menus, and shared menus.

## Basic Menu

```yaml
menu_title: "&8Example Menu"
size: 27
open_command: examplemenu
register_command: true

items:
  info:
    type: CUSTOM
    material: OAK_SIGN
    slot: 13
    display-name: "&eInformation"
    lore:
      - "&7This is a custom menu item."
```

## Menu Options

| Option | Description |
| ------ | ----------- |
| `menu_title` | Inventory title. |
| `shop-name` | Supported by menu validation for older or alternate menu files. |
| `size` | Inventory size. |
| `rows` | Inventory rows. |
| `open_command` | Command that opens the menu. |
| `open-commands` | Command list form. |
| `register-command` | Registers the command dynamically. |
| `update-interval` | Refresh interval. |
| `refresh` | Alternate refresh key. |
| `open-requirement` | Requirement checked before opening. |
| `open-actions` | Actions run when opening. |
| `close-actions` | Actions run when closing. |
| `pagination` | Pagination layout. |
| `items` | Menu items. |

## Click Action Keys

```yaml
left-click-actions:
  - "[message] &aLeft click"
right-click-actions:
  - "[message] &eRight click"
shift-left-click-actions:
  - "[message] &bShift left"
shift-right-click-actions:
  - "[message] &dShift right"
middle-click-actions:
  - "[message] &6Middle click"
click-actions:
  - "[message] &7Any click"
```

## Built-In Menus

Confirmed built-in menu IDs:

| Menu ID | File |
| ------- | ---- |
| `amount-selector` | `shops/shared_menus/amount-selectors/default.yml` |
| `bulk-buy` | `shops/shared_menus/bulk-buy/default.yml` |
| `bulk-sell` | `shops/shared_menus/bulk-sell/default.yml` |
| `confirm-purchase` | `shops/shared_menus/purchase-confirmation/default.yml` |
| `favorites` | `menus/favorites_menu.yml` |
| `recent` | `menus/recent_menu.yml` |
| `search` | `menus/search_menu.yml` |
| `sell` | `menus/sell_menu.yml` |

## Different Amount Selectors

Create another file:

```text
plugins/ZaminShop/shops/shared_menus/amount-selectors/compact.yml
```

Then set the shop pack:

```yaml
amount-selector: "compact.yml"
```

Amount selector button IDs used by the click handler:

```text
set1
remove10
remove1
add1
add10
set16
set64
confirm
cancel
sellAll
buyMore
sellMore
```

Custom amount input item types:

```yaml
type: AMOUNT
type: AMOUNT_CHAT
type: AMOUNT_ANVIL
type: AMOUNT_SIGN
```
