---
description: Restrict shop packs, categories, items, worlds, game modes, and GUI interactions.
---

# Permissions and Access Control

ZaminShop applies access controls at several independent layers. A player must pass every relevant layer.

## Category permission

Every category requires:

```text
zaminshop.player.shops.<shop-id>
```

Category IDs are scoped as `<pack-folder>:<category-file>`. For the bundled `minerals` shop:

```text
zaminshop.player.shops.survival_shop:minerals
```

## Additional category permissions

One permission:

```yaml
permission: "server.shop.minerals"
```

Several permissions:

```yaml
required-permissions:
  - "server.shop.minerals"
  - "server.rank.member"
```

All additional permissions must pass.

## Per-item permissions

Enable generated item nodes for a category:

```yaml
enable-per-item-permissions: true
```

Players then need either:

```text
zaminshop.player.items.<shop-id>.<item-id>
```

or:

```text
zaminshop.player.items.<shop-id>.*
```

Example:

```text
zaminshop.player.items.survival_shop:minerals.diamond
zaminshop.player.items.survival_shop:minerals.*
```

When `enable-per-item-permissions` is `false`, these generated item nodes are not checked.

## Additional item permissions

```yaml
items:
  'diamond':
    type: SHOP_ITEM
    material: DIAMOND
    buy-price: 500
    sell-price: 125
    required-permissions:
      - "server.rank.elite"
    permission-denied-lore:
      - "&cElite rank required."
```

These are checked regardless of `enable-per-item-permissions`.

## World filters

Whitelist:

```yaml
worlds-whitelist:
  - world
  - world_nether
```

Blacklist:

```yaml
worlds-blacklist:
  - creative
```

The loader uses the whitelist when both lists are present because it reads `worlds-whitelist` first and only checks the blacklist in the `else` branch.

World names are normalized to lowercase.

Global blocked worlds:

```yaml
disableShopsInWorlds:
  - creative
```

Bypass:

```text
zaminshop.player.bypass.world
```

## Game-mode restrictions

```yaml
disableShopsInGamemodes:
  - ADVENTURE
  - CREATIVE
  - SPECTATOR
```

Bypass:

```text
zaminshop.player.bypass.gamemode
```

Sell commands enforce the blocked world and game-mode lists directly. The shop root and player menus allow the corresponding bypass permissions.

## Direct access

```yaml
deny-direct-access: true
```

This option is loaded at category level and is intended to prevent opening the category outside its expected navigation path.

## Opening for another player

Administrative behavior:

```yaml
sudoAllowAllShopsAccess: false
disableSudoWorldPermissionCheck: false
disableSudoShopPermissionCheck: false
```

`sudoAllowAllShopsAccess` affects directory opening for a target. The world and shop permission switches control whether target checks are omitted in sudo-style open flows.

## GUI view requirements

Menu items can be hidden unless requirements pass:

```yaml
items:
  'elite_category':
    type: SHOP_CATEGORY
    material: DIAMOND
    slot: 22
    shop: minerals
    view-requirement:
      requirements:
        elite:
          type: has permission
          permission: "server.rank.elite"
```

## GUI click requirements

An item can remain visible but refuse a click:

```yaml
items:
  'elite_category':
    type: SHOP_CATEGORY
    material: DIAMOND
    slot: 22
    shop: minerals
    left-click-requirement:
      requirements:
        elite:
          type: has permission
          permission: "server.rank.elite"
      deny-actions:
        - "[message] &cElite rank required."
```

See [Requirements](../gui/requirements.md) for every supported rule type.
