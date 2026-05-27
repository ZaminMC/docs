# Shop Items

Shop item loading supports multiple item types and source keys.

## Common keys

| Key | Meaning |
|---|---|
| `type` | Item type. Examples include normal item, command, permission, enchantment, shop link. |
| `page` / `pages` | Page placement. |
| `slot` / `slots` | GUI slot placement. |
| `material` | Bukkit material or supported item-provider format. |
| `amount` | Display stack amount. |
| `quantity` | Transaction quantity. |
| `buy-price` | Buy price. |
| `sell-price` | Sell price. |
| `permission` / `permissions` | Permission requirement or permission item payload. |
| `special` | Special item behavior. |
| `force` | Force behavior where supported. |
| `stacked`, `unstack` | Stack handling behavior. |

## Command items

Source-supported keys:

```yaml
commands:
  - "say %player% bought this"
requireInventorySpace: false
runSingleCommand: false
runAsBuyer: false
commandsLimit: 1
```

## Permission items

Source-supported keys:

```yaml
permission: "some.permission"
permissions:
  - "some.permission"
```

## Enchantment items

Source-supported keys:

```yaml
enchantment: SHARPNESS
enchantmentLevel: 1
enchantmentStackSizeLimit: 1
```

## Shop link items

Source-supported keys:

```yaml
shop: blocks
link:
  shop: blocks
  page: 1
```

Use this when a shop item should open another shop/page instead of buying an item.
