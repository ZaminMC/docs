---
description: Complete reference for materials, names, lore, metadata, heads, potions, banners, fireworks, NBT, trims, and comparison behavior.
---

# Item Construction Reference

ZaminShop uses the same item loader for shop entries, GUI icons, placeholder items, and item-currency denominations. Once an item option works in this loader, it can be reused anywhere that accepts an item section.

## Minimal item

```yaml
material: DIAMOND
quantity: 1
```

`material` is the core value. `quantity` defaults to `1` and is forced to at least `1`.

## Common options

| Key | Type | Default | Purpose |
|---|---|---:|---|
| `material` | String | Required | Bukkit material or a supported material directive. |
| `quantity` | Integer | `1` | Stack amount and, for `SHOP_ITEM`, transaction quantity. |
| `damage` | Integer/string | `0` | Durability or legacy data value. |
| `name` | String | None | Item display name. |
| `display-name` | String | None | Alias used by menu and shop files; normalized to `name`. |
| `lore` | String list | Empty | Item lore. |
| `glow` | Boolean | `false` | Adds a hidden enchantment when the item has none. |
| `flags` | String list | Empty | Bukkit `ItemFlag` names. |
| `item-flags` | String list | Empty | Alias for `flags`. |
| `unbreakable` | Boolean | `false` | Marks the item unbreakable where supported. |
| `model` | Integer/string | None | Custom model data. |
| `custom-model-data` | Integer/string | None | Alias for `model`. |

Complete example:

```yaml
material: DIAMOND_SWORD
quantity: 1
name: "&bMiner's Blade"
lore:
  - "&7A display and transaction item."
glow: true
unbreakable: true
model: 1201
flags:
  - HIDE_ATTRIBUTES
  - HIDE_UNBREAKABLE
```

## Material directives

| Syntax | Result |
|---|---|
| `head-Zamin` | Player head owned by `Zamin`. |
| `texture-<value>` | Player head with the supplied texture value. |
| `basehead-<value>` | Alias for a texture head. |
| `base64-<value>` | Alias for a texture head. |
| `hdb-<id>` | HeadDatabase head. |
| `oraxen-<item-id>` | Oraxen item. |
| `nexo-<item-id>` | Nexo item. |
| `itemsadder-<namespace:item>` | ItemsAdder item. |
| `mmoitems-<type:id>` | MMOItems item. |
| `SPAWNER-<entity>` | Spawner for an entity. |
| `placeholder-<material>` | Resolves the remainder as the material value. |
| `potion_of_healing` | Potion with base type `INSTANT_HEAL`. |
| `splash_potion_of_strong_healing` | Strong splash healing potion. |
| `lingering_potion_of_long_swiftness` | Extended lingering speed potion. |

Values inside `<...>` come from Minecraft or the installed integration. They cannot be universal copy-paste IDs because ZaminShop does not create those external registries.

{% hint style="info" %}
For integrated items, `type: SHOP_ITEM` controls transaction behavior. The material directive chooses which actual item is displayed and delivered.
{% endhint %}

## Enchantments

```yaml
material: DIAMOND_PICKAXE
quantity: 1
enchantments:
  - "EFFICIENCY:5"
  - "UNBREAKING:3"
```

Each line must contain an enchantment name and integer level separated by `:`.

For `ENCHANTED_BOOK`, ZaminShop adds stored enchantments. Other materials receive unsafe enchantments, allowing levels beyond vanilla limits at item-construction time.

## Player heads

Owner:

```yaml
material: PLAYER_HEAD
owner: "Zamin"
```

Accepted owner aliases:

```text
skullOwner
skullowner
owner
headOwner
```

The structured owner form is:

```yaml
material: "head-Zamin"
```

Texture:

```yaml
material: PLAYER_HEAD
skin: "https://textures.minecraft.net/texture/..."
```

The `skin` loader accepts a value that ZaminShop's texture utilities can convert to a Minecraft skin URL. Invalid values raise an item-load error.

Owner strings containing placeholders are stored for viewer-time resolution.

## Leather color

```yaml
material: LEATHER_CHESTPLATE
color: "38,192,210"
```

`rgb` is also accepted:

```yaml
material: LEATHER_BOOTS
rgb: "38,192,210"
```

Supported materials are the leather armor pieces and leather horse armor.

## Potions

Base potion:

```yaml
material: POTION
potion:
  type: INSTANT_HEAL
  level: 2
  extended: false
  color: "255,0,0"
```

Custom effects:

```yaml
material: SPLASH_POTION
potion_effects:
  - "SPEED;1200;1"
  - "JUMP;1200;0"
```

Each effect is:

```text
<PotionEffectType>;<duration in ticks>;<amplifier>
```

Invalid effect lines are ignored. Invalid base potion types throw a potion-load error.

