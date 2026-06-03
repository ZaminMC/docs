# Adding Shop Items

This page covers the actual sellable and buyable entries inside category shop files.

## Modern shop item example

```yml
diamond:
  type: SHOP_ITEM
  material: DIAMOND
  quantity: 16
  buy-price: 250
  sell-price: 100
  display-name: "&bDiamond"
  lore:
    - "&7A valuable resource."
```

## Core keys

### `type`

For real shop entries, use:

```yml
type: SHOP_ITEM
```

### `material`

This is the main item definition path.

It supports:

- normal materials
- custom directives such as `oraxen-...`
- heads
- spawners
- placeholder-driven materials

Examples:

```yml
material: DIAMOND
material: oraxen-my_item
material: itemsadder-namespace:item
material: hdb-12345
material: SPAWNER-ZOMBIE
material: basehead-<base64>
```

### `quantity`

This is the transaction quantity for the shop item.

If a player buys the item, this is how many they receive.

### `buy-price` and `sell-price`

Missing key means the action is unavailable.

Examples:

```yml
buy-price: 100
sell-price: 40
```

If only `buy-price` exists:

- players can buy
- players cannot sell it back through that entry

## Custom display and lore

You can define:

- `display-name`
- `lore`

Use lore when:

- you want custom player-facing hints
- you want to explain a gated item
- the item needs clearer context than its material name

## Comparison and meta behavior

Shop items can compare different aspects of an item depending on your config and the item definition.

Examples include:

- meta
- model
- damage
- NBT
- repair cost

This matters most for selling and matching.

## Damage and legacy-style variants

ZaminShop supports a clean modern format first, with runtime-aware compatibility underneath.

Example:

```yml
damage: 5
```

Use this when the item’s runtime representation depends on durability or data.

The important rule:

- use modern readable material names in config where possible
- let the plugin resolve older runtime differences internally

## Permission-gated items

You can gate items with custom permissions.

Use this for:

- rank-locked content
- donor-only items
- progression unlocks

When combined with access lore, this lets the item stay visible while still being blocked.

## Hooked and custom items

The unified material directive path supports many optional item hooks.

Examples:

- Oraxen
- Nexo
- ItemsAdder
- MMOItems
- HeadDatabase

This keeps your config format cleaner than scattering plugin-specific keys everywhere.

## Spawners

Spawner items use the same unified material path:

```yml
material: SPAWNER-ZOMBIE
```

Spawner handling can still delegate to:

- the built-in spawner path
- an external hooked spawner provider

The config format stays the same.

## Common mistakes

### Mixing display amount with transaction quantity

The runtime should treat `quantity` as the real purchased or sold amount.

### Using old provider-specific keys in new configs

Prefer the unified `material:` directive path.

### Forgetting sell safety

If a sell path looks safe in one category, check the whole server economy. Risk guard can catch cross-category and cross-pack issues, but your pricing still needs intent.

## Related pages

- [Shop Pack File Format](shop-file-format.md)
- [Item and Spawner Hooks](../integrations/hooks.md)
- [Safety, Risk Guard, and Audit](../configuration/safety.md)
