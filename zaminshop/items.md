# Items

Items are configured inside a menu or category file under `items:`.

## Basic Shop Item

```yaml
stone:
  type: SHOP_ITEM
  material: STONE
  slot: 10
  buy-price: 16
  sell-price: 4
```

## Basic Custom Button

```yaml
info:
  type: CUSTOM
  material: OAK_SIGN
  slot: 4
  display-name: "&eShop Info"
  lore:
    - "&7Left-click items to buy."
    - "&7Right-click items to sell."
```

## Common Options

| Option | Description |
| ------ | ----------- |
| `type` | Menu item type. |
| `material` | Bukkit material or supported custom material directive. |
| `slot` | Single inventory slot. |
| `slots` | Slot list or ranges, such as `0-8`. |
| `amount` | Display stack amount. |
| `quantity` | Alternative display amount key used by item parsing. |
| `display-name` | Item display name. |
| `lore` | Item lore lines. |
| `priority` | Which item wins when multiple entries use the same slot. Lower priority wins in configured menu rendering. |
| `glow` | Adds enchantment glow where supported. |
| `item-flags` / `flags` | Bukkit item flags. |
| `custom-model-data` | Legacy custom model data value. |
| `model` | Model setting accepted by the canonical item loader. |
| `item-model` | Modern item model key when supported by the server version. |
| `tooltip-style` | Tooltip style when supported by the server version. |
| `hide-tooltip` | Hides tooltip when supported by the server version. |
| `enchantment-glint-override` | Controls glint override when supported by the server version. |
| `nbt` and typed `nbt-*` sections | NBT matching/metadata options. |

## Menu Item Types

Confirmed item types from shipped menus and menu code:

| Type | Used for |
| ---- | -------- |
| `CUSTOM` | Static item or button. |
| `SHOP_ITEM` | Buy/sell item or selected shop item display. |
| `SHOP_CATEGORY` | Opens a category from a shop pack main menu. |
| `BACK` | Back button. |
| `NEXT_PAGE` | Next page button. |
| `PREVIOUS_PAGE` | Previous page button. |
| `AMOUNT` | Custom amount input button using the default input mode. |
| `AMOUNT_CHAT` | Custom amount input using chat. |
| `AMOUNT_ANVIL` | Custom amount input using an anvil. |
| `AMOUNT_SIGN` | Custom amount input using a sign. |
| `FAVORITE_ITEM` | Entry renderer for favorites menu. |
| `RECENT_ITEM` | Entry renderer for recent transactions menu. |
| `SEARCH_ITEM` | Entry renderer for search results menu. |
| `SORT_CYCLE` | Sort mode button. |
| `SELL_SLOT` | Sell GUI input slot. |
| `SELL_SUMMARY` | Sell GUI summary item. |

## Prices

```yaml
iron_ingot:
  type: SHOP_ITEM
  material: IRON_INGOT
  slot: 12
  buy-price: 32
  sell-price: 8
```

Use only a buy price for buy-only items:

```yaml
elytra:
  type: SHOP_ITEM
  material: ELYTRA
  slot: 14
  buy-price: 50000
```

Use only a sell price for sell-only items:

```yaml
cobblestone:
  type: SHOP_ITEM
  material: COBBLESTONE
  slot: 15
  sell-price: 1
```

## Currency Provider

Use a provider ID from `currency.yml`.

```yaml
diamond:
  type: SHOP_ITEM
  material: DIAMOND
  slot: 13
  buy-price: 250
  sell-price: 50
  currency-provider: vault
```

## Permission Item

Permission purchases are handled by the transaction service.

```yaml
vip_fly:
  type: PERMISSION
  material: FEATHER
  slot: 22
  display-name: "&bVIP Fly"
  buy-price: 10000
  permissions:
    - "server.fly"
```

You can also use one permission string:

```yaml
vip_home:
  type: PERMISSION
  material: ENDER_PEARL
  slot: 23
  display-name: "&bVIP Home"
  buy-price: 7500
  permission: "server.viphome"
```

World-specific permission entries use a section:

```yaml
nether_access:
  type: PERMISSION
  material: NETHERRACK
  slot: 24
  display-name: "&cNether Access"
  buy-price: 5000
  permissions:
    nether:
      permission: "server.nether"
      world: "world_nether"
```

## Command Item

Command items are bought through the command purchase handler.

```yaml
kit_starter:
  type: COMMAND
  material: CHEST
  slot: 23
  display-name: "&aStarter Kit"
  buy-price: 500
  commands:
    - "kit starter %player_name%"
  commands-limit: 1
```

## Enchantment Item

Enchantment purchases are handled by the enchantment purchase handler.

```yaml
sharpness:
  type: ENCHANTMENT
  material: ENCHANTED_BOOK
  slot: 24
  display-name: "&eSharpness I"
  buy-price: 1500
  enchantment: SHARPNESS
  enchantment-level: 1
  enchantment-stack-size-limit: 1
```

## Custom Material Directives

The material directive parser confirms these formats:

| Format | Description |
| ------ | ----------- |
| `head-<owner>` | Player head by owner name. |
| `basehead-<value>` | Base64/texture head value. |
| `hdb-<id>` | HeadDatabase head ID. |
| `oraxen-<item-id>` | Oraxen item. |
| `itemsadder-<namespace>:<item>` | ItemsAdder item. |
| `mmoitems-<type>:<id>` | MMOItems item. |

Example:

```yaml
dragon_head:
  type: SHOP_ITEM
  material: hdb-12345
  slot: 30
  buy-price: 1000
  sell-price: 100
```

## Provider Sections

The item providers also read provider-specific sections or keys:

```yaml
slimefun_item:
  type: SHOP_ITEM
  slimefun: COPPER_DUST
  slot: 10
  buy-price: 50
```

```yaml
nexo_item:
  type: SHOP_ITEM
  nexo: example_item
  slot: 10
  buy-price: 50
```

```yaml
craftengine_item:
  type: SHOP_ITEM
  craftEngine: "minecraft:example_item"
  slot: 10
  buy-price: 50
```

```yaml
customitems_item:
  type: SHOP_ITEM
  customItems: example_item
  slot: 10
  buy-price: 50
```

```yaml
mythic_item:
  type: SHOP_ITEM
  mythicMobs:
    item: ExampleItem
  slot: 11
  buy-price: 100
```

```yaml
brewery_item:
  type: SHOP_ITEM
  brewery:
    recipe: Wheatbeer
    quality: 5
  slot: 12
  buy-price: 250
```

See [Supported Plugins](supported-plugins.md) for confirmed provider keys.