`OMINOUS_BOTTLE` uses `potion.level` as an amplifier on runtimes that support its metadata, clamped to levels 1 through 5 internally.

## Banners and shields

Modern section form:

```yaml
material: WHITE_BANNER
base_color: WHITE
patterns:
  stripe:
    color: RED
    type: STRIPE_CENTER
  border:
    color: BLACK
    type: BORDER
```

Legacy list form:

```yaml
material: WHITE_BANNER
banner_meta:
  - "RED;STRIPE_CENTER"
  - "BLACK;BORDER"
```

Shields use the same `base_color`, `patterns`, and `banner_meta` options.

Invalid individual pattern lines are ignored.

## Fireworks

Rocket:

```yaml
material: FIREWORK_ROCKET
fireworkPower: 2
fireworkEffects:
  primary:
    type: BALL_LARGE
    colors:
      - RED
      - WHITE
    fadeColors:
      - BLUE
    flicker: true
    trail: true
```

`fireworkPower` is applied only from `1` through `4`.

Firework star:

```yaml
material: FIREWORK_STAR
fireworkColor: RED
fireworkFadeColor: WHITE
```

Color names are Bukkit `DyeColor` values.

## Armor trims

Modern form:

```yaml
material: DIAMOND_CHESTPLATE
armorTrim:
  material: GOLD
  pattern: SENTRY
```

Legacy-key form:

```yaml
material: DIAMOND_CHESTPLATE
trim_material: GOLD
trim_pattern: SENTRY
```

Both material and pattern are required. Armor trims are applied only on runtimes that expose the trim API and only to armor pieces.

## Goat horns

```yaml
material: GOAT_HORN
musicInstrument: PONDER_GOAT_HORN
```

The loader searches Bukkit's music-instrument registry by namespaced key or enum text. Invalid instruments reject the item.

## Spawners and spawn eggs

Spawner:

```yaml
material: SPAWNER
mob: ZOMBIE
```

Equivalent directive:

```yaml
material: "SPAWNER-ZOMBIE"
```

Legacy spawn-egg metadata uses:

```yaml
material: MONSTER_EGG
mob: ZOMBIE
mobType: 54
```

The legacy entity tag path is used only on runtimes that require it.

## NBT and item components

NBT is configured under `nbt`. Each child ID is only a YAML identifier; the actual tag name comes from `key`.

```yaml
material: PAPER
nbt:
  custom_marker:
    type: STRING
    key: zamin_marker
    value: shop_reward
  custom_level:
    type: INT
    key: zamin_level
    value: 5
```

Supported types:

```text
BYTE
SHORT
INT
LONG
FLOAT
DOUBLE
BYTE_ARRAY
STRING
STRING_ARRAY
COMPOUND
INT_ARRAY
```

`STRING_ARRAY` uses a YAML list. `COMPOUND` uses a nested section. The remaining types use a scalar `value`.

On Minecraft 1.20.5 and newer component-style loading prefixes keys with `minecraft:`. `BYTE_ARRAY` is not written by the component path. Component-tag failures are logged and processing continues; legacy NBT failures can reject item loading.

## Shop comparison options

These options affect matching when players sell physical items:

| Key | Default | Behavior |
|---|---:|---|
| `compare-meta` | Global default, or automatically true when metadata is configured | Compare display metadata. |
| `compare-model` | `defaultItemSettings.compareModel` | Compare custom model data. |
| `compare-damage` | Global default, or automatically true for configured/legacy damage | Compare durability/data. |
| `compare-nbt` | Global default, or automatically true when NBT is configured | Compare NBT/components. |
| `compare-repair-cost` | `defaultItemSettings.compareRepairCost` | Compare anvil repair cost. |
| `strip-item-meta` | `defaultItemSettings.stripItemMeta` | Remove metadata from purchased items. |
| `max-stack-size` | Disabled | Override the shop item's stack cap when positive. |

Example for a named currency token:

```yaml
items:
  'server_token':
    type: SHOP_ITEM
    material: PAPER
    quantity: 1
    display-name: "&6Server Token"
    model: 1201
    buy-price: 100
    sell-price: 25
    compare-meta: true
    compare-model: true
    compare-damage: false
    compare-nbt: false
    compare-repair-cost: false
```

Without strict comparison, visually or structurally different items may match the same material. Set comparison options according to the identity rules of the item being traded.

## Placeholder display item

A transactional entry may display a different icon:

```yaml
items:
  'diamond_bundle':
    type: SHOP_ITEM
    material: DIAMOND
    quantity: 16
    buy-price: 3000
    sell-price: 1200
    placeholder:
      material: CHEST
      quantity: 1
      display-name: "&b16 Diamonds"
```

The player receives and sells the primary `DIAMOND` item. The GUI displays the `CHEST` placeholder.

If the placeholder cannot be loaded, ZaminShop reports a warning and uses the primary item.
