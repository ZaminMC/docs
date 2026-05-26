# Version Compatibility

Use this file for material ids, config profiles, GUI defaults, and cross-version Bukkit behavior.

## Current compatibility model
- runtime config profile is selected in `ZaminShopPlugin`
- GUI defaults are split into `src/main/resources/guis/<profile>/`
- material ids are normalized through the material compatibility layer before runtime activation

## Primary files
- `src/main/java/com/zamin/zaminshop/bootstrap/ZaminShopPlugin.java`
- `src/main/java/com/zamin/zaminshop/config/Settings.java`
- `src/main/java/com/zamin/zaminshop/platform/item/MaterialNameResolver.java`
- `src/main/java/com/zamin/zaminshop/platform/item/MaterialConfigNormalizer.java`

## Resource paths
- `src/main/resources/config/`
- `src/main/resources/guis/`
