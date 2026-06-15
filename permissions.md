---
description: Built-in command permissions, dynamic shop permissions, item access, and modifier nodes.
---

# Permissions

ZaminShop uses Bukkit permissions for commands and access checks. Vault is not required for ordinary command, shop, or item access. A Vault-compatible permission provider is required only when purchasing `PERMISSION` shop items.

## Declared permission groups

### `zaminshop.player.*`

Default: `false`

Children:

| Permission | Purpose |
|---|---|
| `zaminshop.player.shop` | Open the main shop directory. |
| `zaminshop.player.search` | Use the search command and search menu. |
| `zaminshop.player.favorite` | Open and use favorites. |
| `zaminshop.player.recent` | Open recent transactions. |
| `zaminshop.player.sell-gui` | Open the configured sell GUI. |
| `zaminshop.player.worth` | Inspect the held item's best buy and sell entries. |
| `zaminshop.player.buy-more` | Use extended buy-more flows. |
| `zaminshop.player.sell-more` | Use extended sell-more flows. |
| `zaminshop.player.bypass.gamemode` | Ignore `disableShopsInGamemodes` for shop commands and menus. |
| `zaminshop.player.bypass.world` | Ignore `disableShopsInWorlds` for shop commands and menus. |
| `zaminshop.player.block-links` | Open linked shop blocks when use-permission checks are enabled. |

### `zaminshop.admin.*`

Default: server operators

Children:

| Permission | Purpose |
|---|---|
| `zaminshop.player.*` | Grants the declared player permission group. |
| `zaminshop.admin.help` | View administrative help. |
| `zaminshop.admin.reload` | Reload ZaminShop. |
| `zaminshop.admin.overwatcher` | List, confirm, and reset Overwatcher findings; receive Runtime Shield notices. |
| `zaminshop.admin.block-links.*` | Grants every block-link management permission. |
| `zaminshop.admin.language` | List, reload, and change languages. |
| `zaminshop.admin.check` | Inspect the held material and damage value. |
| `zaminshop.admin.modifier` | Add, view, and remove command price modifiers. |
| `zaminshop.admin.open-others` | Open directories or shops for another online player. |

Block-link management children:

| Permission | Purpose |
|---|---|
| `zaminshop.admin.block-links.add` | Start linking a physical block to a shop target. |
| `zaminshop.admin.block-links.remove` | Remove links and bypass linked-block break protection. |
| `zaminshop.admin.block-links.list` | List stored positions for a target. |
| `zaminshop.admin.block-links.clear` | Remove every link for a target. |

{% hint style="warning" %}
The `/sell` command permissions are enforced in code but are not children of `zaminshop.player.*` in `plugin.yml`. Grant them separately.
{% endhint %}

## Sell command permissions

| Permission | Command |
|---|---|
| `zaminshop.sell.hand` | `/sell hand [quantity]` |
| `zaminshop.sell.hand.all` | `/sell handall` |
| `zaminshop.sell.all` | `/sell all [shop]` |
| `zaminshop.sell.all.others` | Add a target player to `/sell all`. |

Complete LuckPerms example:

```text
/lp group default permission set zaminshop.player.shop true
/lp group default permission set zaminshop.player.search true
/lp group default permission set zaminshop.player.favorite true
/lp group default permission set zaminshop.player.recent true
/lp group default permission set zaminshop.player.sell-gui true
/lp group default permission set zaminshop.player.worth true
/lp group default permission set zaminshop.player.buy-more true
/lp group default permission set zaminshop.player.sell-more true
/lp group default permission set zaminshop.sell.hand true
/lp group default permission set zaminshop.sell.hand.all true
/lp group default permission set zaminshop.sell.all true
```

## Shop access permissions

Every category shop checks:

```text
zaminshop.player.shops.<shop-id>
```

Category IDs are pack-scoped as `<pack-folder>:<category-file>`. For the bundled `minerals` category in `survival_shop`:

```text
zaminshop.player.shops.survival_shop:minerals
```

Grant it with LuckPerms:

```text
/lp group default permission set zaminshop.player.shops.survival_shop:minerals true
```

A shop can also define additional required permissions in its YAML. All configured entries must pass in addition to the generated shop node.

## Item access permissions

Generated item permissions are checked only when the category contains:

```yaml
enable-per-item-permissions: true
```

When enabled, each transactional shop item checks either:

```text
zaminshop.player.items.<shop-id>.<item-id>
```

or the per-shop wildcard:

```text
zaminshop.player.items.<shop-id>.*
```

For a `diamond` item inside the bundled `survival_shop:minerals` category:

```text
zaminshop.player.items.survival_shop:minerals.diamond
zaminshop.player.items.survival_shop:minerals.*
```

The wildcard grants access to every item in that one shop. It is not a global wildcard implemented by the item-access check.

Example:

```text
/lp group default permission set zaminshop.player.items.survival_shop:minerals.* true
```

When `enable-per-item-permissions` is absent or `false`, these generated item nodes are not checked. Item-level `required-permissions` are still checked.

## Additional item requirements

An item may require arbitrary permissions:

```yaml
items:
  'ranked_diamond':
    type: SHOP_ITEM
    material: DIAMOND
    buy-price: 500
    required-permissions:
      - "server.rank.elite"
    permission-denied-lore:
      - "&cElite rank required."
```

`required-permissions` accepts one string or a list. Every listed permission must pass.

These requirements are additional to the generated node when per-item permissions are enabled, and are still enforced when generated item permissions are disabled.

## Permission-based price modifiers

Entries in `pricemodifiers.yml` are activated with:

```text
zaminshop.player.price-modifiers.<modifier-id>
```

For a modifier whose YAML ID is `vip_discount`:

```text
zaminshop.player.price-modifiers.vip_discount
```

Grant example:

```text
/lp group vip permission set zaminshop.player.price-modifiers.vip_discount true
```

The exact modifier ID comes from `pricemodifiers.yml`; ZaminShop does not derive it from a group name.

## Permission shop items

`type: PERMISSION` sells one or more permission nodes to the buyer:

```yaml
items:
  'builder_access':
    type: PERMISSION
    material: NETHER_STAR
    buy-price: 25000
    permission: "server.builder"
```

This transaction requires:

* Vault;
* a Vault-compatible permission provider;
* a provider that supports adding the permission.

World-specific form:

```yaml
items:
  'world_builder_access':
    type: PERMISSION
    material: NETHER_STAR
    buy-price: 25000
    permissions:
      builder:
        permission: "server.builder"
        world: "world"
```

Use `force: true` only when you intentionally want the transaction to attempt granting permissions even if the player already has them.

## Access checks are separate

These checks answer different questions:

| Layer | Question |
|---|---|
| Command permission | May the sender invoke this feature? |
| Shop permission | May this player enter the category? |
| Generated item permission | May this player use this shop entry? |
| `required-permissions` | Does the entry impose additional custom conditions? |
| Menu requirement | Should a configured GUI item be visible or clickable? |
| Purchased permission | Which permission does a `PERMISSION` item grant? |

Granting `/shop` access does not automatically grant every category or item node. Design the permission tree deliberately.
