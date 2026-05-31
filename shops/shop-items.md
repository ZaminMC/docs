# Shop Items

Category shop files support both transactional items and menu-only items.

## Transactional shop items

The current shop loader maps these menu-style types into shop behavior:

- `SHOP_ITEM`
- `COMMAND`
- `PERMISSION`
- `ENCHANTMENT`

## Menu-only items inside category shops

These item types are handled by the menu layer, not the transaction loader:

- `CUSTOM`
- `SHOP_CATEGORY`
- `PREVIOUS_PAGE`
- `NEXT_PAGE`
- `BACK`

## Common keys

| Key | Purpose |
|---|---|
| `type` | Item behavior |
| `material` | Display or transaction item material |
| `amount` | GUI display amount |
| `quantity` | Transaction quantity |
| `buy-price` | Buy price |
| `sell-price` | Sell price |
| `slot` / `slots` | Fixed menu placement for non-paginated items |
| `display-name` | GUI name override |
| `lore` | GUI lore override |
| `display-page` | Optional page restriction for menu rendering |

## Important pricing rule

Negative pricing is not the current model.

- omit `buy-price` to disable buying
- omit `sell-price` to disable selling
- do not use `-1` as an old-style magic value

## `SHOP_ITEM` example

```yaml
carrot:
  type: SHOP_ITEM
  material: CARROT
  amount: 16
  quantity: 16
  buy-price: 40
  sell-price: 4
```

## `COMMAND` example

```yaml
rank_token:
  type: COMMAND
  material: PAPER
  buy-price: 5000
  sell-price: 0
  commands:
    - "lp user %player% parent add vip"
```

## `PERMISSION` example

```yaml
fly_access:
  type: PERMISSION
  material: FEATHER
  buy-price: 10000
  sell-price: 0
  permission: "essentials.fly"
```

## `ENCHANTMENT` example

```yaml
sharpness_1:
  type: ENCHANTMENT
  material: ENCHANTED_BOOK
  buy-price: 1500
  sell-price: 0
  enchantment: SHARPNESS
  enchantmentLevel: 1
  enchantmentStackSizeLimit: 1
```
