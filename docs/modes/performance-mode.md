# Performance Mode

Read this file with `AGENTS.md` for startup cost, repeated scans, storage churn, or cache work.

## Focus
- `ZaminShopPlugin`
- `ShopFileManager`
- `ShopManager`
- `SellLimitStorage`
- `DataManager`
- `Settings`

## Check first
- repeated reload/normalization paths
- broad per-click scans
- synchronous disk work
- avoid opening GUI and command files unless they are on the hot path
