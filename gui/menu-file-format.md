# Menu File Format

This page explains the shared GUI menu format used by ZaminShop.

## Where this format is used

The menu system powers:

- pack main menus
- shared menus in `guis/`
- category pages
- utility menus such as search, favorites, and recent

## Top-level structure

Typical example:

```yml
menu_title: "&8Favorites"
rows: 6

pagination:
  favorite-item-slots:
    single-page:
      - 9-17
      - 18-26

items:
  back:
    type: BACK
    material: BARRIER
    slot: 49
    display-name: "&cBack"
```

## Title and size

### `menu_title`

Inventory title.

Placeholders can be used where supported by the current menu context.

### `rows` or `size`

Use `rows` for the cleanest format.

`size` is still supported where applicable.

## `items`

This is where menu entries are defined.

Each item has a unique id and can define:

- `type`
- `material`
- `slot` or `slots`
- `display-name`
- `lore`
- `priority`
- `left_click_actions`
- `right_click_actions`
- `middle_click_actions`
- requirements

## Supported slots

You can use:

- single slots
- ranges
- slot lists

Examples:

```yml
slot: 13
```

```yml
slots:
  - 0-8
  - 12
  - 14
```

## Priority

Lower priority values are stronger.

Use priority when multiple definitions could target the same slot and one should intentionally win.

## Pagination

Pagination is now layout-based.

Depending on the menu type, the slot family key changes, for example:

- `shop-item-slots`
- `favorite-item-slots`
- `recent-item-slots`
- `search-item-slots`

Each family can define:

- `single-page`
- `first-page`
- `middle-page`
- `last-page`

or a uniform shorthand list.

## Navigation items

Typical navigation item types:

- `BACK`
- `PREVIOUS_PAGE`
- `NEXT_PAGE`

You can also use:

```yml
show-when-unavailable: false
shift-click-jump: true
```

`shift-click-jump` allows:

- `NEXT_PAGE` to jump to the last page
- `PREVIOUS_PAGE` to jump to the first page

## Page-restricted items

Use:

```yml
display-page: 2
```

or:

```yml
only-show-on-page:
  - 1
  - 3
  - 5-7
```

This is useful for:

- decorative items
- status items
- special-page buttons

## Placeholders

Menus support placeholders, including current context values such as:

- current item
- current category
- current shop pack
- balance
- page

Exact availability depends on where the menu is opened from.

## Related pages

- [Built-in Menus](built-in-menus.md)
- [Actions and Requirements](actions-requirements.md)
- [PlaceholderAPI](../integrations/placeholderapi.md)
