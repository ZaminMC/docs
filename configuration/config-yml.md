---
description: Complete reference for every option shipped in ZaminShop's config.yml.
---

# config.yml Reference

`plugins/ZaminShop/config.yml` controls global services and defaults. Shop contents belong in shop-pack files, while menu layouts belong in `guis/`.

{% hint style="info" %}
Paths and defaults below match the distributed `config.yml`. Run `/zaminshop validate` after editing.
{% endhint %}

## Core

| Path | Default | Purpose |
| --- | --- | --- |
| `config-version` | `2` | Internal configuration format version. Do not change it manually. |
| `language` | `en_US` | Language file ID under `plugins/ZaminShop/lang/`. |
| `enforceDefaultStackSize` | `true` | Enforces normal item stack-size behavior. |
| `hideShopLoadingSupportMessage` | `false` | Hides the shop-loading support message. |

## Database

```yaml
database:
  type: sqlite
  mySQLHost: localhost
  mySQLPort: 3306
  mySQLDatabase: db
  mySQLUser: root
  mySQLPassword: ""
  tableNames:
    players: "players"
```

| Path | Default | Purpose |
| --- | --- | --- |
| `database.type` | `sqlite` | `sqlite` or `mysql`. Invalid values fall back to SQLite. |
| `database.mySQLHost` | `localhost` | MySQL host. |
| `database.mySQLPort` | `3306` | MySQL port. |
| `database.mySQLDatabase` | `db` | Database name. |
| `database.mySQLUser` | `root` | Login user. |
| `database.mySQLPassword` | empty | Login password. |
| `database.tableNames.players` | `players` | Player-data table name. |
| `database.mySQLParameters.<name>` | none | Optional JDBC parameters loaded as string key/value pairs. |

[Database setup](database.md)

## Economies

```yaml
economyTypes:
  - VAULT
```

The first enabled provider is the default. Valid types are `CUSTOM`, `EXP`, `EXP_LEVELS`, `EXCELLENT_ECONOMY`, `COINS_ENGINE`, `GEMS_ECONOMY`, `ITEM`, `MYSQL_TOKENS`, `PLAYER_POINTS`, `TOKEN_ENCHANT`, `TOKEN_MANAGER`, `VAULT`, and `VOTING_PLUGIN`.

`economyType` is still read as a legacy single-value alternative when it is a string.

Optional display overrides:

```yaml
currencies:
  prefixes:
    VAULT: "$"
  suffixes:
    PLAYER_POINTS: " points"
```

[Economy providers](../integrations/economies.md)

## Item currency

```yaml
item-currency:
  display-name: Coins
  decimal-places: 0
  denominations:
    emerald:
      value: 1
      item:
        material: EMERALD
    emerald-block:
      value: 9
      item:
        material: EMERALD_BLOCK
```

This section is validated when `ITEM` is used. See [Built-in item currency](../integrations/item-currency.md).

## Spawner provider

| Path | Default | Purpose |
| --- | --- | --- |
| `spawnerProvider` | empty | Preferred external provider when more than one supported spawner provider is installed. |

## Startup logging

| Path | Default | Purpose |
| --- | --- | --- |
| `startup-log.banner` | `true` | Prints the startup banner. |
| `startup-log.debug` | `false` | Enables detailed startup diagnostics. |
| `startup-log.show-shop-breakdown` | `false` | Logs per-shop loading details. |

## Notification throttling

| Path | Default | Purpose |
| --- | --- | --- |
| `notifications.throttling.enabled` | `true` | Limits repeated routine notices. |
| `notifications.throttling.default-cooldown-ms` | `2500` | Default repeat-notice cooldown in milliseconds; negative values are clamped to zero. |

Transaction results, confirmations, rollbacks, and other important transaction messages are not described by the default comments as routine throttled notices.

## Inventory click shortcuts

```yaml
inventoryClickShortcuts:
  enabled: true
  mainMenu: false
  shopMenu: true
  amountSelector: false
  bulkBuy: false
  bulkSell: false
```

The root toggle controls the feature globally. Each child enables it for one menu context.

## Transaction safety

| Path | Default | Purpose |
| --- | --- | --- |
| `transaction-safety.enabled` | `true` | Master transaction-safety switch. |
| `transaction-safety.per-player-lock` | `true` | Prevents overlapping transactions for one player. |
| `transaction-safety.lock-timeout-ms` | `5000` | Lock timeout. |
| `transaction-safety.click-cooldown-ms` | `150` | Transaction click cooldown. |
| `transaction-safety.block-while-inventory-open` | `false` | Blocks the guarded path while an inventory is open. |
| `transaction-safety.debug-failures` | `false` | Logs additional failure diagnostics. |
| `transaction-safety.low-tps.enabled` | `false` | Enables the low-TPS circuit breaker. |
| `transaction-safety.low-tps.minimum-tps` | `17.0` | Blocking threshold, clamped to `1.0`-`20.0`. |
| `transaction-safety.low-tps.recovery-tps` | `18.5` | Recovery threshold, clamped between the minimum and `20.0`. |
| `transaction-safety.low-tps.smoothing-factor` | `0.35` | TPS smoothing factor, clamped to `0.05`-`1.0`. |

