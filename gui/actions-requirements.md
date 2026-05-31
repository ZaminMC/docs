# Actions and Requirements

Actions and requirements are what turn a decorative inventory into a working interface.

## Click actions

ZaminShop menus support these action lists:

```yaml
left_click_actions:
right_click_actions:
shift_left_click_actions:
shift_right_click_actions:
middle_click_actions:
click_actions:
```

## What actions are for

Use actions when you want a menu item to:

- open another menu
- go to the next or previous page
- go back to the previous menu context
- send a message
- run a menu-specific behavior such as navigation or sorting

## Common examples

```yaml
left_click_actions:
  - "[open] sell"

left_click_actions:
  - "[previous_page]"

left_click_actions:
  - "[next_page]"

left_click_actions:
  - "[back]"

left_click_actions:
  - "[message] &ePlace items into the empty slots."
```

## Requirements

Requirements decide whether a player can:

- open a menu
- see a menu item

### Open requirement example

```yaml
open_requirement:
  requirements:
    permission:
      type: permission
      permission: zaminshop.player.shop
  deny_actions:
    - "[message] &cNo access."
```

### View requirement example

```yaml
view_requirement:
  requirements:
    permission:
      type: permission
      permission: some.permission
```

## When to use requirements

Requirements are useful when:

- one item should only appear to staff
- one button should only appear if a permission exists
- one menu should deny opening without custom feedback

## Common mistakes

### Hiding everything behind too many conditions

If players cannot tell why something is missing, the menu feels broken.

Use `deny_actions` or visible explanation items where possible.

### Mixing logic responsibility

Requirements should control access and visibility. They should not be treated as a replacement for fixing broken menu structure or permission design.
