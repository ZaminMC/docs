# Source Coverage Map

This page records the class-by-class source audit used to build this
documentation. It is an implementation map for contributors, not a supported
API guarantee. Server owners should follow the linked configuration and feature
pages instead of calling internal classes.

The audit covers Java sources, bundled YAML resources, command declarations,
permission checks, menu builders, item parsers, hooks, and persistence loaders
present in ZaminShop `1.20.0`.

## Bootstrap and lifecycle

| Class | Documented responsibility |
| --- | --- |
| `ZaminShopPlugin` | Bukkit entry point, command registration, listeners, startup, disable, and public API installation |
| `ZaminShopRuntime` | Runtime service graph, hooks, data managers, menus, currency, Overwatcher, Runtime Shield, and reload ownership |
| `LoadShopsTask` | Deferred shop-pack loading after startup |
| `LifecycleAuditReporter` | Automatic startup and reload summaries for configuration, shops, currencies, and Overwatcher |
| `ZaminShopMetrics` | Metrics startup |
| `PlayerListener` and `PlayerConnectionHandler` | Player data loading, join/quit cleanup, and block-link interaction routing |
| `InventoryClickHandler`, `InventoryDragHandler`, and `InventoryCloseHandler` | Inventory ownership, click dispatch, drag protection, and session cleanup |
| `AmountMenuClickHandler` | Amount-selector click handling |
| `ConfiguredMenuActionHandler` | Configured GUI action execution |
| `GuiOwnedItemEventHandler` | Prevents plugin-owned GUI items from escaping into normal inventories |
| `GuiTransactionFailureFeedback` | Menu-specific transaction error feedback |

Related documentation: [Installation and First Start](../setup.md),
[Automatic Validation](../validation.md), and
[Reloading](../configuration/reloading.md).

## Commands

| Class | Documented responsibility |
| --- | --- |
| `ZaminShopCommand` | `/zaminshop`, `/shop`, `/zshop`, and `/zhop` root dispatch |
| `ZaminShopTabCompleterService` | Root and subcommand suggestions |
| `SellItemsCommand` | `/sell` root dispatch |
| `DynamicShopCommand` and `DynamicShopCommandRegistrar` | Commands declared by shop packs and categories |
| `HelpSubcommand` | Help output |
| `ReloadSubcommand` | Runtime reload |
| `LanguageSubcommand` | Per-player language selection |
| `SearchSubcommand` | Search menu opening |
| `FavoritesSubcommand` | Favorites menu opening |
| `RecentTransactionsSubcommand` | Recent-transactions menu opening |
| `SellGuiSubcommand` | Sell GUI opening |
| `WorthSubcommand` | Held-item and inventory worth checks |
| `CheckShopSubcommand` | Shop lookup and diagnostic command |
| `BlockLinkSubcommand` | Physical block-link add, remove, list, clear, and cancel flows |
| `OverwatcherSubcommand` | Finding list, confirmation, and confirmation reset |
| `AddPriceModifierSubcommand`, `CheckPriceModifiersSubcommand`, and `ResetPriceModifierSubcommand` | Command-managed price modifiers |
| `SellSubcommand`, `SellAllSubcommand`, `SellHandSubcommand`, and `SellHandAllSubcommand` | Supported `/sell` workflows |

The exact syntax, sender restrictions, permissions, and examples are in
[Commands](../commands.md). Permission declarations and runtime checks are in
[Permissions](../permissions.md).

## Configuration loading and validation

| Class or group | Documented responsibility |
| --- | --- |
| `Settings`, `ConfigSnapshot`, and `ConfigurationKeys` | Main configuration parsing and immutable runtime values |
| `Lang` and `TransactionFailureFeedbackSettings` | Language keys and transaction failure presentation |
| `YamlLoadAssistant` | YAML loading diagnostics |
| `MenuSettings` and `MenuWithItemSettings` | Shared GUI file loading |
| `MenuSettingsValidator`, `MenuSchemaValidator`, and `MenuRootValidator` | GUI structure validation |
| `MenuItemValidator`, `MaterialDirectiveValidator`, and `PaginationValidator` | Item, directive, and page-layout validation |
| `CommandMappingValidator` | Configured command-map validation |
| `CanonicalConfig`, `CanonicalMenuConfig`, `CanonicalGuiItem`, `CanonicalItemSpec`, `CanonicalActionSpec`, `CanonicalRequirementSpec`, and `CanonicalSoundSpec` | Normalized configuration representation |
| `ConfigCompatibilityValidator`, `ConfigCompatibilityReport`, and `CompatibilityWarning` | Version and compatibility diagnostics |

