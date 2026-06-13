---
description: Entry point for the current shop-item configuration references.
---

# Shop Item Guide

The complete item documentation is split by responsibility:

1. [Shop item types](item-types.md) explains `SHOP_ITEM`, `PERMISSION`, `ENCHANTMENT`, `COMMAND`, `CUSTOM`, `SHOP_CATEGORY`, and `SPECIAL`.
2. [Item construction](item-options.md) covers materials, heads, custom model data, colors, potions, banners, fireworks, trims, NBT, and comparison controls.
3. [Buying and selling](buying-selling.md) covers quantity, prices, commands, limits, comparison, and transaction behavior.
4. [Permissions and access control](access-control.md) covers category, item, world, game-mode, and direct-access restrictions.
5. [Custom item providers](../integrations/custom-items.md) covers HeadDatabase, Oraxen, Nexo, ItemsAdder, MMOItems, MythicMobs, and every other registered provider.

## Minimal product

```yaml
items:
  diamond:
    type: SHOP_ITEM
    material: DIAMOND
    quantity: 1
    buy-price: 500
    sell-price: 125
```

Do not use `type: CUSTOM` for a product. `CUSTOM` is a static menu item; external products still use `SHOP_ITEM`.
