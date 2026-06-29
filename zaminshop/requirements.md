# Requirements

Requirements control whether a menu can open, whether an item is visible, or whether a click can run.

## Places Requirements Can Be Used

```yaml
open-requirement:
view-requirement:
click-requirement:
left-click-requirement:
right-click-requirement:
shift-left-click-requirement:
shift-right-click-requirement:
middle-click-requirement:
```

## Syntax

```yaml
view-requirement:
  requirements:
    vip:
      type: has permission
      permission: "group.vip"
  deny-actions:
    - "[message] &cYou need VIP."
```

## Requirement Options

| Option | Description |
| ------ | ----------- |
| `requirements` | Map of named requirement rules. |
| `minimum-requirements` | Minimum optional rules that must pass. |
| `stop-at-success` | Stops optional checking once enough rules pass. |
| `success-actions` | Actions run when the requirement group passes. |
| `deny-actions` | Actions run when the requirement group fails. |
| `optional` | Marks a rule as optional. |

## Requirement Types

Confirmed requirement types:

| Type | Description |
| ---- | ----------- |
| `has permission` | Checks one permission. |
| `has permissions` | Checks a list of permissions. |
| `has money` | Checks the default economy provider. |
| `has item` | Checks the player inventory for an item. |
| `has meta` | Checks item metadata. |
| `has exp` | Checks player experience. |
| `is near` | Checks player distance from a location. |
| `javascript` | Evaluates a JavaScript expression. |
| `string contains` | Checks whether input contains output. |
| `string equals` | Exact string match. |
| `string equals ignorecase` | Case-insensitive string match. |
| `regex matches` | Regex match. |
| `string length` | Checks min/max string length. |
| `is object` | Checks whether input is an int, double, UUID, or player. |
| `>` | Numeric greater-than comparison. |
| `>=` | Numeric greater-than-or-equal comparison. |
| `==` | Numeric equality comparison. |
| `!=` | Numeric not-equal comparison. |
| `<=` | Numeric less-than-or-equal comparison. |
| `<` | Numeric less-than comparison. |

Prefix a type with `!` to invert it:

```yaml
type: "!has permission"
```

## Permission Example

```yaml
view-requirement:
  requirements:
    rank:
      type: has permission
      permission: "shops.vip"
  deny-actions:
    - "[message] &cYou cannot view this item."
```

## Money Example

```yaml
click-requirement:
  requirements:
    enough_money:
      type: has money
      amount: "1000"
  deny-actions:
    - "[message] &cYou need $1000."
```

## String Example

```yaml
view-requirement:
  requirements:
    world:
      type: string equals ignorecase
      input: "%player_world%"
      output: "world"
```

## Numeric Example

```yaml
click-requirement:
  requirements:
    level:
      type: ">="
      input: "%player_level%"
      output: "10"
```