The shipped values are reproduced as commented YAML in
[config.yml](../configuration/config-yml.md),
[currency.yml](../configuration/currency-yml.md),
[overwatcher.yml](../configuration/overwatcher-yml.md), and
[GUI Settings](../gui/gui-settings.md).

## Shop packs and item loading

| Class or group | Documented responsibility |
| --- | --- |
| `ShopFileManager` | Shop directory discovery and pack file ownership |
| `ShopDefinitionLoader` and `ShopPackDefinition` | `main.yml` pack definition loading |
| `ShopItemLoader` and `ShopConfigItemStackReader` | Category item and Bukkit item-stack construction |
| `ShopConfigSource`, `ShopLoadDiagnostic`, `ShopLoadReport`, `ShopLoadSeverity`, and `ShopLoadStats` | Source locations and load diagnostics |
| `Shop`, `ShopManager`, and `ShopDirectoryEntry` | Loaded shop model and lookup |
| `ShopItem`, `ShopItemType`, `ShopItemPermission`, and `ShopLink` | Item behavior, product type, permission product, and shop navigation target |
| `ShopPriceService` | Buy/sell price resolution and modifiers |
| `ShopPermissionService` | Shop and item access rules |
| `ShopSearchService` and `ShopItemLookupService` | Search and direct item lookup |
| `ShopOpenService`, `ShopNavigationService`, `ShopMenuOpenActionService`, and `ShopCloseService` | Menu opening, navigation, configured open actions, and close behavior |
| `ShopReloadService` | Shop state replacement during reload |
| `ShopTransactionActionService`, `ShopTransactionResult`, `SellAllResult`, and `SellAllResults` | Menu-to-transaction bridging and sell-all summaries |

Related documentation: [Shop Packs](../shops/README.md),
[Shop Pack File Format](../shops/shop-file-format.md),
[Shop Item Types](../shops/item-types.md), and
[Item Construction](../shops/item-options.md).

## Menu engine

| Class or group | Documented responsibility |
| --- | --- |
| `ZMenuLoader`, `ZMenuRegistry`, and `ZMenuDefinition` | GUI YAML loading and registered menu definitions |
| `ZMenuItemDefinition`, `ConfiguredItemNormalizer`, `ConfiguredItemCompiler`, and `ConfiguredItemRenderer` | Configured menu-item normalization, compilation, and rendering |
| `ConfiguredStaticMenu`, `ConfiguredListMenu`, and `ConfiguredShopMenuRenderer` | Static, list, and shop menu rendering |
| `MenuSession`, `PagedMenuSession`, `ShopMenuSession`, `CustomMenuSession`, `FavoritesSession`, `RecentTransactionsSession`, `SearchResultsSession`, and `ShopDirectorySession` | Player-specific menu state |
| `AmountSelectorMenu`, `BulkAmountSelectorMenu`, and `CurrencySelectionMenu` | Transaction amount, bulk amount, and provider selection flows |
| `MenuPaginationService`, `PaginationLayout`, `MenuPageState`, and `PageVisibility` | Page selection and page-specific layouts |
| `ZMenuActionParser`, `ConfiguredMenuActionResolver`, `ZAction`, and `ZActionType` | Action parsing and execution model |
| `ZMenuRequirementEvaluator`, `ZRequirement`, `ZRequirementRule`, and `ZRequirementResult` | Requirement checks and denial results |
| `MenuPlaceholderContextBuilder` and `MenuJavascriptExpressionEvaluator` | Menu placeholder context and JavaScript expressions |
| `MenuAccessPresentationService`, `MenuSlotBindingService`, and `ConfiguredStatefulMenuItemRenderer` | Access-aware display, slot binding, and stateful item presentation |
| `GuiOwnedItemService` and `MenuDiagnostics` | GUI item ownership and runtime menu diagnostics |
| `GuiButton`, `GuiElement`, `GuiSpecialElement`, and their value/type classes | Legacy GUI element representation |

Inventory-holder classes identify each open ZaminShop inventory and carry its
session. Their behavior is documented through the menu that owns them rather
than as separate user options.

