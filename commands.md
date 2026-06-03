# Commands

This page explains the commands that matter in day-to-day operation.

## Main command roots

ZaminShop ships with these plugin command roots:

- `/zaminshop`
- `/shop` as an alias of `/zaminshop`
- `/zshop`
- `/zhop`
- `/sell`

In addition, shop packs and category files can register their own open commands.

## Player commands

### `/shop`

Opens the main command path for the active pack configuration.

What it does depends on your current setup:

- if a pack main menu is bound to `shop`, it opens that pack menu
- if you use subcommands, `/shop <subcommand>` can open a category or custom menu target

### `/shop search <query>`

Searches items in the current pack context.

Use this when:

- players know the item name
- your pack has many categories
- you want a faster path than category browsing

### `/shop favorites`

Opens the favorites menu if it is enabled.

### `/shop recent`

Opens the recent transactions menu if it is enabled.

### `/shop sell`

Opens the sell GUI if it is enabled.

### `/sell`

ZaminShop also registers `/sell` for sell-focused flows.

Exact behavior depends on your configuration and available subcommands such as:

- hand-based selling
- sell-all behavior
- GUI-driven selling

If you do not want ZaminShop to own `/sell`, use:

```yml
disableCommands:
  sell: true
```

and restart the server.

## Admin commands

### `/zaminshop reload`

Reloads configuration, menus, packs, language files, and runtime references.

Use it after:

- editing `config.yml`
- editing GUI menu files
- editing shop pack files
- changing language content

### `/zaminshop validate`

Runs shop and menu validation.

This is one of the most important admin commands in the plugin.

Use it after:

- adding or moving shop packs
- editing category files
- changing menu commands
- changing pagination layouts
- adding new item directives or hooks

### `/zaminshop risk list`

Lists current risk guard findings.

This is where you review:

- pricing problems
- arbitrage paths
- blocked items or shops
- findings that require confirmation

### `/zaminshop language`

Used for language inspection and switching when supported by your setup.

### `/zaminshop sanitize`

Used to remove leaked GUI-owned items from inventories when cleanup is needed.

### `/zaminshop check`

Used for item/shop inspection workflows such as held-item checks and worth checks.

### `/zaminshop modifier`

Used for price modifier management when modifiers are enabled.

## Dynamic pack and category commands

ZaminShop can register commands from:

- `shops/<pack>/main.yml` via `open_command`
- category shop files via `open_command`
- category shop files via `open_sub_command`

Examples:

```yml
open_command:
  - shop
```

```yml
open_command:
  - buildingblocks
```

```yml
open_sub_command:
  - buildingblocks
```

That allows flows such as:

- `/shop`
- `/buildingblocks`
- `/shop buildingblocks`

depending on how you configure the pack and category.

## Command collisions

If two menus or packs try to claim the same command, ZaminShop warns and keeps the existing owner instead of silently overriding it.

You should still design your command layout intentionally.

Good practice:

- one clear main command per pack
- unique standalone category commands when used
- subcommands when you want pack-scoped category routing

## Common mistakes

### Treating every category as a root command

This works, but it can make the command space noisy. Prefer `open_sub_command` where the category belongs under a pack root.

### Forgetting to restart after `disableCommands`

Command registration ownership needs a full restart for some root-command changes.

### Not validating command changes

If you move command structure around, run `/zaminshop validate`.

## Related pages

- [Permissions](permissions.md)
- [Shop Pack File Format](shops/shop-file-format.md)
- [Menu File Format](gui/menu-file-format.md)
