---
description: Complete commented reference for every option shipped in ZaminShop's config.yml.
---

# config.yml Reference

`plugins/ZaminShop/config.yml` controls global services and defaults. Shop contents belong in shop-pack files, while menu layouts belong in `guis/`.

{% hint style="info" %}
Every block below uses the hierarchy and defaults shipped with ZaminShop. Copy a complete section into `config.yml`, keep its indentation intact, then run `/zaminshop validate`.
{% endhint %}

## Core settings

```yaml
# Internal configuration format version.
# Do not change this manually.
config-version: 2

# Language file loaded from plugins/ZaminShop/lang/.
language: "en_US"

# Enforce normal Minecraft item stack-size behavior.
enforceDefaultStackSize: true

# Hide the support message printed while shops load.
hideShopLoadingSupportMessage: false
```

## Database

```yaml
database:
  # Database backend. Supported values: sqlite or mysql.
  # Invalid values fall back to SQLite.
  type: sqlite

  # MySQL connection details. These are ignored when type is sqlite.
  mySQLHost: localhost
  mySQLPort: 3306
  mySQLDatabase: db
  mySQLUser: root
  mySQLPassword: ""

  # MySQL table names.
  tableNames:
    players: "players"

  # Optional JDBC parameters can be added as string key/value pairs.
  # mySQLParameters:
  #   useSSL: "false"
```

See [Database Setup](database.md) before changing the backend.

## Economies

```yaml
# Economy providers enabled for shops.
# The first entry is the default economy for every shop that does not
# declare its own economy.
#
# Supported values:
# CUSTOM, EXP, EXP_LEVELS, EXCELLENT_ECONOMY, COINS_ENGINE,
# GEMS_ECONOMY, ITEM, MYSQL_TOKENS, PLAYER_POINTS, TOKEN_ENCHANT,
# TOKEN_MANAGER, VAULT, and VOTING_PLUGIN.
economyTypes:
  - VAULT

# Optional display text added before or after formatted currency values.
currencies:
  prefixes:
    VAULT: "$"
  suffixes:
    PLAYER_POINTS: " points"
```

`economyType` is still read as a legacy single-value alternative when it contains a string. See [Economy Providers](../integrations/economies.md) for dependencies and provider behavior.

## Item currency

```yaml
# Built-in physical currency. Add ITEM to economyTypes to enable it.
# Only the 36 normal inventory slots are counted. Armor, off-hand,
# ender chests, container contents, and cursor items are excluded.
item-currency:
  # Name appended to formatted currency values.
  display-name: Coins

  # Decimal precision represented by the smallest denomination.
  # Valid range: 0 through 6.
  decimal-places: 0

  denominations:
    emerald:
      # Currency value of one matching item.
      value: 1
      # Item definition loaded by ZaminShop's normal item parser.
      item:
        material: EMERALD

    emerald-block:
      value: 9
      item:
        material: EMERALD_BLOCK
```

This section is validated when `ITEM` is enabled. See [Built-in Item Currency](../integrations/item-currency.md) for validation, matching, deposits, withdrawals, and change.

## Spawner provider

```yaml
# Preferred external spawner provider when more than one supported provider
# is installed. Leave empty to use the only detected provider or
# ZaminShop's built-in spawner support.
spawnerProvider: ""
```

## Startup logging

```yaml
startup-log:
  # Print the ZaminShop banner during startup.
  banner: true

  # Print detailed startup diagnostics.
  debug: false

  # Print a separate loading breakdown for each shop.
  show-shop-breakdown: false
```

## Notification throttling

```yaml
# Limit repeated routine notices without delaying purchase, sale,
# confirmation, rollback, or other important transaction messages.
notifications:
  throttling:
    # Enable routine-notice throttling.
    enabled: true

    # Default cooldown between repeated notices, in milliseconds.
    # Negative values are clamped to zero.
    default-cooldown-ms: 2500
```

## Inventory click shortcuts

