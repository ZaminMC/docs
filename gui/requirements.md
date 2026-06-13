---
description: Complete syntax and option reference for menu open, view, and click requirements.
---

# Requirements

Requirements control:

* whether a menu can open;
* whether an item is rendered;
* whether a click's configured actions execute.

## Requirement locations

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

## Complete structure

```yaml
left-click-requirement:
  minimum-requirements: 1
  stop-at-success: true
  requirements:
    elite:
      type: has permission
      permission: "server.rank.elite"
      optional: true
      success-actions:
        - "[message] &aElite permission accepted."
      deny-actions:
        - "[message] &cElite permission missing."
    balance:
      type: has money
      amount: 5000
      optional: true
  success-actions:
    - "[sound] UI_BUTTON_CLICK 1.0 1.0"
  deny-actions:
    - "[sound] ENTITY_VILLAGER_NO 1.0 1.0"
```

Non-optional rules must all pass. Optional rules use `minimum-requirements`.

When `minimum-requirements` is `0` or absent, every optional rule must pass.

`stop-at-success: true` stops evaluating optional rules once enough have passed.

## Inverting a rule

Prefix the type with `!`:

```yaml
type: "!has permission"
permission: "server.shop.blocked"
```

Quote inverted types because `!` has special meaning in YAML.

## Permission requirements

One permission:

```yaml
type: has permission
permission: "server.rank.elite"
```

Several permissions:

```yaml
type: has permissions
permissions:
  - "server.rank.elite"
  - "server.quest.mines"
minimum: 1
```

Without `minimum`, every listed permission is required.

## Money requirement

```yaml
type: has money
amount: 5000
```

or:

```yaml
type: has money
placeholder: "%zaminshop_price%"
```

The check uses ZaminShop's default economy provider.

## Item requirement

```yaml
type: has item
material: DIAMOND
amount: 16
damage: 0
custom-model-data: 1201
name: "&bQuest Diamond"
lore:
  - "&7Mined in the quest world."
name_contains: false
name_ignorecase: false
lore_contains: false
lore_ignorecase: false
strict: false
armor: false
offhand: false
```

Behavior:

* `material` is required;
* `amount` defaults to `1`;
* matching amounts are accumulated across inventory stacks;
* `damage` is checked only when configured;
* `custom-model-data` requires an exact integer match;
* name and lore can use contains and ignore-case modes;
* `strict: true` requires no display name, lore, or custom model data;
* `armor` includes armor contents;
* `offhand` includes extra/off-hand contents where the runtime exposes them.

Special case:

```yaml
type: has item
material: AIR
```

This passes when the player's inventory has no empty slot.

## Persistent metadata requirement

```yaml
type: has meta
key: "zaminshop:rank"
meta_type: STRING
value: elite
```

Supported metadata types:

```text
STRING
BOOLEAN
DOUBLE
LONG
INTEGER
INT
```

For `DOUBLE`, `LONG`, `INTEGER`, and `INT`, the stored value passes when it is greater than or equal to the configured value.

An unnamespaced key is created in ZaminShop's namespace. A `namespace:key` value is resolved through Bukkit's namespaced-key parser where available.

## Experience requirement

Experience points:

```yaml
type: has exp
amount: 500
level: false
```

Levels:

```yaml
type: has exp
amount: 30
level: true
```

## Location requirement

```yaml
type: is near
location: "world,100,64,100"
distance: 10
```

The player must be in the same world and their distance must be strictly less than the configured value.

## String requirements

Contains:

```yaml
type: string contains
input: "%player_name%"
output: "Zam"
```

Exact:

```yaml
type: string equals
input: "%player_world%"
output: "world"
```

Ignore case:

```yaml
type: string equals ignorecase
input: "%player_world%"
output: "WORLD"
```

Regex:

```yaml
type: regex matches
input: "%player_name%"
regex: "^[A-Za-z0-9_]{3,16}$"
```

Invalid regular expressions are not caught inside the rule evaluator. Validate regex patterns before deploying them.

## String length

```yaml
type: string length
input: "%player_name%"
min: 3
max: 16
```

Either boundary may be omitted.

## Numeric comparisons

```yaml
type: ">="
input: "%player_level%"
output: 30
```

Supported operators:

```text
>
>=
==
!=
<=
<
```

Both values are parsed as doubles.

## Object validation

Integer:

```yaml
type: is object
input: "42"
object: integer
```

Supported object values:

```text
int
integer
double
uuid
player
```

`player` passes for an online exact player name or the UUID of an online player.

## JavaScript

```yaml
type: javascript
expression: "1 + 1 == 2"
```

`input` is accepted as a fallback key when `expression` is absent.

The expression is resolved after placeholders. JavaScript availability depends on the runtime evaluator and Java environment.

{% hint style="warning" %}
**Needs verification in code:** the evaluator implementation is present, but Java distributions differ in bundled script-engine availability. Test JavaScript requirements on the exact server Java runtime.
{% endhint %}

## Unknown types

An unknown requirement type returns `false`. It does not throw a friendly configuration error at evaluation time, so run:

```text
/zaminshop validate
```

after editing menu requirements.