Related documentation: [Menus](../gui/README.md),
[Menu File Format](../gui/menu-file-format.md),
[Actions](../gui/actions.md), [Requirements](../gui/requirements.md), and
[Full GUI Settings](../gui/gui-settings.md).

## Currency and economy

| Class or group | Documented responsibility |
| --- | --- |
| `CurrencyService` | `currency.yml` provider registry and provider metadata |
| `CurrencyResolutionService` and `ProviderPrice` | Item, pack, legacy category, and default-provider price resolution |
| `CurrencySelectionService` | Available-provider selection and remembered player choice |
| `CurrencySelectionMenu` | Provider selection GUI |
| `EconomyManager`, `EconomyProvider`, `EconomyType`, and `EconomyTransactionResult` | Provider lifecycle and balance transactions |
| `ItemCurrencyDefinition` and `ItemCurrencyEconomyProvider` | Denomination-backed inventory currency |
| `EconomyVaultProvider` | Vault economy bridge |
| `EconomyPlayerPointsProvider` | PlayerPoints bridge |
| `EconomyCoinsEngineProvider`, `EconomyExcellentEconomyProvider`, `EconomyGemsEconomyProvider`, `EconomyMySqlTokensProvider`, `EconomyTokenEnchantProvider`, `EconomyTokenManagerProvider`, and `EconomyVotingPluginProvider` | Legacy economy bridges still present in source |
| `EconomyExpProvider` and `EconomyExpLevelProvider` | Player experience-point and level providers |

The active multi-currency configuration model is documented in
[Economy Providers](../integrations/economies.md),
[Item Currency](../integrations/item-currency.md), and
[Multi-Currency Shops](../shops/multi-currency.md).

## Transactions and safeguards

| Class or group | Documented responsibility |
| --- | --- |
| `ShopTransactionService`, `TransactionContext`, and `TransactionState` | Buy/sell state machine and mutation boundary |
| `TransactionLockService` | Per-player duplicate transaction protection |
| `ServerLoadMonitor` | Load-aware transaction safeguards |
| `TransactionAuditLogger` | Transaction audit output |
| `SellLimitService`, `SellLimitStorage`, and `SellLimitCheckResult` | Daily and weekly sale limits |
| `SuspiciousTransactionService` and `SuspiciousCheckResult` | Suspicious sale-pattern checks |
| `NotificationService`, `NotificationLimiter`, and `NotificationKey` | Rate-limited staff and console notices |
| `ItemComparisonService`, `ItemMetadataService`, and `ItemNbtService` | Sale matching, metadata handling, and NBT access |

Related documentation: [Buying and Selling](../shops/buying-selling.md),
[Transaction Safety](../configuration/safety.md), and
[Sell Limits](../configuration/sell-limits.md).

## Overwatcher and Runtime Shield

| Class or group | Documented responsibility |
| --- | --- |
| `OverwatcherService`, `OverwatcherFinding`, and `OverwatcherLevel` | Static finding generation, severity, blocking, and confirmation |
| `DirectSellArbitrageAnalyzer` | Cross-shop direct buy/sell arbitrage |
| `CraftingArbitrageAnalyzer` and `CraftingConversionRule` | Crafting and compaction conversion loops |
| `RuntimeShieldService` and `RuntimeShieldConfig` | Runtime resale decision and configuration |
| `RuntimeShieldLockService` | Temporary listing locks after an exploit attempt |
| `PurchaseFingerprintService` and `PurchaseFingerprint` | Purchased-item signature creation and verification |
| `PurchaseFingerprintStorageFactory` | Selects the compatible signature backend |
| `PersistentDataFingerprintStorage`, `NbtPurchaseFingerprintStorage`, and `LegacyNbtFingerprintStorage` | Modern PDC, NBT, and legacy signature storage |

Configuration and operational behavior are in
[overwatcher.yml](../configuration/overwatcher-yml.md) and
[Transaction Safety and Overwatcher](../configuration/safety.md).

## Player data features

