---
description: Every action token accepted by ZaminShop menu click, open, close, success, and deny action lists.
---

# Actions

Actions use:

```text
[token] optional argument
```

Example:

```yaml
left-click-actions:
  - "[message] &aOpening the minerals shop."
  - "[shop] minerals"
```

Unknown tokens are skipped and warned once.

## Click action keys

```yaml
left-click-actions:
right-click-actions:
shift-left-click-actions:
shift-right-click-actions:
middle-click-actions:
click-actions:
```

Every action key must be a YAML list.

## Messaging and commands

| Action | Argument | Behavior |
|---|---|---|
| `[message]` | Text | Sends a colorized message to the player. |
| `[broadcast]` | Text | Broadcasts a colorized message. |
| `[console]` | Command | Runs a command as console on the next tick. |
| `[player]` | Command | Runs a command as the player. |
| `[chat]` | Text | Sends text through the player's chat method. |

```yaml
left-click-actions:
  - "[message] &aPurchase menu opened."
  - "[console] say %player_name% opened the purchase menu"
  - "[player] balance"
```

`[console]` and `[player]` accept commands with or without a leading slash; ZaminShop strips one leading slash before dispatch.

## Sound

```yaml
left-click-actions:
  - "[sound] UI_BUTTON_CLICK 1.0 1.2"
```

Syntax:

```text
[sound] <sound> [volume] [pitch]
```

`[rawsound]` uses the same resolver and execution path.

Click-action defaults are volume `0.2` and pitch `1.0`. Menu open actions use volume `1.0` and pitch `1.0`.

Invalid sound names are reported by menu validation.

## Menu navigation

| Action | Behavior |
|---|---|
| `[close]` | Closes the inventory one tick later. |
| `[open] <target>` | Opens a built-in target, registered menu, or category. |
| `[back]` | Restores the previous runtime/menu context where possible. |
| `[refresh]` | Re-renders the current shop or configured menu. |
| `[next_page]` | Opens the next page. |
| `[previous_page]` | Opens the previous page. |
| `[shop] <shop-id>` | Opens a category shop. |
| `[category] <shop-id>` | Same category-opening path as `[shop]`. |

Built-in `[open]` targets:

```text
favorites
favorite
fav
recent
history
transactions
main
shop
shop-directory
sell
```

Registered menu IDs and loaded category IDs are also accepted.

## Favorites and history

| Action | Behavior |
|---|---|
| `[toggle_favorite]` | Adds or removes the clicked shop item from favorites. |
| `[clear_favorites]` | Clears favorites and reopens page 1. |
| `[clear_recent]` | Clears recent history and reopens page 1. |
| `[toggle_compact_mode]` | Toggles compact lore in a paged list menu. |

`[toggle_favorite]` does nothing when the clicked slot has no bound shop item.

## Sorting

```text
[sort_next]
[sort_previous]
[sort_reset]
```

These actions reopen the list at its first page with the updated sort mode.

## Player settings

```yaml
left-click-actions:
  - "[toggle_player_setting] confirm-purchases"
```

The action toggles the named `PlayerPreferences` value, saves player data, and refreshes the menu.

## Transaction actions

| Action | Argument | Behavior |
|---|---|---|
| `[buy]` | Optional amount | Buys the bound item or command item. |
| `[sell]` | Optional amount | Sells the bound physical item. |
| `[sell_all]` | None | Sells all matching physical items. |

```yaml
left-click-actions:
  - "[buy] 1"
right-click-actions:
  - "[sell] 1"
shift-right-click-actions:
  - "[sell_all]"
```

The amount is resolved through placeholders, then parsed as a positive integer. Invalid or empty values fall back to `1`.

`[buy]` supports:

* `SHOP_ITEM`;
* `COMMAND`;
* `PERMISSION` when amount is `1`;
* `ENCHANTMENT` when amount is `1`.

`[sell]` and `[sell_all]` support physical `SHOP_ITEM` entries.

Transaction-failure feedback can temporarily replace the clicked slot after a refused buy or sale.

## Menu open actions

Root-level:

```yaml
open-actions:
  - "[message] &aWelcome to the shop."
  - "[sound] UI_BUTTON_CLICK 1.0 1.0"
```

The inspected open-action service implements:

```text
[message]
[broadcast]
[player]
[console]
[chat]
[sound]
[rawsound]
```

Navigation and transaction actions are not executed by the open-action service.

## Menu close actions

```yaml
close-actions:
  - "[message] &7Shop closed."
```

Close actions use the configured click-action handler and therefore support its action switch. Avoid `[open]`, `[back]`, or other navigation loops in close actions unless that behavior is intentional and tested.

## Requirement actions

Actions may be attached to a whole requirement list:

```yaml
left-click-requirement:
  requirements:
    permission:
      type: has permission
      permission: "server.rank.elite"
  success-actions:
    - "[message] &aAccess granted."
  deny-actions:
    - "[message] &cElite rank required."
```

Or to one rule:

```yaml
requirements:
  permission:
    type: has permission
    permission: "server.rank.elite"
    success-actions:
      - "[sound] ENTITY_EXPERIENCE_ORB_PICKUP 1.0 1.0"
    deny-actions:
      - "[sound] ENTITY_VILLAGER_NO 1.0 1.0"
```

Rule actions run as each rule is evaluated. List actions run after the final requirement result.

{% hint style="warning" %}
A click requirement is evaluated only when that click has configured actions. A deny action by itself does not create a clickable binding.
{% endhint %}
