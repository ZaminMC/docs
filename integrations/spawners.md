---
description: Configure built-in and external spawner item handling.
---

# Spawner Providers

ZaminShop can create and compare normal mob spawners through its internal implementation or a detected external spawner provider.

## Preferred provider

`config.yml` contains:

```yaml
spawnerProvider: ""
```

Leave the value empty to use:

- the only detected external provider; or
- ZaminShop's built-in spawner support when no external provider is selected.

When more than one supported external provider is installed, set the exact registered provider name printed in the server log.

MineableSpawners and SilkSpawners require separate bridge plugins:

```text
ZaminShopMineableSpawnersBridge
ZaminShopSilkSpawnersBridge
```

If either base plugin is detected without its bridge, ZaminShop prints a warning and the configured bridge download location.

## Shop item

Use a normal shop item with `material: SPAWNER` and a mob:

```yaml
items:
  zombie-spawner:
    type: SHOP_ITEM
    material: SPAWNER
    mob: ZOMBIE
    slot: 13
    buy-price: 50000
    sell-price: 25000
```

`mob-type` is accepted as an alias:

```yaml
mob-type: ZOMBIE
```

## Display-only spawner

```yaml
items:
  spawner-information:
    type: CUSTOM
    material: SPAWNER
    mob: ZOMBIE
    slot: 13
    display-name: "&eSpawner Shop"
```

As with custom items, `CUSTOM` is only for display. Use `SHOP_ITEM` when the player must buy or sell the spawner.

## MythicMobs spawners

MythicMobs has a separate item-provider path:

```yaml
items:
  mythic-spawner:
    type: SHOP_ITEM
    mythicMobs:
      spawner: SkeletonKing
    slot: 13
    buy-price: 50000
    sell-price: 25000
```

That syntax asks MythicMobs to generate its spawner item. It is different from `material: SPAWNER` plus a Bukkit entity type.

## Reloading

Changing `spawnerProvider` should be followed by a full restart. Installing or removing a spawner plugin always requires a full restart.
