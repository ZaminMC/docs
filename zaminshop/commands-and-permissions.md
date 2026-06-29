# Commands & Permissions

## Commands

| Command | Permission | Description |
| ------- | ---------- | ----------- |
| `/zaminshop` | none | Shows plugin info or admin help when the sender has admin help permission. |
| `/zaminshop help [page]` | `zaminshop.admin.help` | Shows admin help. |
| `/zaminshop dump [shop <pack>\|category <category>]` | `zaminshop.admin.diagnostics` | Creates a support dump when paste support is enabled. |
| `/zaminshop reload [shop <shop>\|category <shop> <category>]` | `zaminshop.admin.reload` | Reloads ZaminShop. |
| `/zaminshop check` | `zaminshop.admin.check` | Checks loaded shop data. |
| `/zaminshop language [reload\|<locale>]` | `zaminshop.admin.language` | Reloads or switches language files. |
| `/zaminshop addmodifier <item\|shop\|global>` | `zaminshop.admin.modifier` | Adds or sets a price modifier. Aliases: `setmodifier`, `am`, `sm`. |
| `/zaminshop resetmodifier <item\|shop\|global>` | `zaminshop.admin.modifier` | Removes a price modifier. Aliases: `removemodifier`, `deletemodifier`, `rm`, `dm`. |
| `/zaminshop checkmodifiers <player>` | `zaminshop.admin.modifier` | Shows active price modifiers. Aliases: `viewmodifiers`, `viewmodifier`, `checkmodifier`, `vm`, `cm`. |
| `/zaminshop blocklink add <shop>` | `zaminshop.admin.block-links.add` | Starts block-link add mode. |
| `/zaminshop blocklink remove` | `zaminshop.admin.block-links.remove` | Starts block-link remove mode. |
| `/zaminshop blocklink list [shop]` | `zaminshop.admin.block-links.list` | Lists linked shop blocks. |
| `/zaminshop blocklink clear <shop>` | `zaminshop.admin.block-links.clear` | Removes links for a shop target. |
| `/zaminshop blocklink cancel` | player only | Cancels your pending block-link action. |
| `/zaminshop blocklink tp <world> <x> <y> <z>` | `zaminshop.admin.block-links.list` | Teleports to a listed linked block. |
| `/shop` | `zaminshop.player.shop` | Opens the default shop pack or shop directory. |
| `/shop help [page]` | none | Shows player help. |
| `/shop search <query>` | `zaminshop.player.search` | Searches shop items. Alias: `find`. |
| `/shop favorites` | `zaminshop.player.favorite` | Opens favorites. Aliases: `fav`, `favorite`. |
| `/shop recent` | `zaminshop.player.recent` | Opens recent transactions. Aliases: `history`, `transactions`. |
| `/shop sell` | `zaminshop.player.sell-gui` | Opens the sell GUI. |
| `/worth` | `zaminshop.player.worth` | Shows the worth of the held item. The label is configurable. |
| `/sell hand [quantity]` | `zaminshop.sell.hand` | Sells items from your hand. Aliases are configurable. |
| `/sell handall` | `zaminshop.sell.hand.all` | Sells matching held items. Aliases are configurable. |
| `/sell all [shop]` | `zaminshop.sell.all` | Sells matching inventory items. Aliases are configurable. |

## Dynamic Commands

Shop packs can register commands from their `main.yml`.

```yaml
open_command: shop
register_command: true
```

Menus can also register commands with `open_command`.

```yaml
open_command: favorites
register_command: true
```

Command labels can be changed in `config.yml`:

```yaml
commands:
  worth:
    enabled: true
    labels:
      - worth
  sell:
    enabled: true
    labels:
      - sell
```

## Permissions

| Permission | Used for |
| ---------- | -------- |
| `zaminshop.player.*` | Grants player permissions listed in `plugin.yml`. |
| `zaminshop.admin.*` | Grants admin permissions listed in `plugin.yml`. |
| `zaminshop.player.shop` | Open normal shop menus. |
| `zaminshop.player.search` | Use search. |
| `zaminshop.player.favorite` | Open favorites. |
| `zaminshop.player.recent` | Open recent transactions. |
| `zaminshop.player.sell-gui` | Open the sell GUI. |
| `zaminshop.player.worth` | Use worth command. |
| `zaminshop.player.buy-more` | Use bulk buy button. |
| `zaminshop.player.sell-more` | Use bulk sell button. |
| `zaminshop.player.bypass.gamemode` | Bypass disabled gamemode checks. |
| `zaminshop.player.bypass.world` | Bypass disabled world checks. |
| `zaminshop.player.block-links` | Use linked shop blocks when block-link permission checks are enabled. |
| `zaminshop.player.price-modifiers.<id>` | Receive a permission price modifier with that ID. |
| `zaminshop.admin.help` | Use admin help. |
| `zaminshop.admin.diagnostics` | Create support dumps. |
| `zaminshop.admin.reload` | Reload ZaminShop. |
| `zaminshop.admin.language` | Manage language files. |
| `zaminshop.admin.check` | Use shop check command. |
| `zaminshop.admin.modifier` | Manage price modifiers. |
| `zaminshop.admin.open-others` | Open shops for other players. |
| `zaminshop.admin.block-links.*` | Grants block-link admin permissions. |
| `zaminshop.admin.block-links.add` | Add block links. |
| `zaminshop.admin.block-links.remove` | Remove block links. |
| `zaminshop.admin.block-links.list` | List and teleport to block links. |
| `zaminshop.admin.block-links.clear` | Clear block links. |
| `zaminshop.sell.hand` | Use `/sell hand`. |
| `zaminshop.sell.hand.all` | Use `/sell handall`. |
| `zaminshop.sell.all` | Use `/sell all`. |
| `zaminshop.sell.all.others` | Use sell-all for another player when the command path requests a target. |
