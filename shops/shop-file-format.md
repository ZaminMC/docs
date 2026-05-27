# Shop File Format

A shop file may contain these source-supported keys:

| Key | Meaning |
|---|---|
| `name` | Shop display name. |
| `namePerPage` | Optional page-specific names. |
| `menu_title` | GUI title override. |
| `rows` | Menu rows. Converted to inventory size. |
| `size` | Raw menu size. |
| `economy` | Economy provider override for this shop. |
| `enableBuyGUI` | Enable amount selector for buying. |
| `enableSellGUI` | Enable amount selector for selling. |
| `enableBuyMoreGUI` | Enable bulk buy GUI. |
| `enableSellMoreGUI` | Enable bulk sell GUI. |
| `enableSellGUISellAll` | Enables sell-all flow in sell GUI. |
| `enablePerItemPermissions` | Enables item permission checks. |
| `denyDirectAccess` | Prevent direct opening if configured. |
| `worldsWhitelist` | Worlds where shop is allowed. |
| `worldsBlacklist` | Worlds where shop is blocked. |
| `messageBuy` | Shop-specific buy message. |
| `messageSell` | Shop-specific sell message. |
| `messageSellAll` | Shop-specific sell-all message. |
| `messageCannotAfford` | Shop-specific insufficient funds message. |
| `items` | Shop items. |

## Minimal example

```yaml
name: "&8Blocks"
rows: 6
economy: VAULT

items:
  stone:
    type: item
    material: STONE
    buy-price: 10
    sell-price: 2
    page: 1
    slot: 10
```
