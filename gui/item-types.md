---
description: Static, transactional, navigational, dynamic-list, sell, sorting, confirmation, and player-setting menu item types.
---

# Menu Item Types

Menu item `type` values tell the renderer where content comes from and what default interaction it receives.

## Type index

| Type | Used for |
|---|---|
| `CUSTOM` | Static icon, decoration, information, or action button. |
| `SHOP_ITEM` | A transactional entry loaded by the category shop system. |
| `SHOP_CATEGORY` | Link to a category shop. |
| `FAVORITE_ITEM` | Dynamic favorite-entry template. |
| `RECENT_ITEM` | Dynamic recent-transaction template. |
| `SEARCH_ITEM` | Dynamic search-result template. |
| `SELL_SLOT` | Slot where players may place items in the sell GUI. |
| `SELL_ITEM` | Sell-GUI action item. |
| `SELL_SUMMARY` | Dynamic sell-GUI summary item. |
| `PREVIOUS_PAGE` | Previous-page control. |
| `NEXT_PAGE` | Next-page control. |
| `BACK` | Returns to the previous runtime/menu context. |
| `SORT_CYCLE` | Cycles a list menu's sort mode. |
| `CONFIRM` | Player-setting/confirmation state item. |
| `PLAYER_SETTING` | Toggles a stored player preference. |

## `CUSTOM`

```yaml
items:
  'information':
    type: CUSTOM
    material: BOOK
    slot: 4
    display-name: "&eInformation"
    lore:
      - "&7This item is not sold."
```

An omitted `type` defaults to the item ID uppercased. Use an explicit `type` in production files so behavior remains obvious.

## `SHOP_ITEM`

Transactional category entries use:

```yaml
items:
  'diamond':
    type: SHOP_ITEM
    material: DIAMOND
    buy-price: 500
    sell-price: 125
```

When a category defines `pagination.shop-item-slots`, these items are placed into pagination slots in YAML order. Explicit `slot` values are not used for those paginated transactional entries.

## `SHOP_CATEGORY`

```yaml
items:
  'minerals':
    type: SHOP_CATEGORY
    material: DIAMOND
    slot: 22
    shop: minerals
```

When no click actions are configured, ZaminShop automatically binds a left-click `[shop] minerals` action.

## Dynamic list templates

Favorites:

```yaml
items:
  'favorite-entry':
    type: FAVORITE_ITEM
    slots:
      - 10-16
      - 19-25
    display-name: "%zaminshop_current_item_name%"
```

Recent:

```yaml
items:
  'recent-entry':
    type: RECENT_ITEM
    slots:
      - 10-16
      - 19-25
```

Search:

```yaml
items:
  'search-entry':
    type: SEARCH_ITEM
    slots:
      - 10-16
      - 19-25
```

Only one dynamic list family is detected per menu. The first matching dynamic provider type determines whether the menu is treated as favorites, recent, or search.

The actual icon comes from each shop item's display/placeholder item. The dynamic definition supplies display-name and lore formatting.

## Page controls

```yaml
items:
  'previous-page':
    type: PREVIOUS_PAGE
    material: ARROW
    slot: 48
    show-when-unavailable: false
    display-name: "&ePrevious Page"
    left-click-actions:
      - "[previous_page]"

  'back':
    type: BACK
    material: BARRIER
    slot: 49
    display-name: "&cBack"
    left-click-actions:
      - "[back]"

  'next-page':
    type: NEXT_PAGE
    material: ARROW
    slot: 50
    show-when-unavailable: false
    display-name: "&eNext Page"
    left-click-actions:
      - "[next_page]"
```

Default actions are added for `BACK`, `PREVIOUS_PAGE`, and `NEXT_PAGE` when no actions are configured.

`show-when-unavailable: false` hides a page button when no page exists in that direction.

`shift-click-jump: true` makes shift-click jump to the first or last page rather than one page.

## `SORT_CYCLE`

```yaml
items:
  'sort':
    type: SORT_CYCLE
    slot: 49
    default: RELEVANCE
    modes:
      - RELEVANCE
      - CHEAPEST
      - MOST_EXPENSIVE
      - SHOP_ORDER
      - ALPHABETICAL
    current:
      RELEVANCE:
        material: COMPASS
        display-name: "&eSort: Relevance"
      CHEAPEST:
        material: GOLD_NUGGET
        display-name: "&eSort: Cheapest"
```

Automatic controls:

| Click | Action |
|---|---|
| Left | Next sort mode |
| Right | Previous sort mode |
| Shift-left | Reset to default |
| Shift-right | Reset to default |

Built-in defaults:

* Recent: `RECENT`, `OLDEST`, `MOST_BOUGHT`, `USEFUL`
* Search: `RELEVANCE`, `CHEAPEST`, `MOST_EXPENSIVE`, `SHOP_ORDER`, `ALPHABETICAL`
* Favorites: `FAVORITE_RECENT`, `MOST_BOUGHT`, `CHEAPEST`, `MOST_EXPENSIVE`, `SHOP_ORDER`, `ALPHABETICAL`

## `CONFIRM` and `PLAYER_SETTING`

These stateful item types resolve a setting key and automatically bind:

```text
[toggle_player_setting] <setting-key>
```

Example:

```yaml
items:
  'confirm-purchases':
    type: PLAYER_SETTING
    slot: 22
    setting-key: confirm-purchases
    current:
      enabled:
        material: LIME_DYE
        display-name: "&aPurchase confirmation enabled"
      disabled:
        material: GRAY_DYE
        display-name: "&7Purchase confirmation disabled"
```

Available stored defaults in `config.yml`:

```yaml
player-settings:
  defaults:
    confirm-purchases: false
    return-to-shop: true
```

## Sell GUI types

`SELL_SLOT` marks inventory positions where player items may be placed.

`SELL_ITEM` represents a configured sell action/control.

`SELL_SUMMARY` renders the current sell summary.

Their behavior belongs to the sell GUI manager rather than the ordinary static-menu renderer. See [Sell GUI](sell-gui.md).

## Priority and overlapping slots

```yaml
priority: 50
```

Lower numeric priority wins when several configured items compete for a slot. The bundled filler uses a high number such as `999`, allowing functional buttons to replace it.

## Page visibility

Supported keys include:

```yaml
display-page: 1
only-show-on-page: 1
```

Use pagination families for repeated dynamic content and page controls. Use page visibility for static elements that belong only on one page.
