# config.yml Reference

This page follows the actual default `config.yml` from the source.

## `language`

Default: `en_US`

## `database`

```yaml
database:
  type: sqlite
  mySQLHost: localhost
  mySQLPort: 3306
  mySQLDatabase: db
  mySQLUser: root
  mySQLPassword: ''
  tableNames:
    players: players
```

## `economyTypes`

```yaml
economyTypes:
- VAULT
```

## `startup-log`

```yaml
startup-log:
  banner: true
  debug: false
  show-shop-breakdown: false
```

## `inventoryClickShortcuts`

```yaml
inventoryClickShortcuts:
  enabled: true
  mainMenu: false
  shopMenu: true
  amountSelector: false
  bulkBuy: false
  bulkSell: false
```

## `transaction-safety`

```yaml
transaction-safety:
  enabled: true
  per-player-lock: true
  lock-timeout-ms: 5000
  click-cooldown-ms: 150
  block-while-inventory-open: false
  debug-failures: false
```

## `transaction-audit`

```yaml
transaction-audit:
  enabled: false
  log-success: false
  log-failures: true
  include-inventory-summary: false
```

## `currency-safety`

```yaml
currency-safety:
  enabled: true
  decimal-places: 2
  reject-prices-with-too-many-decimals: true
  minimum-transaction-value: 0.01
  normalize-player-balances-for-checks: true
  block-nan-infinity: true
  max-transaction-value: 1000000000000
```

## `risk-guard`

```yaml
risk-guard:
  enabled: true
  block-critical-shops: true
  notify-admins: true
  require-confirmation: true
  max-sell-buy-ratio: 0.8
  allow-sell-higher-than-buy: false
```

## `sell-limits`

```yaml
sell-limits:
  enabled: false
  reset-timezone: server
  daily:
    enabled: false
    max-money: 50000
    max-items: 50000
  weekly:
    enabled: false
    max-money: 500000
    max-items: 500000
```

## `suspicious-transactions`

```yaml
suspicious-transactions:
  enabled: false
  notify-admins: true
  log-console: true
  cooldown-between-alerts-seconds: 60
  thresholds:
    transactions-per-10-seconds: 20
    money-earned-per-minute: 1000000
    items-sold-per-minute: 50000
    same-item-sales-per-10-seconds: 15
  actions:
    warn-admins: true
    temporarily-block-selling: false
    block-duration-seconds: 30
```

## `search`

```yaml
search:
  enabled: true
  fuzzy: true
  max-results: 45
  search-on-unknown-shop-command: false
```

## `recent-menu`

```yaml
recent-menu:
  enabled: true
  max-records-per-player: 20
  show-bought: true
  show-sold: true
```

## `gui_menus`

```yaml
gui_menus:
  gui-settings:
    file: guis/gui-settings.yml
  shop-directory:
    file: guis/shop-directory.yml
  amount-selector:
    file: guis/amount-selector.yml
  bulk-buy:
    file: guis/bulk-buy.yml
  bulk-sell:
    file: guis/bulk-sell.yml
  recent:
    file: guis/recent.yml
  favorites:
    file: guis/favorites.yml
  search:
    file: guis/search.yml
  sell:
    file: guis/sell.yml
```

## `maxEnchantments`

Default: `3`

## `limitEnchantmentLevelDiff`

Default: `False`

## `enableAmountSelectionFix`

Default: `True`

## `allowAllSellAllStackSizes`

Default: `False`

## `roundPrices`

Default: `none`

## `disableMainMenu`

Default: `False`

## `useDifferentMessagesForFreeItems`

Default: `True`

## `capitalizeItemNames`

Default: `True`

## `priceModifiersType`

Default: `BOTH`

## `closeGuiAfterSellAll`

Default: `False`

## `openBulkGuiImmediately`

Default: `False`

## `sudoAllowAllShopsAccess`

Default: `False`

## `disableShopsInGamemodes`

```yaml
disableShopsInGamemodes:
- ADVENTURE
- CREATIVE
- SPECTATOR
```

## `disableShopsInWorlds`

```yaml
disableShopsInWorlds: []
```

## `displayPriceModifiersInPercents`

Default: `True`

## `disableSudoWorldPermissionCheck`

Default: `False`

## `disableSudoShopPermissionCheck`

Default: `False`

## `disableUnsafeEnchantmentCheck`

Default: `False`

## `allowEnchantmentLevelIncrease`

Default: `True`

## `defaultItemSettings`

```yaml
defaultItemSettings:
  compareMeta: false
  stripItemMeta: false
  compareModel: true
  compareDamage: false
  compareNbt: false
  compareRepairCost: false
```

## `log`

```yaml
log:
  toConsole: true
  toFile: false
  formatDate: yyyy/MM/dd HH:mm:ss
  formatBuyCommand: '%player% bought %amount% x %command% command for %price% from
    %shop% shop'
  formatBuyEnchantment: '%player% bought %enchantment% enchantment for %price% from
    %shop% shop'
  formatBuyPermission: '%player% bought %permission% permission for %price% from %shop%
    shop'
  formatBuy: '%player% bought %amount% x %item% for %price% from %shop% shop'
  formatSell: '%player% sold %amount% x %item% for %price% to %shop% shop'
  formatSellAll: '%player% sold all %amount% x %item% for %price% to %shop% shop'
```

## `sellHand`

```yaml
sellHand:
  allowAllQuantities: true
  sellsAllItems: false
  excludeFreeItems: true
  excludeArmorSlots: true
  excludeOffHand: false
```

## `sellAll`

```yaml
sellAll:
  detailedSummary: false
  findMaxSellPrice: true
  excludeFreeItems: true
  excludeArmorSlots: true
  excludeOffHand: false
```

## `disableCommands`

```yaml
disableCommands:
  sell: false
```

## `numberFormat`

```yaml
numberFormat:
  decimalSeparator: .
  groupingSeparator: ','
  minimumIntegerDigits: 1
  maximumIntegerDigits: 32
  minimumFractionDigits: 0
  maximumFractionDigits: 8
  hideFraction: true
  shortScale:
    enableShortScaleNumbering: false
    shortScaleLimit: 1000000
    shortHandDecimalLimit: 2
    shortHandNumberLimit: 32
```


## Notes

- `economyTypes` is ordered. The first entry becomes the default economy for shops unless a shop overrides it.
- `gui_menus` points built-in menu IDs to files. Move menu files only if you also update this section.
- `transaction-safety` should usually stay enabled.
- `risk-guard` should stay enabled on public servers.
- `disableCommands.sell` needs a full server restart.
