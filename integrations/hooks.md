---
description: Compatibility index for every optional plugin declared or registered by ZaminShop.
---

# Integration Compatibility Index

## Item providers

| Plugin | YAML key | Material directive | Notes |
| --- | --- | --- | --- |
| HeadDatabase | `headDatabase` | `hdb-<id>` | Waits for the database load event |
| Oraxen | `oraxen` | `oraxen-<id>` | External item ID |
| Nexo | `nexo` | `nexo-<id>` | External item ID |
| ItemsAdder | `itemsAdder` | `itemsadder-<namespace:id>` | Namespace is required by the directive |
| MMOItems | `mmoItems.type` and `.id` | `mmoitems-<type:id>` | Both values required |
| MythicMobs | `mythicMobs` | none | Item, egg, and spawner forms |
| Slimefun | `slimefun` | none | Slimefun item ID |
| CraftEngine | `craftEngine` | none | ID must contain `:` |
| CrackShot | `crackShot` | none | Weapon ID |
| QualityArmory | `qualityArmory` | none | Item ID |
| WeaponMechanics | `weaponMechanics.weapon` or `.ammo` | none | Weapon or ammo |
| CustomItems | `customItems` | none | Item ID |
| Brewery / BreweryX | `brewery.recipe` and `.quality` | none | Recipe and non-zero quality |
| ExecutableItems | `executableItems` | none | Requires ExecutableItems and SCore |
| ExecutableBlocks | `executableBlocks` | none | Requires ExecutableBlocks and SCore |

[Configuration examples](custom-items.md)

## Economy providers

| Plugin or source | Type |
| --- | --- |
| Minecraft experience | `EXP` |
| Minecraft experience levels | `EXP_LEVELS` |
| Built-in physical item economy | `ITEM` |
| Vault | `VAULT` |
| ExcellentEconomy | `EXCELLENT_ECONOMY` |
| CoinsEngine | `COINS_ENGINE` |
| GemsEconomy | `GEMS_ECONOMY` |
| MySQL-Tokens | `MYSQL_TOKENS` |
| PlayerPoints | `PLAYER_POINTS` |
| TokenEnchant | `TOKEN_ENCHANT` |
| TokenManager | `TOKEN_MANAGER` |
| VotingPlugin | `VOTING_PLUGIN` |
| API registration | `CUSTOM` |

## Spawner compatibility

Built-in spawner support is used when no external provider is active.

MineableSpawners and SilkSpawners require separate bridge plugins:

- `ZaminShopMineableSpawnersBridge`;
- `ZaminShopSilkSpawnersBridge`.

ZaminShop logs a warning with the bridge download location when it detects MineableSpawners or SilkSpawners without the corresponding bridge.

If exactly one external provider registers, it is selected automatically. If multiple providers register, set `spawnerProvider` to one of the names printed in the server log. An empty or invalid selection leaves built-in support active.

## Other soft dependencies

| Plugin | Role |
| --- | --- |
| PlaceholderAPI | Dynamic text and the `%zaminshop_*%` expansion |
| Vault | Economy and permission bridge |
| LangUtils | Language provider |

## Not present in the current source

`GRINGOTTS` is not a current economy type. Do not copy it from older documentation.

## Restart requirement

Install, remove, or upgrade any integration with a full server restart. Reloading ZaminShop does not load a missing Bukkit plugin.
