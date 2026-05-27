# Commands

ZaminShop registers two command roots in `plugin.yml`:

| Command | Source behavior |
|---|---|
| `/zaminshop` | Main command. Also has aliases `/shop`, `/zshop`, `/zhop`, but the Java command handler treats the literal label `shop` as the player shop command. |
| `/sell` | Sell command root for selling items from hand/inventory. |

## Player-facing `/shop`

| Command | Permission | Notes |
|---|---|---|
| `/shop` | `zaminshop.player.shop` | Opens the configured shop directory unless `disableMainMenu` is true. |
| `/shop help [page]` | none enforced by help subcommand | Shows player help. |
| `/shop search <query>` | `zaminshop.player.search` | Opens search results when `search.enabled` is true. Alias: `find`. |
| `/shop favorites` | `zaminshop.player.favorite` | Opens favorites. Aliases: `fav`, `favorite`. |
| `/shop recent` | `zaminshop.player.recent` | Opens recent transaction menu. Aliases: `history`, `transactions`. |
| `/shop sell` | no explicit subcommand permission; sell GUI itself uses config permission | Opens configured sell GUI. |

## Admin and shared `/zaminshop` subcommands

| Usage | Aliases | Permission | Sender |
|---|---|---|---|
| `/zaminshop addmodifier <item|shop|global>` | `addmodifier, setmodifier, am, sm` | `zaminshop.admin.modifier` | Console ok |
| `/zaminshop checkmodifiers <player>` | `viewmodifiers, viewmodifier, checkmodifiers, checkmodifier, vm, cm` | `zaminshop.admin.modifier` | Console ok |
| `/zaminshop check` | `check` | `zaminshop.admin.check` | Player only |
| `/shop favorites` | `fav, favorite, favorites` | `zaminshop.player.favorite` | Player only |
| `adminHelp ? "/zaminshop help [page]" : "/shop help [page]` | `help, ?` | `none in subcommand` | Console ok |
| `/zaminshop language [reload|<locale>]` | `language, lang` | `zaminshop.admin.language` | Console ok |
| `/shop recent` | `recent, history, transactions` | `zaminshop.player.recent` | Player only |
| `/zaminshop reload` | `reload` | `zaminshop.admin.reload` | Console ok |
| `/zaminshop resetmodifier <item|shop|global>` | `resetmodifier, removemodifier, deletemodifier, rm, dm` | `zaminshop.admin.modifier` | Console ok |
| `/zaminshop risk <list|confirm|reset> [riskId]` | `risk` | `zaminshop.admin.risk` | Console ok |
| `/zaminshop sanitize <player>` | `sanitize` | `zaminshop.admin.sanitize` | Console ok |
| `/shop search <query>` | `search, find` | `zaminshop.player.search` | Player only |
| `/shop sell` | `sell` | `none in subcommand` | Player only |
| `/zaminshop validate` | `validate` | `zaminshop.admin.validate` | Console ok |
| `/zaminshop worth` | `worth, w` | `zaminshop.player.worth` | Player only |

## Opening shops for other players

The command handler also supports opening menus for online players:

```text
/zaminshop <player>
/zaminshop <player> <shopId> [page]
```

Required permission:

```text
zaminshop.admin.open-others
```

Behavior:

- With only the player name, it opens the shop directory for that player.
- With a shop id, it opens that specific shop.
- `sudoAllowAllShopsAccess`, `disableSudoWorldPermissionCheck`, and `disableSudoShopPermissionCheck` control how much normal access checking is bypassed.

## `/sell`

The plugin registers:

```text
/sell <hand|all>
```

Related permissions are under sell permissions in the Permissions page.
