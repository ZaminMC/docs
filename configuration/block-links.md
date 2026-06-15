---
description: Link physical world blocks to shop packs or category shops.
---

# Physical Shop Block Links

Block links let a physical world block open a shop pack or category without reading configuration on every click.

Links are stored in:

```text
plugins/ZaminShop/block-links.yml
```

This file is generated and maintained by the plugin.

## Configuration

```yaml
block-links:
  # Master switch for block links.
  enabled: true

  # Cancel the block's normal right-click behavior when it opens a shop.
  cancel-vanilla-interaction: true

  # Require the configured permission before a player can use a link.
  require-permission-to-use: false

  # Permission checked when the requirement is enabled.
  permission: "zaminshop.player.block-links"

  # Show the linked target when a player left-clicks the block.
  allow-left-click-info: true

  # Stop players without the remove-management permission from breaking links.
  prevent-breaking-linked-blocks: true

  # Remove the stored link when its block is broken.
  remove-link-if-block-breaks: false

  # Time allowed to right-click a block after starting add/remove mode.
  link-tool-timeout-seconds: 60
```

## Link a block

Start add mode:

```text
/zaminshop blocklink add survival_shop
```

Then right-click the block to store the link.

The target may be:

- a shop pack ID;
- a scoped category ID;
- a local category ID when it resolves to a loaded shop.

Pack IDs are offered by tab completion. Category IDs are accepted by the service but are not added to the current tab-completion list.

## Remove one link

```text
/zaminshop blocklink remove
```

Then right-click the linked block.

## List links

```text
/zaminshop blocklink list survival_shop
```

The command returns serialized positions in this format:

```text
world:x:y:z
```

## Clear links for one target

```text
/zaminshop blocklink clear survival_shop
```

This removes every stored link whose target matches `survival_shop`.

## Cancel link mode

```text
/zaminshop blocklink cancel
```

Add and remove sessions also expire after `link-tool-timeout-seconds`, and are cleared when the player quits or the plugin reloads.

## Player interaction

- Right-click opens the linked target.
- Left-click shows the target when `allow-left-click-info` is enabled.
- Off-hand duplicate interaction events are ignored.
- Missing targets are reported instead of opening a menu.
- When use permissions are enabled, the configured permission is checked before opening.

## Breaking linked blocks

When protection is enabled, a player without:

```text
zaminshop.admin.block-links.remove
```

cannot break a linked block.

If a permitted player breaks it:

- `remove-link-if-block-breaks: true` removes the stored link;
- `false` leaves the stored position in `block-links.yml`.

## Permissions

```text
zaminshop.admin.block-links.add
zaminshop.admin.block-links.remove
zaminshop.admin.block-links.list
zaminshop.admin.block-links.clear
zaminshop.player.block-links
```