## Transaction audit

| Path | Default | Purpose |
| --- | --- | --- |
| `transaction-audit.enabled` | `false` | Enables transaction audit output. |
| `transaction-audit.log-success` | `false` | Includes successful transactions. |
| `transaction-audit.log-failures` | `true` | Includes failed transactions. |
| `transaction-audit.include-inventory-summary` | `false` | Adds inventory summary data. |

## Currency safety

| Path | Default | Purpose |
| --- | --- | --- |
| `currency-safety.enabled` | `true` | Master currency validation switch. |
| `currency-safety.decimal-places` | `2` | Global currency precision. |
| `currency-safety.reject-prices-with-too-many-decimals` | `true` | Rejects prices exceeding configured precision. |
| `currency-safety.minimum-transaction-value` | `0.01` | Minimum non-zero transaction value. |
| `currency-safety.normalize-player-balances-for-checks` | `true` | Normalizes balance comparisons. |
| `currency-safety.block-nan-infinity` | `true` | Blocks non-finite numeric values. |
| `currency-safety.max-transaction-value` | `1000000000000` | Maximum transaction value. |

## Overwatcher

```yaml
overwatcher:
  enabled: true
  block-critical-shops: true
  notify-admins: true
  require-confirmation: true
  max-sell-buy-ratio: 0.8
  allow-sell-higher-than-buy: false
```

| Path | Purpose |
| --- | --- |
| `enabled` | Runs economy-risk analysis. |
| `block-critical-shops` | Blocks shops classified as critical. |
| `notify-admins` | Sends administrator warnings. |
| `require-confirmation` | Requires confirmation for guarded operations. |
| `max-sell-buy-ratio` | Maximum accepted sell-to-buy ratio. |
| `allow-sell-higher-than-buy` | Allows a sell price above its buy price when true. |

The current section name is `overwatcher`, not `risk-guard`.

## Sell limits

| Path | Default |
| --- | --- |
| `sell-limits.enabled` | `false` |
| `sell-limits.reset-timezone` | `server` |
| `sell-limits.daily.enabled` | `false` |
| `sell-limits.daily.max-money` | `50000` |
| `sell-limits.daily.max-items` | `50000` |
| `sell-limits.weekly.enabled` | `false` |
| `sell-limits.weekly.max-money` | `500000` |
| `sell-limits.weekly.max-items` | `500000` |

[Sell limits](sell-limits.md)

## Suspicious transactions

| Path | Default |
| --- | --- |
| `suspicious-transactions.enabled` | `false` |
| `suspicious-transactions.notify-admins` | `true` |
| `suspicious-transactions.log-console` | `true` |
| `suspicious-transactions.cooldown-between-alerts-seconds` | `60` |
| `thresholds.transactions-per-10-seconds` | `20` |
| `thresholds.money-earned-per-minute` | `1000000` |
| `thresholds.items-sold-per-minute` | `50000` |
| `thresholds.same-item-sales-per-10-seconds` | `15` |
| `actions.warn-admins` | `true` |
| `actions.temporarily-block-selling` | `false` |
| `actions.block-duration-seconds` | `30` |

Threshold and action paths in the table are children of `suspicious-transactions`.

## Search

| Path | Default | Notes |
| --- | --- | --- |
| `search.enabled` | `true` | Enables search. |
| `search.mode` | `SMART` | `EXACT`, `SIMPLE`, `FUZZY`, or `SMART`. |
| `search.max-results` | `45` | Runtime value is clamped to `1`-`45`. |
| `search.search-on-unknown-shop-command` | `false` | Searches when a shop command target is unknown. |

Legacy `search.fuzzy` is read when `search.mode` is blank.

## Recent transactions

| Path | Default | Notes |
| --- | --- | --- |
| `recent-menu.enabled` | `true` | Enables recent history. |
| `recent-menu.max-records-per-player` | `20` | Clamped to `1`-`54`. |
| `recent-menu.show-bought` | `true` | Records/displays purchases. |
| `recent-menu.show-sold` | `true` | Records/displays sales. |
| `recent-menu.merge-duplicate-items` | `true` | Keeps the newest matching item/action entry. |

## Player defaults

| Path | Default |
| --- | --- |
| `player-settings.defaults.confirm-purchases` | `false` |
| `player-settings.defaults.return-to-shop` | `true` |

## Built-in GUI paths

`gui_menus.<id>.file` points to each fixed menu:

| ID | Default file |
| --- | --- |
| `gui-settings` | `guis/gui-settings.yml` |
| `amount-selector` | `guis/amount-selector.yml` |
| `bulk-buy` | `guis/bulk-buy.yml` |
| `bulk-sell` | `guis/bulk-sell.yml` |
| `recent` | `guis/recent.yml` |
| `favorites` | `guis/favorites.yml` |
| `search` | `guis/search.yml` |
| `sell` | `guis/sell.yml` |
| `confirm-purchase` | `guis/confirm-purchase.yml` |
| `player-settings` | `guis/player-settings.yml` |

