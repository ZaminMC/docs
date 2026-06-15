---
description: Register pack commands, category commands, subcommands, menu roots, and shop-link buttons.
---

# Custom Commands and Shop Links

ZaminShop can expose a pack, category, or built-in menu through custom command mappings.

## Pack root commands

In:

```text
plugins/ZaminShop/shops/survival_shop/main.yml
```

configure:

```yaml
open_command:
  - shop
  - market
```

The pack can then open through:

```text
/shop
/market
```

The runtime registers pack roots dynamically when they are not already declared.

## Category root commands

In a category file:

```yaml
open_command:
  - minerals
  - ores
```

The category can then open through:

```text
/minerals
/ores
```

Each value must be a command label. Empty values are warned and ignored.

## Category subcommands

```yaml
open_sub_command:
  - minerals
  - ores
```

With a pack root of `shop`, players can use:

```text
/shop minerals
/shop ores
```

A subcommand is unreachable when its owning pack has no root command. ZaminShop reports that condition during loading.

Values must be single tokens. A value containing spaces is invalid.

## Menu command registration

A menu file can declare:

```yaml
register_command: true
open_command:
  - shopsearch
```

`register_command` has no effect without at least one `open_command`.

Menus intended for runtime root registration should use a single command label rather than a string containing spaces.

## Command collisions

ZaminShop tracks command ownership across:

* plugin roots;
* shop packs;
* categories;
* registered menus.

Duplicate mappings are diagnosed. A later definition does not become a safe way to override another plugin's command.

Use:

```text
/zaminshop reload
```

after changing command mappings.

## Disable `/sell`

```yaml
disableCommands:
  sell: true
```

This prevents ZaminShop from registering `/sell`.

{% hint style="danger" %}
Changing `disableCommands.sell` requires a full server restart. `/zaminshop reload` cannot change Bukkit command ownership safely.
{% endhint %}

## Shop links inside menus

Main-menu category button:

```yaml
items:
  'category_minerals':
    type: SHOP_CATEGORY
    material: DIAMOND
    slot: 22
    display-name: "&bMinerals"
    shop: minerals
```

Explicit link section:

```yaml
items:
  'category_minerals':
    type: SHOP_CATEGORY
    material: DIAMOND
    slot: 22
    display-name: "&bMinerals"
    link:
      shop: minerals
      page: 1
```

When no click action is configured, the menu resolver automatically creates:

```text
[shop] minerals
```

The button is disabled when the target does not exist or the player cannot access it.

## Action-based navigation

Static button:

```yaml
items:
  'open_sell_menu':
    type: CUSTOM
    material: HOPPER
    slot: 49
    display-name: "&aSell items"
    left-click-actions:
      - "[open] sell"
```

Category action:

```yaml
left-click-actions:
  - "[shop] minerals"
```

Page navigation:

```yaml
left-click-actions:
  - "[next_page]"
```

See [Actions](../gui/actions.md) for all accepted action tokens.
