# Commands

ZaminShop registers two root commands in `plugin.yml`:

- `/zaminshop`
- `/sell`

It also registers aliases for `/zaminshop`:

- `/shop`
- `/zshop`
- `/zhop`

In practice:

- `/shop` is the normal player-facing entry
- `/zaminshop` is the admin root
- `/sell` is the direct selling command root

## Player commands

### `/shop`

Opens the main shop entry for the active pack command.

- Permission: `zaminshop.player.shop`
- Sender: player only
- Notes: if `disableMainMenu` is enabled, the default main menu path is blocked

### `/shop help [page]`

Shows player help.

- Permission: none enforced in the command class
- Sender: any

### `/shop search <query>`

Searches the currently scoped shop pack.

- Permission: `zaminshop.player.search`
- Sender: player only
- Aliases: `find`
- Notes: search must be enabled in `config.yml -> search.enabled`

Example:

```text
/shop search diamond
```

### `/shop favorites`

Opens the global favorites menu.

- Permission: `zaminshop.player.favorite`
- Sender: player only
- Aliases: `fav`, `favorite`

### `/shop recent`

Opens the global recent transactions menu.

- Permission: `zaminshop.player.recent`
- Sender: player only
- Aliases: `history`, `transactions`

### `/shop sell`

Opens the configurable sell GUI.

- Permission: `zaminshop.sellgui`
- Sender: player only
- Notes: the GUI can also be disabled by config

## Admin commands

### `/zaminshop help [page]`

Shows admin help.

- Permission: `zaminshop.admin.help`
- Sender: any

### `/zaminshop reload`

Reloads ZaminShop configuration, menus, and registered shop packs.

- Permission: `zaminshop.admin.reload`
- Sender: any

### `/zaminshop validate`

Validates menus, configs, and shop files.

- Permission: `zaminshop.admin.validate`
- Sender: any

### `/zaminshop risk <list|confirm|reset> [riskId]`

Works with the risk guard system.

- Permission: `zaminshop.admin.risk`
- Sender: any

### `/zaminshop language [reload|<locale>]`

Reloads or switches the active language.

- Permission: `zaminshop.admin.language`
- Sender: any

### `/zaminshop sanitize <player>`

Removes leaked GUI-owned items from a player inventory.

- Permission: `zaminshop.admin.sanitize`
- Sender: any

### `/zaminshop check`

Shows the held item material and durability for the executing player.

- Permission: `zaminshop.admin.check`
- Sender: player only

### `/zaminshop worth`

Checks the value of the item in hand.

- Permission: `zaminshop.player.worth`
- Sender: player only
- Alias: `w`

### `/zaminshop search <query>`

Runs the admin search subcommand.

- Permission: `zaminshop.player.search`
- Sender: player only

### `/zaminshop recent`

Opens the recent transactions view through the admin root.

- Permission: `zaminshop.player.recent`
- Sender: player only

### `/zaminshop addmodifier ...`

Adds a price modifier.

- Permission: `zaminshop.admin.modifier`
- Sender: any
- Aliases: `setmodifier`, `am`, `sm`

### `/zaminshop resetmodifier ...`

Removes or resets a price modifier.

- Permission: `zaminshop.admin.modifier`
- Sender: any
- Aliases: `removemodifier`, `deletemodifier`, `rm`, `dm`

### `/zaminshop checkmodifiers <player>`

Shows active price modifiers for a player.

- Permission: `zaminshop.admin.modifier`
- Sender: any
- Aliases: `viewmodifiers`, `viewmodifier`, `checkmodifier`, `vm`, `cm`

## Opening shops for another player

The admin root also supports:

```text
/zaminshop <player>
/zaminshop <player> <shopId> [page]
```

- Permission: `zaminshop.admin.open-others`
- Sender: any

Behavior:

- with only a player name, ZaminShop opens the main menu for that player
- with a `shopId`, it opens a specific category shop and optional page

## Direct sell command

### `/sell hand`

Sells the item in the player's main hand.

- Permission: `zaminshop.sell.hand`

### `/sell all`

Sells matching inventory contents using the sell-all pipeline.

- Permission: `zaminshop.sell.all`

### `/sell handall`

Uses the hand-all selling path.

- Permission: `zaminshop.sell.hand.all`
