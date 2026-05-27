# Permissions

Source-merged from `plugin.yml` and Java permission checks.

| Permission | Default | Meaning |
|---|---:|---|
| `zaminshop.admin` | `op` | Legacy alias for zaminshop.admin.* |
| `zaminshop.admin.*` | `op` | Grants all admin ZaminShop permissions |
| `zaminshop.admin.check` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.admin.help` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.admin.language` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.admin.modifier` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.admin.open-others` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.admin.reload` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.admin.risk` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.admin.sanitize` | `op` | Allows removing leaked ZaminShop GUI items from a player inventory |
| `zaminshop.admin.validate` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.buymore` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.bypassgamemode` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.bypassworld` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.check` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.item.` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.language` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.others` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.player.*` | `False` | Grants all player ZaminShop permissions |
| `zaminshop.player.buy-more` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.player.bypass.gamemode` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.player.bypass.world` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.player.favorite` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.player.recent` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.player.search` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.player.sell-more` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.player.shop` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.player.worth` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.pricemodifiers.` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.reload` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.sell.all` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.sell.all.others` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.sell.hand` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.sell.hand.all` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.sellgui` | `False` | Allows opening the configurable sell GUI |
| `zaminshop.sellmore` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.shop` | `False` | Legacy alias for zaminshop.player.shop |
| `zaminshop.shop.addmodifier` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.shop.checkmodifiers` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.shop.resetmodifier` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.shops.` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.validate` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |
| `zaminshop.worth` | `not declared` | Detected from source usage; not explicitly declared in plugin.yml. |

## Permission groups declared in plugin.yml

`zaminshop.player.*` grants the normal player feature set:

- `zaminshop.player.shop`
- `zaminshop.player.search`
- `zaminshop.player.favorite`
- `zaminshop.player.recent`
- `zaminshop.sellgui`
- `zaminshop.player.worth`
- `zaminshop.player.buy-more`
- `zaminshop.player.sell-more`

`zaminshop.admin.*` grants admin tools and also includes `zaminshop.player.*`.