```yaml
inventoryClickShortcuts:
  # Master switch for inventory click shortcuts.
  enabled: true

  # Enable shortcuts in each menu context.
  mainMenu: false
  shopMenu: true
  amountSelector: false
  bulkBuy: false
  bulkSell: false
```

## Transaction safety

```yaml
transaction-safety:
  # Master switch for guarded transaction handling.
  enabled: true

  # Prevent two transactions from running at the same time for one player.
  per-player-lock: true

  # Maximum time to wait for the player transaction lock, in milliseconds.
  lock-timeout-ms: 5000

  # Minimum delay between transaction clicks, in milliseconds.
  click-cooldown-ms: 150

  # Block the guarded transaction path while an inventory is open.
  block-while-inventory-open: false

  # Print additional transaction-safety failure diagnostics.
  debug-failures: false

  # Optional circuit breaker for overloaded servers. Recovery uses a higher
  # threshold to prevent transactions rapidly switching on and off.
  low-tps:
    enabled: false

    # Block transactions below this TPS value. Clamped to 1.0 through 20.0.
    minimum-tps: 17.0

    # Resume transactions at this TPS value. Clamped between minimum-tps
    # and 20.0.
    recovery-tps: 18.5

    # Weight used when smoothing TPS readings. Clamped to 0.05 through 1.0.
    smoothing-factor: 0.35
```

## Transaction audit

```yaml
transaction-audit:
  # Enable transaction audit output.
  enabled: false

  # Include successful transactions.
  log-success: false

  # Include failed transactions.
  log-failures: true

  # Include an inventory summary in audit records.
  include-inventory-summary: false
```

## Currency safety

```yaml
currency-safety:
  # Master switch for currency validation.
  enabled: true

  # Global accepted currency precision.
  decimal-places: 2

  # Reject prices with more decimal places than the configured precision.
  reject-prices-with-too-many-decimals: true

  # Smallest accepted non-zero transaction value.
  minimum-transaction-value: 0.01

  # Normalize player balances before affordability checks.
  normalize-player-balances-for-checks: true

  # Reject NaN and positive or negative infinity.
  block-nan-infinity: true

  # Largest accepted transaction value.
  max-transaction-value: 1000000000000
```

## Overwatcher

```yaml
overwatcher:
  # Run economy-risk analysis.
  enabled: true

  # Block shops classified as critical.
  block-critical-shops: true

  # Notify administrators about detected risks.
  notify-admins: true

  # Require confirmation for guarded operations.
  require-confirmation: true

  # Highest accepted sell-price to buy-price ratio.
  max-sell-buy-ratio: 0.8

  # Allow an item's sell price to exceed its buy price.
  allow-sell-higher-than-buy: false
```

The current section name is `overwatcher`, not `risk-guard`.

## Sell limits

```yaml
sell-limits:
  # Master switch for per-player sale limits.
  enabled: false

  # Reset timezone. "server" uses the server's timezone.
  reset-timezone: "server"

  daily:
    enabled: false
    # Maximum money a player can earn from sales each day.
    max-money: 50000
    # Maximum number of items a player can sell each day.
    max-items: 50000

  weekly:
    enabled: false
    # Maximum money a player can earn from sales each week.
    max-money: 500000
    # Maximum number of items a player can sell each week.
    max-items: 500000
```

See [Sell Limits](sell-limits.md) for counting and reset behavior.

## Suspicious transactions

```yaml
suspicious-transactions:
  # Enable suspicious transaction monitoring.
  enabled: false

  # Notify administrators when a threshold is exceeded.
  notify-admins: true

  # Write alerts to the console.
  log-console: true

  # Minimum delay between repeated alerts, in seconds.
  cooldown-between-alerts-seconds: 60

  thresholds:
    transactions-per-10-seconds: 20
    money-earned-per-minute: 1000000
    items-sold-per-minute: 50000
    same-item-sales-per-10-seconds: 15

  actions:
    # Send an administrator warning.
    warn-admins: true

    # Temporarily block the player's selling activity.
    temporarily-block-selling: false

    # Selling block duration, in seconds.
    block-duration-seconds: 30
```

