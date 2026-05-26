# GUI Mode

Read this file with `AGENTS.md` for menu rendering, click routing, and session behavior.

## Focus
- `PlayerListener`
- `MenuSession`
- `ShopMenuSession`
- `ShopDirectoryMenu`
- `AmountSelectorMenu`
- `BulkAmountSelectorMenu`
- `Settings`

## Avoid first
- economy providers
- persistence layer
- broad shop-loading internals unless the bug starts during menu build
