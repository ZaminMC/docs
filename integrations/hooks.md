# Item and Spawner Hooks

ZaminShop supports optional integrations for custom items and spawner handling.

The important goal is consistency:

- the config should stay readable
- unsupported integrations should fail cleanly
- missing plugins should not crash startup

## Unified material directives

Modern ZaminShop config prefers the unified `material:` directive path.

Examples:

```yml
material: oraxen-my_item
material: nexo-my_item
material: itemsadder-namespace:item
material: mmoitems-SWORD:my_item
material: hdb-12345
material: SPAWNER-ZOMBIE
```

This is cleaner than scattering plugin-specific keys across every item.

## Supported custom item paths

Depending on your server setup, ZaminShop can work with integrations such as:

- Oraxen
- Nexo
- ItemsAdder
- MMOItems
- HeadDatabase
- other supported item providers in the plugin runtime

These are optional integrations. If the plugin is not installed, the corresponding item directive cannot be resolved.

## Oraxen example

```yml
my_oraxen_blade:
  type: SHOP_ITEM
  material: oraxen-my_blade
  quantity: 1
  buy-price: 5000
```

## ItemsAdder example

```yml
custom_crop:
  type: SHOP_ITEM
  material: itemsadder-my_pack:custom_crop
  quantity: 16
  buy-price: 1200
```

## MMOItems example

```yml
boss_sword:
  type: SHOP_ITEM
  material: mmoitems-SWORD:boss_blade
  quantity: 1
  buy-price: 50000
```

## Heads

ZaminShop supports several head styles, including:

- player heads
- BaseHead values
- texture heads
- HeadDatabase ids

Examples:

```yml
material: head-Notch
material: basehead-<base64>
material: texture-<texture_id>
material: hdb-12345
```

## Spawners

Spawner items use:

```yml
material: SPAWNER-ZOMBIE
```

The config format stays the same whether the runtime uses:

- built-in spawner support
- an external spawner provider

## Legacy and version behavior

ZaminShop supports modern config syntax where possible, but it does not fake features on runtimes that fundamentally cannot represent them.

That means:

- modern names can map to legacy runtime equivalents where safe
- truly unsupported items on old versions produce readable warnings
- compatibility should not mean pretending every modern feature exists on 1.8

## Common mistakes

### Assuming the hook is loaded because the config looks right

The plugin providing the item still needs to be present and compatible.

### Mixing old provider-specific keys with the new material directive format

Prefer the unified `material:` format for new configs.

### Expecting modern-only items on old runtimes

If a material only exists in newer Minecraft versions, ZaminShop should warn clearly instead of forcing a fake item into existence.

## Related pages

- [Adding Shop Items](../shops/shop-items.md)
- [PlaceholderAPI](placeholderapi.md)
- [Version Compatibility](../developer/version-compat.md)
