# config.yml

Core plugin configuration.

## `config-version`
```yaml
config-version: 2
```
Controls this part of the plugin.

## `language`
```yaml
language: en_US
```
Controls this part of the plugin.

## `database`
```yaml
database: {'type': 'sqlite', 'mySQLHost': 'localhost', 'mySQLPort': 3306, 'mySQLDatabase': 'db', 'mySQLUser': 'root', 'mySQLPassword': '', 'tableNames': {'players': 'players'}}
```
Controls this part of the plugin.

## `economyTypes`
```yaml
economyTypes: ['VAULT']
```
Controls this part of the plugin.

## `startup-log`
```yaml
startup-log: {'banner': True, 'debug': False, 'show-shop-breakdown': False}
```
Controls this part of the plugin.

## `inventoryClickShortcuts`
```yaml
inventoryClickShortcuts: {'enabled': True, 'mainMenu': False, 'shopMenu': True, 'amountSelector': False, 'bulkBuy': False, 'bulkSell': False}
```
Controls this part of the plugin.

## `transaction-safety`
```yaml
transaction-safety: {'enabled': True, 'per-player-lock': True, 'lock-timeout-ms': 5000, 'click-cooldown-ms': 150, 'block-while-inventory-open': False, 'debug-failures': False}
```
Controls this part of the plugin.

## `transaction-audit`
```yaml
transaction-audit: {'enabled': False, 'log-success': False, 'log-failures': True, 'include-inventory-summary': False}
```
Controls this part of the plugin.

## `currency-safety`
```yaml
currency-safety: {'enabled': True, 'decimal-places': 2, 'reject-prices-with-too-many-decimals': True, 'minimum-transaction-value': 0.01, 'normalize-player-balances-for-checks': True, 'block-nan-infinity': True, 'max-transaction-value': 1000000000000}
```
Controls this part of the plugin.

## `risk-guard`
```yaml
risk-guard: {'enabled': True, 'block-critical-shops': True, 'notify-admins': True, 'require-confirmation': True, 'max-sell-buy-ratio': 0.8, 'allow-sell-higher-than-buy': False}
```
Controls this part of the plugin.

## `sell-limits`
```yaml
sell-limits: {'enabled': False, 'reset-timezone': 'server', 'daily': {'enabled': False, 'max-money': 50000, 'max-items': 50000}, 'weekly': {'enabled': False, 'max-money': 500000, 'max-items': 500000}}
```
Controls this part of the plugin.

## `suspicious-transactions`
```yaml
suspicious-transactions: {'enabled': False, 'notify-admins': True, 'log-console': True, 'cooldown-between-alerts-seconds': 60, 'thresholds': {'transactions-per-10-seconds': 20, 'money-earned-per-minute': 1000000, 'items-sold-per-minute': 50000, 'same-item-sales-per-10-seconds': 15}, 'actions': {'warn-admins': True, 'temporarily-block-selling': False, 'block-duration-seconds': 30}}
```
Controls this part of the plugin.

## `search`
```yaml
search: {'enabled': True, 'fuzzy': True, 'max-results': 45, 'search-on-unknown-shop-command': False}
```
Controls this part of the plugin.

## `recent-menu`
```yaml
recent-menu: {'enabled': True, 'max-records-per-player': 20, 'show-bought': True, 'show-sold': True}
```
Controls this part of the plugin.

## `gui_menus`
```yaml
gui_menus: {'gui-settings': {'file': 'guis/gui-settings.yml'}, 'shop-directory': {'file': 'guis/shop-directory.yml'}, 'amount-selector': {'file': 'guis/amount-selector.yml'}, 'bulk-buy': {'file': 'guis/bulk-buy.yml'}, 'bulk-sell': {'file': 'guis/bulk-sell.yml'}, 'recent': {'file': 'guis/recent.yml'}, 'favorites': {'file': 'guis/favorites.yml'}, 'search': {'file': 'guis/search.yml'}, 'sell': {'file': 'guis/sell.yml'}}
```
Controls this part of the plugin.

## `maxEnchantments`
```yaml
maxEnchantments: 3
```
Controls this part of the plugin.

## `limitEnchantmentLevelDiff`
```yaml
limitEnchantmentLevelDiff: False
```
Controls this part of the plugin.

