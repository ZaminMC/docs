# GUI Overview

ZaminShop menus are YAML files loaded by `ZMenuLoader`.

| File | Title | Size | Items | Types |
|---|---|---:|---:|---|
| `amount-selector.yml` | `&8Amount Selector` | `54` | 14 | `CUSTOM, SHOP_ITEM` |
| `bulk-buy.yml` | `&8Bulk Buy` | `18` | 11 | `CUSTOM` |
| `bulk-sell.yml` | `&8Bulk Sell` | `18` | 11 | `CUSTOM` |
| `favorites.yml` | `&8Favorite Items` | `45` | 11 | `CUSTOM, FAVORITE_ITEM, NEXT_PAGE, PREVIOUS_PAGE, SORT_CYCLE` |
| `gui-settings.yml` | `` | `None` | 0 | `` |
| `recent.yml` | `&8Recent Items` | `45` | 9 | `CUSTOM, NEXT_PAGE, PREVIOUS_PAGE, RECENT_ITEM, SORT_CYCLE` |
| `search.yml` | `&8ZaminShop ➔ Search: %query%` | `54` | 8 | `BACK, CUSTOM, NEXT_PAGE, PREVIOUS_PAGE, SEARCH_ITEM, SORT_CYCLE` |
| `sell.yml` | `&8Sell Items` | `54` | 10 | `CUSTOM, SELL_SLOT, SELL_SUMMARY` |
| `shop-directory.yml` | `&rZaminShop` | `54` | 16 | `CUSTOM, SHOP_CATEGORY` |

The menu system supports slots/ranges, click actions, open/close actions, requirements, item priorities, pagination, and dynamic item types.
