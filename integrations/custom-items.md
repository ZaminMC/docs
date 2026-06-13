---
description: Display, buy, and sell items supplied by HeadDatabase and other custom-item plugins.
---

# Custom Item Providers

Custom-item integrations are used inside a normal shop item. They do **not** use `type: CUSTOM`.

{% hint style="danger" %}
`type: CUSTOM` creates a static GUI item. It is suitable for buttons, decoration, and information. It does not create a purchasable or sellable shop product.
{% endhint %}

For an external item that players can buy or sell, use:

```yaml
type: SHOP_ITEM
```

and add the provider-specific key documented below.

## HeadDatabase

### Purchasable shop item

```yaml
items:
  decorative-head:
    type: SHOP_ITEM
    headDatabase: "1234"
    slot: 13
    buy-price: 250
    sell-price: 75
```

The equivalent material directive is:

```yaml
items:
  decorative-head:
    type: SHOP_ITEM
    material: "hdb-1234"
    slot: 13
    buy-price: 250
    sell-price: 75
```

`1234` demonstrates the accepted ID format. Head IDs belong to the installed HeadDatabase data set; verify that the chosen ID exists on the server.

### Static display item

To display a HeadDatabase head as a non-transactional menu button:

```yaml
items:
  information:
    type: CUSTOM
    headDatabase: "1234"
    slot: 13
    display-name: "&eShop Information"
    lore:
      - "&7This item is only a menu button."
```

This answers the important type distinction:

- sellable/buyable HDB head: `SHOP_ITEM`;
- display-only HDB head: `CUSTOM`.

HeadDatabase finishes loading its database after normal plugin enable. ZaminShop listens for `DatabaseLoadEvent` and refreshes the provider when the database becomes ready.

## Oraxen

```yaml
items:
  oraxen-item:
    type: SHOP_ITEM
    oraxen: "item_id"
    slot: 13
    buy-price: 250
    sell-price: 75
```

Material directive:

```yaml
material: "oraxen-item_id"
```

The exact item ID is defined in Oraxen.

## Nexo

```yaml
items:
  nexo-item:
    type: SHOP_ITEM
    nexo: "item_id"
    slot: 13
    buy-price: 250
    sell-price: 75
```

Material directive:

```yaml
material: "nexo-item_id"
```

## ItemsAdder

```yaml
items:
  itemsadder-item:
    type: SHOP_ITEM
    itemsAdder: "namespace:item_id"
    slot: 13
    buy-price: 250
    sell-price: 75
```

Material directive:

```yaml
material: "itemsadder-namespace:item_id"
```

ItemsAdder loading is completed by an external event. ZaminShop refreshes the provider when that event is received.

## MMOItems

```yaml
items:
  mmo-item:
    type: SHOP_ITEM
    mmoItems:
      type: SWORD
      id: STEEL_SWORD
    slot: 13
    buy-price: 250
    sell-price: 75
```

Both `type` and `id` are required inside `mmoItems`.

## MythicMobs

Normal Mythic item:

```yaml
items:
  mythic-item:
    type: SHOP_ITEM
    mythicMobs: SkeletonKingSword
    slot: 13
    buy-price: 250
    sell-price: 75
```

Explicit item form:

```yaml
mythicMobs:
  item: SkeletonKingSword
```

Mob egg form:

```yaml
mythicMobs:
  egg: SkeletonKing
```

Mythic spawner form:

```yaml
mythicMobs:
  spawner: SkeletonKing
```

The names must match MythicMobs item or mob identifiers on the server.

## Slimefun

```yaml
items:
  slimefun-item:
    type: SHOP_ITEM
    slimefun: "SLIMEFUN_ITEM_ID"
    slot: 13
    buy-price: 250
    sell-price: 75
```

## CraftEngine

```yaml
items:
  craftengine-item:
    type: SHOP_ITEM
    craftEngine: "namespace:item_id"
    slot: 13
    buy-price: 250
    sell-price: 75
```

The provider requires an ID containing `:`.

## CrackShot

```yaml
items:
  crackshot-weapon:
    type: SHOP_ITEM
    crackShot: "weapon_id"
    slot: 13
    buy-price: 250
    sell-price: 75
```

## QualityArmory

```yaml
items:
  qualityarmory-item:
    type: SHOP_ITEM
    qualityArmory: "item_id"
    slot: 13
    buy-price: 250
    sell-price: 75
```

## WeaponMechanics

Weapon:

```yaml
items:
  weapon:
    type: SHOP_ITEM
    weaponMechanics:
      weapon: "weapon_id"
    slot: 13
    buy-price: 250
    sell-price: 75
```

Ammo:

```yaml
items:
  ammo:
    type: SHOP_ITEM
    weaponMechanics:
      ammo: "ammo_id"
    slot: 13
    buy-price: 25
    sell-price: 5
```

Only one of `weapon` or `ammo` should be set.

## CustomItems

```yaml
items:
  customitems-item:
    type: SHOP_ITEM
    customItems: "item_id"
    slot: 13
    buy-price: 250
    sell-price: 75
```

## Brewery

```yaml
items:
  brew:
    type: SHOP_ITEM
    brewery:
      recipe: "recipe_name"
      quality: 5
    slot: 13
    buy-price: 250
    sell-price: 75
```

`quality` must not be `0`, and `recipe` must match a Brewery recipe.

## ExecutableItems

```yaml
items:
  executable-item:
    type: SHOP_ITEM
    executableItems: "item_id"
    slot: 13
    buy-price: 250
    sell-price: 75
```

## ExecutableBlocks

```yaml
items:
  executable-block:
    type: SHOP_ITEM
    executableBlocks: "block_id"
    slot: 13
    buy-price: 250
    sell-price: 75
```

ExecutableItems and ExecutableBlocks depend on their external APIs and the shared SCore environment declared by those plugins.

## Display overrides

Provider items can still be assigned shop lore, slots, prices, permissions, and transaction actions. Changing display metadata may also affect selling when metadata comparison is enabled.

Review:

- [Item options](../shops/item-options.md)
- [Buying and selling](../shops/buying-selling.md)
- [Access control](../shops/access-control.md)

## Selling behavior

Each provider decides how two external items are identified. ZaminShop calls the provider's comparison method in addition to the configured item comparison rules.

Do not rely only on the visible material. Two custom items can share a base material while representing different provider IDs.

## Common mistakes

### Using `type: CUSTOM` for a product

Use `SHOP_ITEM` for transactions. `CUSTOM` is display-only.

### Using the plugin display name as a YAML key

Keys are case-sensitive as shown in the examples: `headDatabase`, `itemsAdder`, `mmoItems`, `mythicMobs`, `weaponMechanics`, and so on.

### Copying an external ID from another server

ZaminShop passes the ID to the provider. Whether the ID exists is controlled by the external plugin's configuration or database.

### Reloading before the dependency exists

Install the provider plugin and restart the server. A ZaminShop reload cannot load a missing Bukkit plugin.
