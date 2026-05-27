# Actions & Requirements

## Actions found in default GUI files

Examples:

```yaml
left_click_actions:
  - "[open] sell"
  - "[previous_page]"
  - "[next_page]"
  - "[back]"
  - "[message] &ePlace items into the empty slots."
```

Common action patterns:

| Action | Meaning |
|---|---|
| `[open] <menuId>` | Opens a configured menu. |
| `[previous_page]` | Goes to previous page. |
| `[next_page]` | Goes to next page. |
| `[back]` | Returns to previous menu/context. |
| `[message] <text>` | Sends message to player. |

## Requirements

Menus and items support requirement blocks:

```yaml
open_requirement:
  requirements:
    permission:
      type: permission
      permission: zaminshop.player.shop
  deny_actions:
    - "[message] &cNo access."
```

Item visibility can use:

```yaml
view_requirement:
  requirements:
    permission:
      type: permission
      permission: some.permission
```
