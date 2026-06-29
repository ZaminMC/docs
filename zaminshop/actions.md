# Actions

Actions run from menu items, open actions, close actions, and requirement results.

## Syntax

```yaml
left-click-actions:
  - "[message] &aHello!"
  - "[console] say %player_name% clicked the menu"
```

## Click Types

```yaml
left-click-actions:
right-click-actions:
shift-left-click-actions:
shift-right-click-actions:
middle-click-actions:
click-actions:
```

`click-actions` runs for a normal click fallback.

## Action Types

Confirmed action tokens:

| Action | Description |
| ------ | ----------- |
| `[message]` | Sends a message to the player. |
| `[broadcast]` | Broadcasts a message. |
| `[console]` | Runs a command as console. |
| `[player]` | Runs a command as the player. |
| `[chat]` | Makes the player send chat text. |
| `[sound]` | Plays a configured sound. |
| `[rawsound]` | Plays a raw Bukkit sound. |
| `[close]` | Closes the menu. |
| `[open]` | Opens a configured menu. Aliases in code include `[openguimenu]`, `[open_gui_menu]`, and `[openmenu]`. |
| `[back]` | Goes back where the current session supports it. |
| `[refresh]` | Refreshes the current menu. |
| `[next_page]` | Goes to the next page. |
| `[previous_page]` | Goes to the previous page. |
| `[toggle_favorite]` | Toggles a favorite item. |
| `[clear_favorites]` | Clears favorites. |
| `[clear_recent]` | Clears recent transactions. |
| `[toggle_compact_mode]` | Toggles compact mode. |
| `[sort_next]` | Moves to the next sort mode. |
| `[sort_previous]` | Moves to the previous sort mode. |
| `[sort_reset]` | Resets sorting. |
| `[toggle_player_setting]` | Toggles a player setting. |
| `[search]` | Starts or opens search flow. |
| `[change_amount]` | Changes amount where supported by the menu. |
| `[buy]` | Buys the selected/current item. |
| `[sell]` | Sells the selected/current item. |
| `[sell_all]` | Sells all matching items. |
| `[shop]` | Opens a shop category. |
| `[category]` | Opens a category target. |

## Examples

Open another menu:

```yaml
favorites:
  type: CUSTOM
  material: ENDER_CHEST
  slot: 11
  display-name: "&eFavorites"
  left-click-actions:
    - "[open] favorites"
```

Open a category:

```yaml
blocks:
  type: CUSTOM
  material: GRASS_BLOCK
  slot: 20
  display-name: "&aBlocks"
  left-click-actions:
    - "[shop] building_blocks"
```

Run commands:

```yaml
reward:
  type: CUSTOM
  material: DIAMOND
  slot: 13
  display-name: "&bReward"
  left-click-actions:
    - "[console] eco give %player_name% 100"
    - "[message] &aYou received $100."
```