| Class or group | Documented responsibility |
| --- | --- |
| `DataManager`, `SqliteDataManager`, and `MySqlDataManager` | Persistent player data backends |
| `PlayerManager`, `PlayerData`, `PlayerPreferences`, and `PlayerIdentityService` | Loaded player state, preferences, and identity |
| `FavoriteService`, `FavoriteStorage`, `FavoriteEntry`, and `FavoriteShopService` | Favorite item persistence and shop-facing behavior |
| `RecentTransactionService`, `RecentTransactionStorage`, `RecentTransactionEntry`, `RecentTransactionAction`, and `RecentPurchaseService` | Recent history and purchase recording |
| `PermissionPriceModifierManager`, `CommandPriceModifierManager`, and the modifier model classes | Permission and command price adjustments |
| `PermissionManager` and `PermissionProviderBridge` | Permission checks and Vault permission bridge |
| `LanguageManager`, `Language`, `LanguageProvider`, and `LanguageLanguageUtilsProvider` | Player language and LangUtils integration |
| `SoundManager` and `SoundAction` | Configured sound playback |

Related documentation: [Favorites and Recent Transactions](../gui/favorites-recent.md),
[Price Modifiers](../configuration/price-modifiers.md),
[Database Setup](../configuration/database.md), and
[Language](../configuration/language.md).

## Physical block links

| Class | Documented responsibility |
| --- | --- |
| `BlockLinkService` | Link sessions, persistence, interaction handling, access checks, and block-break protection |
| `BlockPosition` | World and block-coordinate persistence key |
| `BlockLinkSubcommand` | Administrative link workflow |

See [Physical Shop Block Links](../configuration/block-links.md).

## Item providers and parsers

`ItemManager` registers the available item providers. Each provider class owns
the exact plugin-specific item lookup described in
[Custom Item Providers](../integrations/custom-items.md):

```text
BreweryItemProvider
CrackShotItemProvider
CraftEngineItemProvider
CustomItemsItemProvider
ExecutableBlocksItemProvider
ExecutableItemsItemProvider
HeadDatabaseItemProvider
ItemsAdderItemProvider
MMOItemsItemProvider
MythicMobsItemsItemProvider
NexoItemProvider
OraxenItemProvider
QualityArmoryItemProvider
SlimefunItemProvider
WeaponMechanicsItemProvider
```

`ItemStackCompiler`, `MaterialDirectiveParser`, `MaterialNameResolver`,
`MaterialAliasRegistry`, `RuntimeMaterialMatcher`, `VersionedItemFeatureSupport`,
and `LegacyItemStackHandler` own built-in material and metadata compatibility.
`NbtTagLoader` owns configured NBT tags. The accepted user-facing forms are in
[Item Construction](../shops/item-options.md) and
[Integration Compatibility](../integrations/hooks.md).

## Spawners, placeholders, and utility hooks

| Class or group | Documented responsibility |
| --- | --- |
| `SpawnerManager`, `ExternalSpawnerHandler`, and `ExternalSpawnerProvider` | External spawner plugin registration and delegation |
| `InternalSpawnerHandler`, `InternalSpawnerProvider`, and `InternalSpawnerProviderPostV1_8` | Built-in spawner item support |
| `ZaminShopPlaceholderExpansion` and `PlaceholderContextService` | PlaceholderAPI registration, identifier resolution, and short-lived player context |
| `PermissionProviderBridge` | Vault-compatible permission checks |
| `LanguageLanguageUtilsProvider` | LangUtils material, enchantment, and entity translations |

See [Spawner Providers](../integrations/spawners.md),
[PlaceholderAPI](../integrations/placeholderapi.md), and
[Utility Hooks](../integrations/utility-hooks.md).

## Public API and events

The `com.zamin.zaminshop.api` package contains the supported API-facing
interfaces and default adapters: `ZaminShop`, `ZaminShopAPI`,
`DefaultZaminShopAPI`, `ShopManager`, `ShopCategory`, `ShopItem`,
`DefaultShopCategory`, and `DefaultShopItem`.

Lifecycle and transaction events are:

```text
PlayerDataPostLoadEvent
ShopPreTransactionEvent
ShopPostTransactionEvent
ShopsPostLoadEvent
ZaminShopPostEnableEvent
```

See [Developer API](api.md) before depending on internal services.

## Compatibility support

`ServerCapabilityDetector`, `ServerCapabilities`, `VersionCapabilityMatrix`,
`ItemRuntimeSupport`, material/sound/text resolvers, NMS utilities, and the item
loading exception classes exist to fail unsupported definitions cleanly across
Minecraft versions. They do not introduce additional YAML options beyond those
documented in the item, GUI, sound, and compatibility references.

See [Version Compatibility](version-compat.md).