## `enableAmountSelectionFix`
```yaml
enableAmountSelectionFix: True
```
Controls this part of the plugin.

## `allowAllSellAllStackSizes`
```yaml
allowAllSellAllStackSizes: False
```
Controls this part of the plugin.

## `roundPrices`
```yaml
roundPrices: none
```
Controls this part of the plugin.

## `disableMainMenu`
```yaml
disableMainMenu: False
```
Controls this part of the plugin.

## `useDifferentMessagesForFreeItems`
```yaml
useDifferentMessagesForFreeItems: True
```
Controls this part of the plugin.

## `capitalizeItemNames`
```yaml
capitalizeItemNames: True
```
Controls this part of the plugin.

## `priceModifiersType`
```yaml
priceModifiersType: BOTH
```
Controls this part of the plugin.

## `closeGuiAfterSellAll`
```yaml
closeGuiAfterSellAll: False
```
Controls this part of the plugin.

## `openBulkGuiImmediately`
```yaml
openBulkGuiImmediately: False
```
Controls this part of the plugin.

## `sudoAllowAllShopsAccess`
```yaml
sudoAllowAllShopsAccess: False
```
Controls this part of the plugin.

## `disableShopsInGamemodes`
```yaml
disableShopsInGamemodes: ['ADVENTURE', 'CREATIVE', 'SPECTATOR']
```
Controls this part of the plugin.

## `disableShopsInWorlds`
```yaml
disableShopsInWorlds: []
```
Controls this part of the plugin.

## `displayPriceModifiersInPercents`
```yaml
displayPriceModifiersInPercents: True
```
Controls this part of the plugin.

## `disableSudoWorldPermissionCheck`
```yaml
disableSudoWorldPermissionCheck: False
```
Controls this part of the plugin.

## `disableSudoShopPermissionCheck`
```yaml
disableSudoShopPermissionCheck: False
```
Controls this part of the plugin.

## `disableUnsafeEnchantmentCheck`
```yaml
disableUnsafeEnchantmentCheck: False
```
Controls this part of the plugin.

## `allowEnchantmentLevelIncrease`
```yaml
allowEnchantmentLevelIncrease: True
```
Controls this part of the plugin.

## `defaultItemSettings`
```yaml
defaultItemSettings: {'compareMeta': False, 'stripItemMeta': False, 'compareModel': True, 'compareDamage': False, 'compareNbt': False, 'compareRepairCost': False}
```
Controls this part of the plugin.

## `log`
```yaml
log: {'toConsole': True, 'toFile': False, 'formatDate': 'yyyy/MM/dd HH:mm:ss', 'formatBuyCommand': '%player% bought %amount% x %command% command for %price% from %shop% shop', 'formatBuyEnchantment': '%player% bought %enchantment% enchantment for %price% from %shop% shop', 'formatBuyPermission': '%player% bought %permission% permission for %price% from %shop% shop', 'formatBuy': '%player% bought %amount% x %item% for %price% from %shop% shop', 'formatSell': '%player% sold %amount% x %item% for %price% to %shop% shop', 'formatSellAll': '%player% sold all %amount% x %item% for %price% to %shop% shop'}
```
Controls this part of the plugin.

## `sellHand`
```yaml
sellHand: {'allowAllQuantities': True, 'sellsAllItems': False, 'excludeFreeItems': True, 'excludeArmorSlots': True, 'excludeOffHand': False}
```
Controls this part of the plugin.

## `sellAll`
```yaml
sellAll: {'detailedSummary': False, 'findMaxSellPrice': True, 'excludeFreeItems': True, 'excludeArmorSlots': True, 'excludeOffHand': False}
```
Controls this part of the plugin.

## `disableCommands`
```yaml
disableCommands: {'sell': False}
```
Controls this part of the plugin.

## `numberFormat`
```yaml
numberFormat: {'decimalSeparator': '.', 'groupingSeparator': ',', 'minimumIntegerDigits': 1, 'maximumIntegerDigits': 32, 'minimumFractionDigits': 0, 'maximumFractionDigits': 8, 'hideFraction': True, 'shortScale': {'enableShortScaleNumbering': False, 'shortScaleLimit': 1000000, 'shortHandDecimalLimit': 2, 'shortHandNumberLimit': 32}}
```
Controls this part of the plugin.
