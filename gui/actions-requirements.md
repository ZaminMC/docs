---
description: Entry point for menu actions and requirement rules.
---

# Actions and Requirements

The complete references are:

- [Actions](actions.md): every action token, click list, command executor, navigation action, sound action, favorite action, sort action, and player-setting action.
- [Requirements](requirements.md): open, view, and click requirements; boolean logic; permissions; money; items; metadata; experience; location; strings; numbers; object checks; and JavaScript evaluation.

## Combined example

```yaml
items:
  restricted-sell-menu:
    type: CUSTOM
    material: HOPPER
    slot: 13
    display-name: "&aStaff Sell Menu"
    view-requirement:
      requirements:
        staff:
          type: has permission
          permission: zaminshop.staff.sell
    click-requirement:
      requirements:
        staff:
          type: has permission
          permission: zaminshop.staff.sell
      deny-actions:
        - "[message] &cYou cannot open this menu."
    left-click-actions:
      - "[open] sell"
```

The view requirement controls rendering. The click requirement protects interaction. Use both when a hidden item must also remain protected against stale inventory clicks.
