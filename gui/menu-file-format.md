# Menu File Format

Supported root keys from `ZMenuLoader`:

| Key | Meaning |
|---|---|
| `menu_title` | Inventory title. |
| `size` | Inventory size. Normalized to 9–54 and rounded to a multiple of 9. |
| `rows` | Alternative to size. `rows * 9`. |
| `update_interval` / `refresh` | Menu refresh interval. |
| `open_command` | Commands that open this menu. |
| `open_actions` / `open_commands` | Actions run when opened. |
| `close_actions` | Actions run when closed. |
| `open_requirement` | Requirement block for opening. |
| `pagination` | Pagination layout. |
| `items` | Menu item definitions. |

## Item keys

| Key | Meaning |
|---|---|
| `type` | Dynamic item type. |
| `material` | Material or head format. |
| `item` | Nested item definition. |
| `display-name` / `display_name` | Item name. |
| `lore` | Lore lines. |
| `slot` | Single slot. |
| `slots` | Multiple slots and ranges, e.g. `10-16`. |
| `priority` | Render priority. Lower priority wins when overlapping. |
| `update` | Whether item updates. |
| `show-when-empty` | Dynamic list behavior. |
| `show-when-unavailable` | Navigation behavior. |
| `view_requirement` | Requirement block for displaying the item. |
| `glow` | Enchantment glow. |
| `item-flags` / `item_flags` | Bukkit item flags. |
| `custom-model-data` / `custom_model_data` / `model` | Custom model data. |

## Click actions

Supported action sections:

```yaml
left_click_actions:
right_click_actions:
shift_left_click_actions:
shift_right_click_actions:
middle_click_actions:
click_actions:
```

Aliases with `_commands` also work.

## Slot ranges

```yaml
slots:
  - 10-16
  - 19-25
  - 28
```
