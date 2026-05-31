# Shop File Format

Category shop files are menu files with shop-aware item types.

They are usually stored under:

```text
plugins/ZaminShop/shops/<pack>/categories/*.yml
```

## Root keys

Common keys supported by the current loader:

| Key | Purpose |
|---|---|
| `menu_title` | Shop inventory title |
| `rows` | Inventory rows |
| `size` | Inventory size |
| `economy` | Optional economy override |
| `pagination` | Paged slot layout for shop items |
| `items` | Item definitions |
| `denyDirectAccess` | Blocks direct opening when enabled |
| `enablePerItemPermissions` | Enables per-item access checks |
| `enableBuyGUI` | Enables amount selector for buying |
| `enableSellGUI` | Enables amount selector for selling |
| `enableBuyMoreGUI` | Enables bulk buy flow |
| `enableSellMoreGUI` | Enables bulk sell flow |
| `enableSellGUISellAll` | Enables sell-all behavior in sell GUI |
| `messageBuy` | Shop-specific buy message |
| `messageSell` | Shop-specific sell message |
| `messageSellAll` | Shop-specific sell-all message |
| `messageCannotAfford` | Shop-specific cannot-afford message |
| `worldsWhitelist` | Allowed worlds |
| `worldsBlacklist` | Blocked worlds |

## Minimal example

```yaml
menu_title: "&8Blocks"
rows: 6

pagination:
  shop-item-slots:
    - 10-16
    - 19-25
    - 28-34

items:
  stone:
    type: SHOP_ITEM
    material: STONE
    amount: 64
    quantity: 64
    buy-price: 10
    sell-price: 2

  back:
    type: BACK
    material: BARRIER
    slot: 49
    display-name: "&cBack"
    left_click_actions:
      - "[back]"
```

## Pagination

For category shops, pagination is driven by:

```yaml
pagination:
  shop-item-slots:
```

You can use:

- a single slot list
- `single-page`
- `first-page`
- `middle-page`
- `last-page`

Example:

```yaml
pagination:
  shop-item-slots:
    single-page:
      - 10-16
      - 19-25
    first-page:
      - 10-17
      - 19-26
    middle-page:
      - 9-17
      - 18-26
    last-page:
      - 10-16
      - 19-25
```

## Navigation items

Category shops support menu navigation items directly inside `items:`

- `PREVIOUS_PAGE`
- `NEXT_PAGE`
- `BACK`

These are regular menu items and can use:

- `slot`
- `display-name`
- `show-when-unavailable`
- click actions
