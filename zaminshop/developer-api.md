# Developer API

ZaminShop exposes a small API package for plugin developers.

Use the public API package instead of internal runtime classes:

```text
com.zamin.zaminshop.api
```

## API Entry Points

Confirmed API classes/interfaces:

| Type | Purpose |
| ---- | ------- |
| `ZaminShopAPI` | Main API access type. |
| `ZaminShop` | API holder/access class. |
| `ShopManager` | Public shop manager API. |
| `ShopCategory` | Public category view. |
| `ShopItem` | Public item view. |

## Events

Confirmed events:

| Event | Description |
| ----- | ----------- |
| `ZaminShopPostEnableEvent` | Fired after ZaminShop enables. |
| `ShopsPostLoadEvent` | Fired after shops load. |
| `PlayerDataPostLoadEvent` | Fired after player data loads. |
| `ShopPreTransactionEvent` | Fired before a shop transaction. Can be cancelled. |
| `ShopPostTransactionEvent` | Fired after a shop transaction. |

## Custom Economy Providers

The economy manager supports API-registered custom providers with provider IDs.

Use `CUSTOM` providers for plugin-defined currencies.

## Custom Item Providers

ZaminShop has an item provider interface used by built-in custom item hooks.

Use public extension points where available and avoid depending on internal menu/session classes.

## Safe Hooking

* Wait until ZaminShop has enabled before reading shops.
* Do not mutate player inventories asynchronously.
* Do not bypass transaction events for economy actions.
* Treat shop, menu, and transaction internals as subject to change.
