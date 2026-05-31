# Search Menu

The search system exists so players do not have to remember which category contains every item.

## What search does

Search looks through the currently scoped shop pack and opens a result menu with matching items.

Command:

```text
/shop search <query>
```

## Why it matters

As your pack grows, search becomes one of the biggest quality-of-life features in the plugin.

It helps with:

- large survival shops
- donor packs with many categories
- mixed item naming where players know the item but not the category

## Global search settings

```yaml
search:
  enabled: true
  fuzzy: true
  max-results: 45
  search-on-unknown-shop-command: false
```

### Key options

- `enabled`: turns the feature on or off
- `fuzzy`: allows looser matching
- `max-results`: caps how many results are shown
- `search-on-unknown-shop-command`: controls fallback behavior for unknown shop labels

## Permission

```text
zaminshop.player.search
```

## Search menu layout

The bundled `search.yml` uses:

- `SEARCH_ITEM` for dynamic results
- `SORT_CYCLE` for result ordering
- `PREVIOUS_PAGE` and `NEXT_PAGE` for result navigation
- `BACK` or custom back flow for returning to the previous menu

## Typical customizations

Most servers change:

- the result slot layout
- sort button wording
- back button wording
- result lore
- profile/info items

## Good practice

Keep search results readable.

A good result item usually shows:

- item name
- shop/category
- buy price
- sell price
- one-line click hints

If the lore becomes too crowded, the menu loses the speed advantage search is supposed to provide.
