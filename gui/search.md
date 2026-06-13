---
description: Configure search matching, ranking, permissions, sorting, and the search results menu.
---

# Search

## Commands

```text
/shop search <query>
/shop find <query>
```

Permission:

```text
zaminshop.player.search
```

The query is every word after `search` or `find`. A search opened through a pack command is scoped to that pack; the normal root search has no forced pack scope.

## Global settings

```yaml
search:
  enabled: true
  mode: SMART
  max-results: 45
  search-on-unknown-shop-command: false
```

| Option | Behavior |
| --- | --- |
| `enabled` | Master search switch. |
| `mode` | `EXACT`, `SIMPLE`, `FUZZY`, or `SMART`. |
| `max-results` | Result cap, clamped to `1`-`45`. |
| `search-on-unknown-shop-command` | Treats unknown `/shop ...` arguments as search text. |

When `mode` is blank, the legacy `search.fuzzy` value selects `FUZZY` or `SIMPLE`.

## What is searchable

The service searches:

- physical items with a positive buy or sell price;
- command products with at least one command;
- enchantment products with a positive buy price;
- permission products with at least one permission and a positive buy price.

Static, category-link, and special items are excluded.

The player must have access to:

- the category;
- the current world for that category;
- the item, including generated and custom item permissions.

Items the player cannot access are not returned.

## Search fields

Each item is matched against:

- scoped shop ID;
- shop display name;
- item ID;
- Bukkit material name;
- formatted item name;
- placeholder item name when a placeholder display item exists.

Formatting colors are removed. Underscores and hyphens become spaces, punctuation is removed, and matching is case-insensitive.

## Match modes

| Mode | Matching |
| --- | --- |
| `EXACT` | Exact normalized candidate only. |
| `SIMPLE` | Exact, starts-with, contains, and full-term matching. |
| `FUZZY` | Simple matching plus tolerant token matching. |
| `SMART` | Uses the same fuzzy allowance and score-based ranking. |

Ranking gives the strongest score to an exact match, followed by starts-with and contains matches. Matching every query term adds another score bonus. Ties are ordered by shop ID, item ID, page, and slot.

## Unknown-command search

```yaml
search:
  search-on-unknown-shop-command: true
```

Then:

```text
/shop redstone repeater
```

is treated as the query `redstone repeater` when it does not match another command route.

## Search menu file

Default path:

```text
plugins/ZaminShop/guis/search.yml
```

The shipped root settings are:

```yaml
menu_title: "&8ZaminShop Search: %query%"
size: dynamic
open_command: search
register_command: true
```

`size: dynamic` lets the list renderer choose the menu size for the resolved page layout.

## Result template

```yaml
items:
  search-item:
    type: SEARCH_ITEM
    display-name: "&e%zaminshop_item%"
    lore:
      - "&7Shop: &f%zaminshop_shop_name%"
      - "&7Buy: &a%zaminshop_buyprice%"
      - "&7Sell: &c%zaminshop_sellprice%"
      - ""
      - "&eLeft-click &7Buy"
      - "&eRight-click &7Sell"
      - "&bMiddle-click &7Favorite"
```

`SEARCH_ITEM` is a template. The renderer repeats it across `pagination.search-item-slots`.

## Sorting

The bundled `SORT_CYCLE` offers:

- `RELEVANCE`;
- `CHEAPEST`;
- `MOST_EXPENSIVE`;
- `ALPHABETICAL`.

Other list-renderer modes accepted by the implementation include `OLDEST`, `MOST_BOUGHT`, `USEFUL`, and `SHOP_ORDER`, though they are not all meaningful for every list kind.

Left click advances through configured modes. Right click moves backward.

## Player interactions

Default result behavior:

- left click: buy;
- right click: sell;
- middle click: toggle favorite.

The player still passes the normal transaction, economy, inventory, shop, and item checks.

## Menu placeholders

Useful values include:

```text
%query%
%zaminshop_search_count%
%zaminshop_item%
%zaminshop_shop_name%
%zaminshop_buyprice%
%zaminshop_sellprice%
```

The list renderer supplies these menu/list values in addition to PlaceholderAPI processing.
