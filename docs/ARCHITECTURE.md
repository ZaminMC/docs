# Architecture

Use this file when the task spans multiple systems.

## Main runtime flow
- Plugin bootstrap and reload are owned by `ZaminShopPlugin`.
- Shop/menu coordination is owned by `ShopManager`.
- All item and money mutations must route through `ShopTransactionService`.
- GUI state is server-side through `MenuSession` and its subclasses.

## Runtime boundaries
- Config activation boundary: `ConfigSnapshot`
- Transaction boundary: `ShopTransactionService`
- GUI authority boundary: `MenuSession`
- Shop loading boundary: `ShopFileManager` + `ShopManager`

## Read these files first
- `src/main/java/com/zamin/zaminshop/bootstrap/ZaminShopPlugin.java`
- `src/main/java/com/zamin/zaminshop/feature/shop/ShopManager.java`
- `src/main/java/com/zamin/zaminshop/service/transaction/ShopTransactionService.java`
- `src/main/java/com/zamin/zaminshop/bootstrap/listener/PlayerListener.java`
