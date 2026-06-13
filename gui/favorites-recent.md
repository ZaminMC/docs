---
description: Configure persistent favorites and recent purchase/sale history.
---

# Favorites and Recent Transactions

Favorites are selected by the player. Recent entries are written automatically after transactions. Both resolve their stored shop/item references against the currently loaded shops before display.

## Favorites commands

```text
/shop favorite
/shop favorites
/shop fav
```

Permission:

```text
zaminshop.player.favorite
```

## Adding and removing favorites

Middle-clicking a searchable shop item toggles it as a favorite when the player has the favorite permission.

Inside the favorites list, the shipped template says to use shift-click to remove the entry. The listener accepts shift-left or shift-right for favorite list items.

Favorites are stored as:

```text
<scoped-shop-id>:<item-id>
```

The service normalizes the key to lowercase.

## Favorites storage

Favorites are persisted through the configured database backend. The service merges records associated with the player's resolved identity IDs, which supports the plugin's identity compatibility path.

If a stored shop or item no longer exists, is inaccessible, or is blocked in the current world, it is skipped when the menu is rendered.

## Favorites menu

Default path:

```text
plugins/ZaminShop/guis/favorites.yml
```

The dynamic template is:

```yaml
items:
  favorite-item:
    type: FAVORITE_ITEM
    display-name: "&e%zaminshop_item%"
    lore:
      - "&7Shop: &f%zaminshop_shop_name%"
      - "&7Buy: &a%zaminshop_buyprice%"
      - "&7Sell: &c%zaminshop_sellprice%"
      - "&7Favorited: &f%zaminshop_favorited_since%"
```

The template is repeated across `pagination.favorite-item-slots`.

## Favorites controls

The bundled menu includes:

- `SORT_CYCLE`;
- compact-mode toggle;
- `[clear_favorites]`;
- previous and next page;
- return-to-shop button;
- empty-list item using `show-when-empty: true`.

Bundled sort modes:

- `FAVORITE_RECENT`;
- `MOST_BOUGHT`;
- `CHEAPEST`;
- `MOST_EXPENSIVE`;
- `ALPHABETICAL`.

`FAVORITE_RECENT` preserves the stored favorite order. `MOST_BOUGHT` counts matching recent `BUY` records available to the service.

## Recent commands

```text
/shop recent
/shop history
/shop transactions
```

Permission:

```text
zaminshop.player.recent
```

The feature is unavailable when:

```yaml
recent-menu:
  enabled: false
```

## Recent settings

```yaml
recent-menu:
  enabled: true
  max-records-per-player: 20
  show-bought: true
  show-sold: true
  merge-duplicate-items: true
```

| Option | Behavior |
| --- | --- |
| `max-records-per-player` | Stored/displayed limit, clamped to `1`-`54`. |
| `show-bought` | Includes `BUY` entries. |
| `show-sold` | Includes `SELL` entries. |
| `merge-duplicate-items` | Keeps the newest entry for the same shop item and action. |

Buy and sell records for the same item are distinct identities because the action is part of the merge key.

Each record contains:

- scoped shop ID;
- item ID;
- `BUY` or `SELL`;
- amount;
- price;
- timestamp.

## Recent menu

Default path:

```text
plugins/ZaminShop/guis/recent.yml
```

Dynamic template:

```yaml
items:
  recent-item:
    type: RECENT_ITEM
    display-name: "&e%zaminshop_item%"
    lore:
      - "&7Shop: &f%zaminshop_shop_name%"
      - "&7Buy: &a%zaminshop_buyprice%"
      - "&7Sell: &c%zaminshop_sellprice%"
      - "&7Bought: &f%zaminshop_buy_count%x"
      - "&7Last Used: &f%zaminshop_last_used%"
```

The template is repeated across `pagination.recent-item-slots`.

Bundled controls:

- `SORT_CYCLE`;
- `[clear_recent]`;
- previous and next page;
- return-to-shop button;
- empty-list item.

Bundled sort modes:

- `RECENT`;
- `MOST_BOUGHT`;
- `OLDEST`.

`RECENT` keeps the service's newest-first order. `OLDEST` reverses timestamp order.

## Recent item interaction

Normal list clicks use the shop item transaction behavior. For a recent `SELL` record representing a physical item, the listener has a dedicated path that repeats the sale behavior for that item.

Middle click toggles the item as a favorite when permitted.

## Compact mode

The favorites menu exposes `[toggle_compact_mode]`. Compact rendering:

- removes empty lore lines;
- removes lines containing left-click, right-click, or shift-click hints;
- keeps at most four remaining lines when possible.

The compact flag is retained in the active menu session and is preserved when navigating back to that list.

## Clearing data

Menu actions:

```text
[clear_favorites]
[clear_recent]
```

These clear the current player's persisted list through the relevant service. They are menu actions, not standalone commands.

## Placeholders

Global counts:

```text
%zaminshop_favorites%
%zaminshop_favorites_count%
%zaminshop_recent_count%
%zaminshop_recent_bought_count%
%zaminshop_recent_sold_count%
```

Latest transaction:

```text
%zaminshop_last_transaction_amount%
%zaminshop_last_transaction_price%
%zaminshop_last_transaction_type%
```
