# Shops Overview

Shops live in:

```text
plugins/ZaminShop/shops/
```

The source ships with default shop files for blocks, armor, drops, dyes, farming, food, miscellaneous, ores, and tools.

Each shop file is loaded through the shop validation pipeline. Invalid entries are skipped when safe and reported through validation diagnostics.

Use:

```text
/zaminshop validate
```

after editing shops.
