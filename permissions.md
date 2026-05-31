# Permissions

This page combines:

- permissions declared in `plugin.yml`
- permissions enforced directly in source

## Declared permission groups

### `zaminshop.player.*`

- Default: `false`
- Purpose: grants the normal player feature set

Children:

- `zaminshop.player.shop`
- `zaminshop.player.search`
- `zaminshop.player.favorite`
- `zaminshop.player.recent`
- `zaminshop.sellgui`
- `zaminshop.player.worth`
- `zaminshop.player.buy-more`
- `zaminshop.player.sell-more`

### `zaminshop.admin.*`

- Default: `op`
- Purpose: grants admin tools and includes `zaminshop.player.*`

Children:

- `zaminshop.admin.help`
- `zaminshop.admin.reload`
- `zaminshop.admin.validate`
- `zaminshop.admin.risk`
- `zaminshop.admin.language`
- `zaminshop.admin.sanitize`
- `zaminshop.admin.check`
- `zaminshop.admin.modifier`
- `zaminshop.admin.open-others`

## Legacy aliases

### `zaminshop.shop`

- Default: `false`
- Purpose: legacy alias for `zaminshop.player.shop`

### `zaminshop.admin`

- Default: `op`
- Purpose: legacy alias for `zaminshop.admin.*`

## Player permissions

### `zaminshop.player.shop`

Allows a player to open the normal shop entry command.

### `zaminshop.player.search`

Allows `/shop search <query>`.

### `zaminshop.player.favorite`

Allows opening the favorites menu.

### `zaminshop.player.recent`

Allows opening the recent transactions menu.

### `zaminshop.sellgui`

Allows opening the sell GUI.

### `zaminshop.player.worth`

Allows `/zaminshop worth`.

### `zaminshop.player.buy-more`

Used for bulk buy flows.

### `zaminshop.player.sell-more`

Used for bulk sell flows.

### `zaminshop.player.bypass.gamemode`

Bypasses blocked gamemode checks for shop access.

### `zaminshop.player.bypass.world`

Bypasses blocked world checks for shop access.

## Admin permissions

### `zaminshop.admin.help`

Allows admin help output.

### `zaminshop.admin.reload`

Allows `/zaminshop reload`.

### `zaminshop.admin.validate`

Allows `/zaminshop validate`.

### `zaminshop.admin.risk`

Allows risk guard administration commands.

### `zaminshop.admin.language`

Allows language management commands.

### `zaminshop.admin.sanitize`

Allows `/zaminshop sanitize <player>`.

### `zaminshop.admin.check`

Allows `/zaminshop check`.

### `zaminshop.admin.modifier`

Allows price modifier commands.

### `zaminshop.admin.open-others`

Allows opening shop menus for another player.

## Sell command permissions

### `zaminshop.sell.hand`

Allows `/sell hand`.

### `zaminshop.sell.hand.all`

Allows `/sell handall`.

### `zaminshop.sell.all`

Allows `/sell all`.

## Notes

- Some permissions are enforced in code but not declared individually in `plugin.yml`
- If you want a strict permission plugin setup, grant the exact nodes you use instead of relying only on the wildcard groups
- Dynamic shop pack commands still rely on the normal shop access checks
