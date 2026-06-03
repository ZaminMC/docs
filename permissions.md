# Permissions

This page covers the built-in permission structure and the practical way to use it on a live server.

## Main permission groups

### `zaminshop.player.*`

Grants the normal player-facing shop permissions.

Includes:

- `zaminshop.player.shop`
- `zaminshop.player.search`
- `zaminshop.player.favorite`
- `zaminshop.player.recent`
- `zaminshop.sellgui`
- `zaminshop.player.worth`
- `zaminshop.player.buy-more`
- `zaminshop.player.sell-more`

### `zaminshop.admin.*`

Grants the admin toolset.

Includes:

- all player permissions
- reload
- validate
- risk tools
- language tools
- sanitize
- inspection tools
- modifier tools
- open-others support

## Direct permissions

### Player-facing

- `zaminshop.player.shop`
  - use the shop
- `zaminshop.player.search`
  - use search
- `zaminshop.player.favorite`
  - use favorites
- `zaminshop.player.recent`
  - use recent history
- `zaminshop.sellgui`
  - open the sell GUI
- `zaminshop.player.worth`
  - use worth-style inspection tools if exposed by your command setup
- `zaminshop.player.buy-more`
  - use buy-more style flows
- `zaminshop.player.sell-more`
  - use sell-more style flows

### Admin-facing

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

Some older aliases still exist for compatibility:

- `zaminshop.shop`
- `zaminshop.admin`

Do not build new permission setups around those aliases unless you have a migration reason.

## Shop access permissions

ZaminShop also supports shop-level access control.

Examples include:

- shop-specific access
- category button access
- item-level permission requirements

Use this when:

- certain packs are donor-only
- categories unlock through progression
- specific items require rank or quest completion permissions

## Category and item permission gating

Shop items and category entries can require custom permissions.

When configured correctly:

- the item remains visible if that is your menu design
- the click can be blocked
- deny lore can be shown

This is useful for:

- donor menus
- level or rank unlocks
- profession or class shops

## Recommended setups

### Survival server

Give normal players:

- `zaminshop.player.*`

Give staff:

- `zaminshop.admin.*`

### Donor pack

Keep normal player access for the base shop, then gate the premium category or premium pack with its own custom permission.

### Network or mixed-mode server

Use permissions per pack or per category rather than trying to solve everything with one root command.

## Common mistakes

### Granting only `/shop` command access

A command being visible is not the same as having permission to the feature behind it.

### Mixing pack access with item access

Pack access decides whether players may enter that experience.
Item access decides whether a specific entry can be used.

Keep those decisions separate.

### Hiding permission failures from yourself

If something “does nothing,” check both:

- permission assignment
- menu/item requirements

## Related pages

- [Commands](commands.md)
- [Shop Item Configuration](shops/shop-items.md)
- [Actions and Requirements](gui/actions-requirements.md)