## Enchantments and amounts

| Path | Default | Purpose |
| --- | --- | --- |
| `maxEnchantments` | `3` | Maximum enchantments; `-1` means no limit. |
| `limitEnchantmentLevelDiff` | `false` | Restricts purchases to one level above the current enchantment. |
| `disableUnsafeEnchantmentCheck` | `false` | Allows unsafe enchant application when true. |
| `allowEnchantmentLevelIncrease` | `true` | Allows replacing a lower level of the same enchantment. |
| `enableAmountSelectionFix` | `true` | Enables the amount-selector double-click fix. |
| `allowAllSellAllStackSizes` | `false` | Allows sell-all to use arbitrary quantities instead of shop stack multiples. |

## General shop behavior

| Path | Default |
| --- | --- |
| `roundPrices` | `none` (`UP`, `DOWN`, `NEAREST`, or `NONE`) |
| `disableMainMenu` | `false` |
| `useDifferentMessagesForFreeItems` | `true` |
| `capitalizeItemNames` | `true` |
| `priceModifiersType` | `BOTH` (`BOTH`, `COMMAND`, or `PERMISSION`) |
| `closeGuiAfterSellAll` | `false` |
| `openBulkGuiImmediately` | `false` |
| `enableBulkBuyGUI` | `true` |
| `enableBulkSellGUI` | `true` |
| `enableBuyMoreGUI` | `true` |
| `enableSellMoreGUI` | `true` |
| `sudoAllowAllShopsAccess` | `false` |
| `displayPriceModifiersInPercents` | `true` |
| `disableSudoWorldPermissionCheck` | `false` |
| `disableSudoShopPermissionCheck` | `false` |

`disableShopsInGamemodes` defaults to `ADVENTURE`, `CREATIVE`, and `SPECTATOR`. `disableShopsInWorlds` defaults to an empty list.

## Default item comparison

| Path | Default |
| --- | --- |
| `defaultItemSettings.compareMeta` | `false` |
| `defaultItemSettings.stripItemMeta` | `false` |
| `defaultItemSettings.compareModel` | `true` |
| `defaultItemSettings.compareDamage` | `false` |
| `defaultItemSettings.compareNbt` | `false` |
| `defaultItemSettings.compareRepairCost` | `false` |

Individual shop items can override these defaults.

## Transaction logging

| Path | Default |
| --- | --- |
| `log.toConsole` | `true` |
| `log.toFile` | `false` |
| `log.formatDate` | `yyyy/MM/dd HH:mm:ss` |
| `log.formatBuyCommand` | Shipped command-purchase format |
| `log.formatBuyEnchantment` | Shipped enchantment-purchase format |
| `log.formatBuyPermission` | Shipped permission-purchase format |
| `log.formatBuy` | Shipped item-purchase format |
| `log.formatSell` | Shipped item-sale format |
| `log.formatSellAll` | Shipped sell-all format |

Format placeholders include the fields present in each shipped string, such as `%player%`, `%amount%`, `%item%`, `%price%`, `%shop%`, `%command%`, `%enchantment%`, and `%permission%`.

## `/sell hand`

| Path | Default |
| --- | --- |
| `sellHand.allowAllQuantities` | `true` |
| `sellHand.sellsAllItems` | `false` |
| `sellHand.excludeFreeItems` | `true` |
| `sellHand.excludeArmorSlots` | `true` |
| `sellHand.excludeOffHand` | `false` |

## `/sell all`

| Path | Default |
| --- | --- |
| `sellAll.detailedSummary` | `false` |
| `sellAll.findMaxSellPrice` | `true` |
| `sellAll.excludeFreeItems` | `true` |
| `sellAll.excludeArmorSlots` | `true` |
| `sellAll.excludeOffHand` | `false` |

## Command registration

```yaml
disableCommands:
  sell: false
```

Setting `disableCommands.sell: true` prevents `/sell` from registering. This requires a full server restart.

## Number format

| Path | Default |
| --- | --- |
| `numberFormat.decimalSeparator` | `.` |
| `numberFormat.groupingSeparator` | `,` |
| `numberFormat.minimumIntegerDigits` | `1` |
| `numberFormat.maximumIntegerDigits` | `32` |
| `numberFormat.minimumFractionDigits` | `0` |
| `numberFormat.maximumFractionDigits` | `8` |
| `numberFormat.hideFraction` | `true` |
| `numberFormat.shortScale.enableShortScaleNumbering` | `false` |
| `numberFormat.shortScale.shortScaleLimit` | `1000000` |
| `numberFormat.shortScale.shortHandDecimalLimit` | `2` |
| `numberFormat.shortScale.shortHandNumberLimit` | `32` |

## Reloading

Most values are read again by `/zaminshop reload`. Dependency installation, command registration, and provider changes need a restart.

[Reload and restart matrix](reloading.md)
