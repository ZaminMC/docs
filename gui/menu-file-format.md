# Menu File Format

ZaminShop uses a modern menu format built around:

- `menu_title`
- `rows` or `size`
- `items`
- optional `pagination`
- optional actions and requirements

## Root keys

| Key | Purpose |
|---|---|
| `menu_title` | Inventory title |
| `rows` | Inventory rows |
| `size` | Inventory size |
| `update_interval` / `refresh` | Auto-refresh interval |
| `open_command` | Commands that open the menu |
| `open_actions` | Actions run on open |
| `close_actions` | Actions run on close |
| `open_requirement` | Requirement block for opening |
| `pagination` | Dynamic slot families for paged content |
| `items` | Menu items |

## Item keys

| Key | Purpose |
|---|---|
| `type` | Menu item type |
| `material` | Display material |
| `slot` | One slot |
| `slots` | Many slots or slot ranges |
| `display-name` | Name |
| `lore` | Lore lines |
| `priority` | Slot conflict priority |
| `display-page` | Optional page restriction |
| `update` | Re-render item during refresh |
| `show-when-empty` | List-item behavior |
| `show-when-unavailable` | Navigation behavior |
| `view_requirement` | Display requirement |

## Supported click sections

```yaml
left_click_actions:
right_click_actions:
shift_left_click_actions:
shift_right_click_actions:
middle_click_actions:
click_actions:
```

## Slot ranges

```yaml
slots:
  - 10-16
  - 19-25
  - 28
```

## Pagination families

Dynamic menus use named slot families such as:

- `favorite-item-slots`
- `recent-item-slots`
- `search-item-slots`
- `shop-item-slots`

Those families can be written as:

- one shared slot list
- `single-page`
- `first-page`
- `middle-page`
- `last-page`

## Example

```yaml
menu_title: "&8Favorites"
rows: 6

pagination:
  favorite-item-slots:
    - 9-17
    - 18-26

items:
  favorite-item:
    type: FAVORITE_ITEM

  previous-page:
    type: PREVIOUS_PAGE
    material: ARROW
    slot: 37
    show-when-unavailable: false

  next-page:
    type: NEXT_PAGE
    material: ARROW
    slot: 43
    show-when-unavailable: false
```
