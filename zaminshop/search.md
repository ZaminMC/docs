# Search

ZaminShop includes a search command and a configurable search menu.

## Command

```text
/shop search <query>
/shop find <query>
```

Permission:

```text
zaminshop.player.search
```

Shop pack commands can also run scoped search:

```text
/shop search diamond
```

If `shops.search.on-unknown-shop-command` is enabled, unknown shop command arguments can be treated as a search query.

## config.yml

```yaml
shops:
  search:
    enabled: true
    mode: SMART
    fuzzy: true
    max-results: 45
    on-unknown-shop-command: false
```

| Option | Description |
| ------ | ----------- |
| `enabled` | Enables search. |
| `mode` | Search mode. Default is `SMART`. |
| `fuzzy` | Allows fuzzy matching. |
| `max-results` | Maximum returned results. |
| `on-unknown-shop-command` | Uses unknown shop command input as a search query. |

## Search Menu

The bundled menu is:

```text
plugins/ZaminShop/menus/search_menu.yml
```

It uses:

```yaml
open_command: search
```

Result items use:

```yaml
type: SEARCH_ITEM
```

## Input Modes

Input settings are in `gui-settings.yml`.

```yaml
input:
  search:
    default-mode: SIGN
    fallback-mode: ANVIL
    max-length: 32
    empty-text: "&cNo search entered"
    invalid-text: "&cInvalid input"
    allow-provider-filter: true
    allow-category-filter: true
    cancel-words:
      - cancel
      - stop
```

Supported input backends in code:

| Mode | Notes |
| ---- | ----- |
| `CHAT` | Uses chat input. |
| `ANVIL` | Uses an anvil input menu. |
| `SIGN` | Uses sign input. ProtocolLib support is present for sign input. |

## Search Placeholders

Confirmed menu placeholders:

```text
%query%
%zaminshop_search_query%
%zaminshop_search_count%
```

Example:

```yaml
info:
  type: CUSTOM
  material: COMPASS
  slot: 49
  display-name: "&eSearch"
  lore:
    - "&7Query: &f%zaminshop_search_query%"
    - "&7Results: &e%zaminshop_search_count%"
```