## Search

```yaml
search:
  # Master switch for /shop search and search menus.
  enabled: true

  # EXACT  = exact normalized item names only
  # SIMPLE = exact, starts-with, contains, and full-term matching
  # FUZZY  = SIMPLE plus typo-tolerant token matching
  # SMART  = fuzzy matching with score-based ranking
  mode: SMART

  # Maximum displayed results. Runtime value is clamped to 1 through 45.
  max-results: 45

  # Treat unknown /shop arguments as search text.
  search-on-unknown-shop-command: false
```

When `mode` is blank, the legacy `search.fuzzy` value selects `FUZZY` or `SIMPLE`. See [Search](../gui/search.md).

## Recent transactions

```yaml
recent-menu:
  # Enable recent transaction history.
  enabled: true

  # Maximum stored/displayed records per player. Clamped to 1 through 54.
  max-records-per-player: 20

  # Record and display purchases.
  show-bought: true

  # Record and display sales.
  show-sold: true

  # Keep only the newest entry for the same shop item and transaction type.
  merge-duplicate-items: true
```

## Player defaults

```yaml
player-settings:
  defaults:
    # Ask for confirmation before purchases by default.
    confirm-purchases: false

    # Return to the shop after supported actions by default.
    return-to-shop: true
```

## Built-in GUI paths

```yaml
# Fixed GUI menu file locations.
# If you move a built-in menu file, update its file path here.
gui_menus:
  gui-settings:
    file: guis/gui-settings.yml
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
  confirm-purchase:
    file: guis/confirm-purchase.yml
  player-settings:
    file: guis/player-settings.yml
```

## Enchantments and amount selection

```yaml
# Maximum enchantments players can add to an item.
# Set to -1 for no limit.
maxEnchantments: 3

# Restrict purchases to an enchantment one level higher than the enchantment
# already on the item.
limitEnchantmentLevelDiff: false

# Enable the amount-selector double-click fix.
enableAmountSelectionFix: true

# true: sell-all may sell any quantity.
# false: sell-all uses multiples of the shop item's configured stack size.
allowAllSellAllStackSizes: false

# Allow ENCHANTMENT products to apply unsafe enchantments, such as
# Sharpness 25 on a stick.
disableUnsafeEnchantmentCheck: false

# Allow ENCHANTMENT products to replace a lower level of the same enchantment.
allowEnchantmentLevelIncrease: true
```

## General shop behavior

```yaml
# Price rounding mode: UP, DOWN, NEAREST, or NONE.
roundPrices: none

# Disable the shop directory opened by /zaminshop.
# Direct /zaminshop open <shop> access remains available.
disableMainMenu: false

# Use the dedicated free-item messages when a buy or sell price is zero.
useDifferentMessagesForFreeItems: true

# Capitalize generated item names, such as "nether brick" to "Nether Brick".
capitalizeItemNames: true

# Price modifier source: BOTH, COMMAND, or PERMISSION.
# With BOTH, permission modifiers have priority over command modifiers.
priceModifiersType: BOTH

# Close the GUI after Sell All completes.
closeGuiAfterSellAll: false

# Open bulk buy/sell immediately after clicking a shop item.
# The matching GUI must be enabled and the player needs its permission.
openBulkGuiImmediately: false

# Allow the dedicated bulk menus to open.
enableBulkBuyGUI: true
enableBulkSellGUI: true

# Allow amount selectors to open their extended buy and sell menus.
enableBuyMoreGUI: true
enableSellMoreGUI: true

# Give players access to every shop when the console opens a shop for them.
sudoAllowAllShopsAccess: false

# Block shops in these game modes.
disableShopsInGamemodes:
  - ADVENTURE
  - CREATIVE
  - SPECTATOR

# Block shops in these worlds.
disableShopsInWorlds: []

# Display price modifiers as percentages, such as 10%, instead of decimals.
# Commands still use decimal values.
displayPriceModifiersInPercents: true

# Skip the world-specific shop permission when a shop is opened for a player
# through /zaminshop open [player] [shop name].
disableSudoWorldPermissionCheck: false

# Skip the shop-specific permission for the same sudo-open path.
disableSudoShopPermissionCheck: false
```

