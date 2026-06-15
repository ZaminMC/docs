---
description: Every built-in, dynamic, player, console, and administrative ZaminShop command.
---

# Commands

ZaminShop has two declared command roots:

| Root | Aliases | Purpose |
|---|---|---|
| `/zaminshop` | `/shop`, `/zshop`, `/zhop` | Opens shops and runs player or administrative subcommands. |
| `/sell` | None | Sells held items or inventory contents. |

Shop packs, categories, and menu files can also register commands at runtime. Those commands are explained under [Dynamic shop commands](#dynamic-shop-commands).

{% hint style="info" %}
Arguments shown inside `[square brackets]` are optional. Words inside `<angle brackets>` describe a required value and are not typed literally.
{% endhint %}

## Player commands

| Command | Aliases | Permission | Sender |
|---|---|---|---|
| `/shop` | `/zaminshop`, `/zshop`, `/zhop` | `zaminshop.player.shop` | Player |
| `/shop help [page]` | `/shop ? [page]` | None | Player or console |
| `/shop search <query>` | `/shop find <query>` | `zaminshop.player.search` | Player |
| `/shop favorite` | `/shop fav`, `/shop favorites` | `zaminshop.player.favorite` | Player |
| `/shop recent` | `/shop history`, `/shop transactions` | `zaminshop.player.recent` | Player |
| `/shop sell` | None | The sell GUI checks `zaminshop.player.sell-gui` | Player |
| `/zaminshop worth` | `/zaminshop w` | `zaminshop.player.worth` | Player |

### `/shop`

Opens the main shop directory or the main menu owned by the command's shop pack.

```text
/shop
```

The command is refused when:

* the player lacks `zaminshop.player.shop`;
* the player's game mode is listed under `disableShopsInGamemodes` and they lack `zaminshop.player.bypass.gamemode`;
* the player's world is listed under `disableShopsInWorlds` and they lack `zaminshop.player.bypass.world`;
* `disableMainMenu` is enabled;
* shops did not load successfully.

### `/shop search <query>`

Searches the current pack when executed from a pack command. The normal `/shop search` path searches without a forced category.

```text
/shop search diamond
/shop find redstone repeater
```

The query is every word after `search` or `find`.

The command requires:

* `search.enabled: true`;
* `zaminshop.player.search`;
* an allowed world and game mode.

### `/shop favorite`

Opens the player's favorites menu.

```text
/shop favorite
```

Accepted aliases:

```text
/shop fav
/shop favorites
```

### `/shop recent`

Opens the player's recorded purchase and sale history.

```text
/shop recent
```

Accepted aliases:

```text
/shop history
/shop transactions
```

The command is unavailable when `recent-menu.enabled` is `false`.

### `/shop sell`

Opens the configured sell GUI.

```text
/shop sell
```

This subcommand itself has no subcommand permission field, but the sell GUI refuses access unless its configured permission is granted. The bundled permission is:

```text
zaminshop.player.sell-gui
```

### `/zaminshop worth`

Inspects the item in the player's main hand and reports:

* whether it can be bought;
* the cheapest matching buy entry;
* whether it can be sold;
* the best matching sell entry;
* the matching shop, page, and slot.

```text
/zaminshop worth
```

This command does not accept an item argument. Hold the item in the main hand before running it.

## Sell commands

| Command | Aliases | Permission | Sender |
|---|---|---|---|
| `/sell hand [quantity]` | `/sell h [quantity]` | `zaminshop.sell.hand` | Player |
| `/sell handall` | `/sell ha` | `zaminshop.sell.hand.all` | Player |
| `/sell all [shop] [player]` | `/sell a ...` | `zaminshop.sell.all` | Player or console |

### `/sell hand [quantity]`

Sells the item in the player's main hand.

```text
/sell hand
/sell hand 16
```

Without a quantity, the command uses the held stack amount. A supplied quantity must be a positive integer no larger than the held stack.

When `sellHand.sellsAllItems` is enabled, `/sell hand` delegates to `/sell handall`.

When `sellHand.allowAllQuantities` is disabled, the requested amount must satisfy the shop item's transaction-quantity rules.

### `/sell handall`

Finds the shop entry matching the held item, then sells matching stacks from the player's inventory.

```text
/sell handall
```

Matching uses the shop item's configured comparison settings, including metadata, model, damage, NBT, and repair-cost rules where enabled.

Armor and off-hand handling follows:

```yaml
sellHand:
  excludeArmorSlots: true
  excludeOffHand: false
```

### `/sell all [shop] [player]`

Sells every sellable stack found in the target inventory.

```text
/sell all
/sell all minerals
/sell all minerals Zamin
/sell all all Zamin
```

Behavior:

* `/sell all` searches all loaded shops.
* `/sell all minerals` limits matching to the shop whose ID is `minerals`.
* `/sell all all Zamin` sells across all shops for `Zamin`; console must use this form when no shop is selected.
* Supplying a player requires `zaminshop.sell.all.others`.
* Console must supply a player.
* The command requires `zaminshop.sell.all` in every form.

{% hint style="warning" %}
The parser treats the first argument after `/sell` as both the subcommand and, inside the `all` handler, the optional shop. Use the exact forms shown above.
{% endhint %}

## Administrative commands

| Command | Aliases | Permission | Sender |
|---|---|---|---|
| `/zaminshop help [page]` | `/zaminshop ? [page]` | `zaminshop.admin.help` | Player or console |
| `/zaminshop reload` | None | `zaminshop.admin.reload` | Player or console |
| `/zaminshop overwatcher <list\|confirm\|reset> [findingId]` | None | `zaminshop.admin.overwatcher` | Player or console |
| `/zaminshop blocklink <add\|remove\|list\|clear\|cancel> [shop]` | None | Action-specific | Player or console, depending on action |
| `/zaminshop language [list\|reload\|locale]` | `/zaminshop lang ...` | `zaminshop.admin.language` | Player or console |
| `/zaminshop check` | None | `zaminshop.admin.check` | Player |
| `/zaminshop addmodifier ...` | `setmodifier`, `am`, `sm` | `zaminshop.admin.modifier` | Player or console |
| `/zaminshop checkmodifiers <player>` | `viewmodifiers`, `viewmodifier`, `checkmodifier`, `vm`, `cm` | `zaminshop.admin.modifier` | Player or console |
| `/zaminshop resetmodifier ...` | `removemodifier`, `deletemodifier`, `rm`, `dm` | `zaminshop.admin.modifier` | Player or console |
| `/zaminshop <player> [shop] [page]` | None | `zaminshop.admin.open-others` | Player or console |

### `/zaminshop reload`

Reloads plugin state, then closes every open ZaminShop GUI when the reload succeeds.

```text
/zaminshop reload
```

Reload is denied while any transaction lock is active. This prevents a configuration swap during a purchase or sale.

Root command registration changes, including `disableCommands.sell`, still require a full server restart.

Configuration, menu, and shop validation runs automatically during startup and reload. See [Automatic Validation](validation.md).

### `/zaminshop overwatcher`

Lists current economy-risk findings:

```text
/zaminshop overwatcher
/zaminshop overwatcher list
```

Confirms one finding by its reported finding ID:

```text
/zaminshop overwatcher confirm A1B2C3D4
```

Clears confirmations, reruns analysis, and rebuilds the finding list:

```text
/zaminshop overwatcher reset
```

`reset` clears persisted confirmations and immediately rebuilds the current findings.

### `/zaminshop blocklink`

Start add mode, then right-click a block:

```text
/zaminshop blocklink add survival_shop
```

Start remove mode, then right-click a linked block:

```text
/zaminshop blocklink remove
```

List or clear links for one target:

```text
/zaminshop blocklink list survival_shop
/zaminshop blocklink clear survival_shop
```

Cancel the current player's pending add/remove operation:

```text
/zaminshop blocklink cancel
```

Permissions:

```text
zaminshop.admin.block-links.add
zaminshop.admin.block-links.remove
zaminshop.admin.block-links.list
zaminshop.admin.block-links.clear
```

`add`, `remove`, and `cancel` require a player because they depend on a block click. `list` and `clear` can be used by console. `cancel` has no separate permission check.

See [Physical Shop Block Links](configuration/block-links.md).

### `/zaminshop language`

Lists installed languages:

```text
/zaminshop language
/zaminshop language list
```

Reloads the active language file:

```text
/zaminshop language reload
```

Changes the configured locale and saves it to `config.yml`:

```text
/zaminshop language en_US
```

The locale must already exist in `plugins/ZaminShop/lang/`.

### `/zaminshop check`

Reports the material and durability/data value of the item in the player's main hand.

```text
/zaminshop check
```

Console cannot use this command because it requires a held item.

## Price modifier commands

Modifiers accept these scopes:

```text
item
shop
global
```

`all` is an alias for `global`.

Action type is optional and defaults to `BOTH`:

```text
BUY
SELL
BOTH
all
```

### Add or replace a modifier

```text
/zaminshop addmodifier item Zamin minerals diamond 0.80 BUY
/zaminshop addmodifier shop Zamin minerals 1.10 SELL
/zaminshop addmodifier global Zamin 0.95 BOTH
```

Syntax:

```text
/zaminshop addmodifier item <player> <shop> <item> <modifier> [BUY|SELL|BOTH]
/zaminshop addmodifier shop <player> <shop> <modifier> [BUY|SELL|BOTH]
/zaminshop addmodifier global <player> <modifier> [BUY|SELL|BOTH]
```

The modifier must be a positive number. Offline player data is loaded from storage when available.

### View modifiers

```text
/zaminshop checkmodifiers Zamin
```

Command modifiers are available for online and stored offline players. Permission modifiers are included only when the target is online because permission checks require a live player.

### Remove modifiers

```text
/zaminshop resetmodifier item Zamin minerals diamond BUY
/zaminshop resetmodifier shop Zamin minerals BOTH
/zaminshop resetmodifier global Zamin BOTH
```

Syntax:

```text
/zaminshop resetmodifier item <player> <shop> <item> [BUY|SELL|BOTH]
/zaminshop resetmodifier shop <player> <shop> [BUY|SELL|BOTH]
/zaminshop resetmodifier global <player> [BUY|SELL|BOTH]
```

## Open a shop for another player

The administrative root treats an online player's name as an open request when it does not match a registered subcommand.

```text
/zaminshop Zamin
/zaminshop Zamin minerals
/zaminshop Zamin minerals 2
```

The first form opens the directory. The second opens a shop by ID. The third requests a positive page number.

The target must be online. Access behavior is controlled by:

```yaml
sudoAllowAllShopsAccess: false
disableSudoWorldPermissionCheck: false
disableSudoShopPermissionCheck: false
```

## Dynamic shop commands

Shop-pack `main.yml` files and category files can register root commands:

```yaml
open_command:
  - shop
  - market
```

Category files can also register subcommands:

```yaml
open_sub_command:
  - minerals
  - ores
```

That configuration can provide:

```text
/market
/shop minerals
/shop ores
```

Custom menu files can register commands when the menu definition enables command registration. Dynamic roots are created at runtime and are not listed in `plugin.yml`.

When two definitions claim the same command mapping, ZaminShop validates the conflict instead of silently replacing an existing owner.

## Unknown `/shop` arguments

By default, an unknown argument shows command usage. When enabled:

```yaml
search:
  search-on-unknown-shop-command: true
```

an unknown argument becomes a search query:

```text
/shop diamond
```

This searches for `diamond` instead of returning the unknown-command response.

## Commands that require a restart

Changing this option requires a full restart:

```yaml
disableCommands:
  sell: true
```

Normal shop, menu, language, and configuration edits can use `/zaminshop reload` unless their own page says otherwise.
