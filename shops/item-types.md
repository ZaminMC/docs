---
description: Every transactional and navigational item type accepted in category shop files.
---

# Shop Item Types

The `type` key decides what a category entry does. It does **not** identify which plugin created the item.

{% hint style="warning" %}
A HeadDatabase, Oraxen, ItemsAdder, or other hooked item that players can buy or sell still uses `type: SHOP_ITEM`. Use `type: CUSTOM` only for a static menu element.
{% endhint %}

## Type index

| Config type | Internal type | Purpose | Buyable | Sellable |
|---|---|---|---:|---:|
| `SHOP_ITEM` | `ITEM` | Buy or sell a physical item. | Yes | Yes |
| `PERMISSION` | `PERMISSION` | Purchase one or more permission nodes. | Yes | No |
| `ENCHANTMENT` | `ENCHANTMENT` | Apply an enchantment to the held item. | Yes | No |
| `COMMAND` | `COMMAND` | Purchase command execution. | Yes | No |
| `CUSTOM` | `DUMMY` | Static menu item or action button. | No | No |
| `SHOP_CATEGORY` | `SHOP_LINK` | Open another category shop. | No | No |
| `SPECIAL` | `SPECIAL` | Render a built-in special value. | No | No |

`ITEM`, `DUMMY`, and `SHOP_LINK` are also accepted directly because they are internal enum names. The public configuration names used by the bundled files are `SHOP_ITEM`, `CUSTOM`, and `SHOP_CATEGORY`.

## `SHOP_ITEM`

Use this for anything that enters or leaves the player's inventory.

```yaml
items:
  'diamond':
    type: SHOP_ITEM
    material: DIAMOND
    quantity: 4
    buy-price: 500
    sell-price: 125
```

The same type is used for hooked items:

```yaml
items:
  'head_database_item':
    type: SHOP_ITEM
    material: "hdb-1234"
    quantity: 1
    buy-price: 500
    sell-price: 50
```

The HeadDatabase ID above is syntax-only. ZaminShop cannot provide a universal ID because IDs come from the installed HeadDatabase catalog.

### Prices

The loader currently treats an omitted price as `0`. A configured negative or non-finite value is rejected. This means a missing key is not a reliable way to disable a direction in the current source even though one validation message says to omit it.

{% hint style="warning" %}
**Needs verification in code:** the loader's implementation defaults missing `buy-price` and `sell-price` to `0`, while its invalid-price diagnostic says omission disables that direction. Test the intended unbuyable/unsellable behavior on the target build before relying on omission.
{% endhint %}

## `PERMISSION`

Purchases permissions through the Vault permission bridge.

Single permission:

```yaml
items:
  'builder_access':
    type: PERMISSION
    material: NETHER_STAR
    quantity: 1
    buy-price: 25000
    permission: "server.builder"
```

Several global permissions:

```yaml
items:
  'builder_bundle':
    type: PERMISSION
    material: NETHER_STAR
    quantity: 1
    buy-price: 40000
    permissions:
      - "server.builder"
      - "server.builder.chat"
```

World-specific permissions:

```yaml
items:
  'world_builder_access':
    type: PERMISSION
    material: NETHER_STAR
    quantity: 1
    buy-price: 25000
    permissions:
      builder:
        permission: "server.builder"
        world: "world"
```

Options:

| Key | Behavior |
|---|---|
| `permission` | One global permission. |
| `permissions` as a list | Several global permissions. |
| `permissions` as sections | Permissions with optional `world` values. |
| `force` | Attempts the grant even when the permission is already present. Defaults to `false`. |

Vault and a compatible permission provider must be enabled. The entry is skipped when permission support cannot be enabled.

## `ENCHANTMENT`

Applies an enchantment to the item in the buyer's main hand.

```yaml
items:
  'sharpness_five':
    type: ENCHANTMENT
    material: ENCHANTED_BOOK
    quantity: 1
    buy-price: 10000
    enchantment: SHARPNESS
    enchantment-level: 5
    enchantment-stack-size-limit: 1
```

Options:

| Key | Required | Behavior |
|---|---:|---|
| `enchantment` | Yes | Enchantment name resolved by ZaminShop's enchantment-name mapper. |
| `enchantment-level` | Yes | Level to apply. Missing values become `0` and are not useful. |
| `enchantment-stack-size-limit` | No | Maximum held stack size accepted for this enchantment purchase. Defaults to `0`. |

Global behavior is controlled by:

```yaml
maxEnchantments: 3
limitEnchantmentLevelDiff: false
disableUnsafeEnchantmentCheck: false
allowEnchantmentLevelIncrease: true
```

## `COMMAND`

Charges the buyer and executes configured commands.

```yaml
items:
  'starter_reward':
    type: COMMAND
    material: CHEST
    quantity: 1
    buy-price: 5000
    commands:
      - "give %player% iron_pickaxe 1"
      - "give %player% bread 16"
    run-as-buyer: false
    run-single-command: false
    require-inventory-space: true
    commands-limit: 1
```

Options:

| Key | Default | Behavior |
|---|---:|---|
| `commands` | Empty list | Commands to execute. Do not include `/`. |
| `run-as-buyer` | `false` | `false` runs commands as console; `true` runs them as the buyer. |
| `run-single-command` | `false` | Runs only one command from the configured list per purchase. |
| `require-inventory-space` | `false` | Requires free inventory space before completing the purchase. |
| `commands-limit` | Display item amount | Caps command executions. |

The loader accepts an empty command list, but the purchase would have no useful result. Always configure at least one command.

## `CUSTOM`

Renders an item in the category GUI without creating a transaction entry.

```yaml
items:
  'information':
    type: CUSTOM
    material: BOOK
    slot: 4
    display-name: "&eShop information"
    lore:
      - "&7Left-click diamonds to buy."
      - "&7Right-click them to sell."
```

Use `slot` or `slots`, because static items are not automatically placed into the shop pagination layout.

`CUSTOM` items can define click actions:

```yaml
items:
  'open_sell_menu':
    type: CUSTOM
    material: HOPPER
    slot: 49
    display-name: "&aSell items"
    left-click-actions:
      - "[open] sell"
```

The menu system processes the action. The entry is not buyable or sellable.

## `SHOP_CATEGORY`

Opens another category.

```yaml
items:
  'open_minerals':
    type: SHOP_CATEGORY
    material: DIAMOND
    slot: 22
    display-name: "&bMinerals"
    shop: minerals
```

Accepted target forms:

```yaml
shop: minerals
```

or:

```yaml
link:
  shop: minerals
  page: 1
```

The target must be a loaded shop. Invalid targets are skipped with a warning.

## `SPECIAL`

The only implemented special element is `BALANCE`.

```yaml
items:
  'balance':
    type: SPECIAL
    special: BALANCE
    slot: 49
```

ZaminShop first looks for a configured balance special element. If none exists, it creates an emerald named `Balance` with `%balance%` in its lore.

## Menu-only types

These types are rendered by the menu system and are intentionally skipped by the transactional shop-item loader:

```text
CUSTOM
SHOP_CATEGORY
PREVIOUS_PAGE
NEXT_PAGE
BACK
SORT_CYCLE
FAVORITE_ITEM
RECENT_ITEM
SEARCH_ITEM
SELL_SLOT
SELL_ITEM
SELL_SUMMARY
```

Their complete behavior is documented under [Menu Item Types](../gui/item-types.md).