## Default item comparison

```yaml
defaultItemSettings:
  # Compare item metadata, including name and lore, during sales.
  compareMeta: false

  # Remove item metadata from items purchased from shops.
  stripItemMeta: false

  # Compare custom model data during sales.
  compareModel: true

  # Compare item damage or durability during sales.
  compareDamage: false

  # Compare item NBT or components during sales.
  compareNbt: false

  # Compare anvil repair cost during sales.
  compareRepairCost: false
```

Individual shop items can override these defaults.

## Transaction logging

```yaml
log:
  # Log transactions to the console and main server log.
  toConsole: true

  # Log transactions to a separate file.
  toFile: false

  # SimpleDateFormat pattern used for transaction timestamps.
  formatDate: "yyyy/MM/dd HH:mm:ss"

  # Messages written for each transaction type.
  formatBuyCommand: "%player% bought %amount% x %command% command for %price% from %shop% shop"
  formatBuyEnchantment: "%player% bought %enchantment% enchantment for %price% from %shop% shop"
  formatBuyPermission: "%player% bought %permission% permission for %price% from %shop% shop"
  formatBuy: "%player% bought %amount% x %item% for %price% from %shop% shop"
  formatSell: "%player% sold %amount% x %item% for %price% to %shop% shop"
  formatSellAll: "%player% sold all %amount% x %item% for %price% to %shop% shop"
```

Use only the placeholders present in the shipped format for that transaction type.

## `/sell hand`

```yaml
sellHand:
  # Allow any quantity and calculate its value from the configured base price.
  allowAllQuantities: true

  # Make /sell hand behave like /sell handall.
  sellsAllItems: false

  # Exclude items with a sell price of zero.
  excludeFreeItems: true

  # Exclude armor slots.
  excludeArmorSlots: true

  # Exclude the off-hand slot.
  excludeOffHand: false
```

## `/sell all`

```yaml
sellAll:
  # Send a stack-by-stack price summary after selling.
  detailedSummary: false

  # Use the highest sell price found across all shops.
  # This can affect performance on servers with many shops and items.
  findMaxSellPrice: true

  # Exclude items with a sell price of zero.
  excludeFreeItems: true

  # Exclude armor slots.
  excludeArmorSlots: true

  # Exclude the off-hand slot.
  excludeOffHand: false
```

## Command registration

```yaml
# Prevent commands from registering when another plugin should own them.
# A full server restart is required after changing this section.
disableCommands:
  # Prevent /sell from registering.
  sell: false
```

## Number formatting

```yaml
numberFormat:
  # Character separating the whole and fractional portions of a number.
  decimalSeparator: "."

  # Character grouping digits in large numbers.
  groupingSeparator: ","

  # Minimum and maximum displayed integer digits.
  minimumIntegerDigits: 1
  maximumIntegerDigits: 32

  # Minimum and maximum displayed fractional digits.
  minimumFractionDigits: 0
  maximumFractionDigits: 8

  # Remove unnecessary trailing fractional digits, such as $100.00 to $100.
  hideFraction: true

  shortScale:
    # Convert large values to short-scale text, such as 1,000,000 to 1 million.
    enableShortScaleNumbering: false

    # Value at which short-scale formatting begins.
    shortScaleLimit: 1000000

    # Maximum decimal places in a short-scale value.
    shortHandDecimalLimit: 2

    # Maximum digits in a short-scale value.
    shortHandNumberLimit: 32
```

## Reloading

Most values are read again by:

```text
/zaminshop reload
```

Dependency installation, command registration, and provider changes require a restart. See the [Reload and Restart Matrix](reloading.md).
