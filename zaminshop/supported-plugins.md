# Supported Plugins

ZaminShop hooks into optional plugins when they are installed.

The plugin can start without these dependencies.

## Economy Plugins

| Plugin | Provider type | Notes |
| ------ | ------------- | ----- |
| Vault | `VAULT` | Uses the registered Vault economy provider. |
| ExcellentEconomy | `EXCELLENT_ECONOMY` | External economy provider. |
| CoinsEngine | `COINS_ENGINE` | External economy provider. |
| GemsEconomy | `GEMS_ECONOMY` | External economy provider. |
| MySQL-Tokens | `MYSQL_TOKENS` | External economy provider. |
| PlayerPoints | `PLAYER_POINTS` | External points provider. |
| TokenEnchant | `TOKEN_ENCHANT` | External token provider. |
| TokenManager | `TOKEN_MANAGER` | External token provider. |
| VotingPlugin | `VOTING_PLUGIN` | External points/provider hook. |
| Minecraft EXP | `EXP` | Built-in player exp points. |
| Minecraft EXP levels | `EXP_LEVELS` | Built-in player exp levels. |
| ZaminShop internal | `INTERNAL` | SQL-backed internal provider. |
| Item currency | `ITEM` | Uses configured item denominations. |

## Item Plugins

| Plugin | Format / key | Notes |
| ------ | ------------ | ----- |
| HeadDatabase | `material: hdb-<id>` or `headDatabase: "<id>"` | Loads heads from HeadDatabase. |
| Oraxen | `material: oraxen-<item-id>` or `oraxen: "<item-id>"` | Loads Oraxen items. |
| ItemsAdder | `material: itemsadder-<namespace>:<item>` | Loads ItemsAdder items. |
| MMOItems | `material: mmoitems-<type>:<id>` | Loads MMOItems items. |
| Nexo | `nexo: "<item-id>"` | Loads Nexo items. |
| MythicMobs | `mythicMobs: "<item>"` or `mythicMobs.item`, `mythicMobs.egg`, `mythicMobs.spawner` | Loads MythicMobs items, eggs, or spawners. |
| Slimefun | `slimefun: "<id>"` | Loads Slimefun items. |
| CraftEngine | `craftEngine: "<namespace>:<item-id>"` | Loads CraftEngine items. |
| CrackShot | `crackShot: "<weapon>"` | Loads CrackShot weapons. |
| QualityArmory | `qualityArmory: "<id>"` | Loads QualityArmory items. |
| WeaponMechanics | `weaponMechanics.weapon` or `weaponMechanics.ammo` | Loads weapons or ammo. |
| CustomItems | `customItems: "<id>"` | Loads CustomItems items. |
| Brewery / BreweryX | `brewery.recipe`, `brewery.quality` | Loads Brewery drink items. |
| ExecutableItems | `executableItems: "<id>"` | Loads ExecutableItems. |
| ExecutableBlocks | `executableBlocks: "<id>"` | Loads ExecutableBlocks. |

## Other Plugins

| Plugin | Used for | Notes |
| ------ | -------- | ----- |
| PlaceholderAPI | Placeholders in menus, text, and the ZaminShop expansion. | Optional. |
| ProtocolLib | Sign input backend. | Used when sign input support is available. |
| Vault permissions | Permission provider bridge. | Optional permission hook. |
| LangUtils | Language provider hook. | Optional. |
| MineableSpawners | External spawner support. | Optional. |
| SilkSpawners | External spawner support. | Optional. |
| SCore | Dependency used by some Ssomar plugins. | Listed as softdepend. |

## Bukkit Materials

Normal Bukkit material names work:

```yaml
stone:
  type: SHOP_ITEM
  material: STONE
  slot: 10
  buy-price: 16
  sell-price: 4
```

Legacy material support is handled by ZaminShop's material resolver where possible.
