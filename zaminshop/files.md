# Files

ZaminShop stores its files in `plugins/ZaminShop/`.

```text
plugins/ZaminShop/
├── config.yml
├── currency.yml
├── gui-settings.yml
├── lang/
│   └── en_US.yml
├── menus/
│   ├── favorites_menu.yml
│   ├── recent_menu.yml
│   ├── search_menu.yml
│   └── sell_menu.yml
├── shops/
│   ├── packs/
│   │   └── survival_shop/
│   │       ├── main.yml
│   │       └── categories/
│   │           ├── building_blocks.yml
│   │           ├── colorful_blocks.yml
│   │           ├── food.yml
│   │           ├── minerals.yml
│   │           ├── miscellaneous.yml
│   │           ├── mob_drops.yml
│   │           ├── redstone_items.yml
│   │           └── spawners.yml
│   └── shared_menus/
│       ├── amount-selectors/
│       ├── bulk-buy/
│       ├── bulk-sell/
│       └── purchase-confirmation/
└── webhooks/
    └── config.yml
```

## config.yml

Main plugin settings.

Used for database settings, command labels, shop toggles, buying and selling behavior, price modifiers, item matching, access rules, safety, sell limits, block links, formatting, transaction logging, and advanced click/input settings.

## currency.yml

Currency providers and currency selection settings.

The default file registers `vault`, `internal`, `playerpoints`, and `item`.

## gui-settings.yml

Shared GUI behavior.

Used for built-in menu defaults, price visibility, click actions, item lore formats, input modes, transaction failure feedback, shared buttons, and sell GUI settings.

## lang/

Language files.

The bundled default is `en_US.yml`.

## menus/

Standalone menus:

* `favorites_menu.yml`
* `recent_menu.yml`
* `search_menu.yml`
* `sell_menu.yml`

These menus can define `open_command`, items, actions, requirements, and layout.

## shops/packs/

Shop packs.

Each pack has a `main.yml` file and a `categories/` folder.

## shops/shared_menus/

Shared buy/sell menus used by shop packs:

* `amount-selectors/default.yml`
* `bulk-buy/default.yml`
* `bulk-sell/default.yml`
* `purchase-confirmation/default.yml`

Each shop pack can choose which shared menu file it uses.

## webhooks/config.yml

Discord webhook settings.

Keep real webhook URLs private.

Basic setup:

```yaml
enabled: true

channels:
  default:
    url: "https://discord.com/api/webhooks/example/example"
  transactions:
    url: "https://discord.com/api/webhooks/example/example"
  staff:
    url: "https://discord.com/api/webhooks/example/example"
  security:
    url: "https://discord.com/api/webhooks/example/example"
```

Supported event sections in the bundled file:

| Event | Default channel | Description |
| ----- | --------------- | ----------- |
| `purchase` | `transactions` | Buy transactions. |
| `sell` | `transactions` | Sell transactions. |
| `blocked-transaction` | `security` | Blocked transaction events. |
| `reload` | `staff` | Reload command events. |
| `admin-action` | `staff` | Admin shop actions. |
| `cancelled-click` | `security` | Blocked GUI click events. Disabled by default. |

Webhook templates use brace placeholders:

```yaml
description: "**{player}** bought **{amount}x {item}** for **{price} {currency}**."
```

Bundled webhook placeholders:

```text
{player}
{uuid}
{item}
{material}
{amount}
{price}
{unit_price}
{currency}
{shop}
{category}
{reason}
{finding_id}
{action}
{target}
{details}
{click}
{menu}
{result}
{transaction_id}
{server}
{world}
{x}
{y}
{z}
{time}
```

Delivery settings:

```yaml
delivery:
  async: true
  queue-size: 500
  timeout-ms: 5000
  max-retries: 2
  retry-delay-seconds: 10
  log-failures: true
```

Safety settings:

```yaml
security:
  allow-mentions: false
  strip-colors: true
  max-field-length: 1024
  max-fields-per-embed: 25
  auto-split-large-embeds: true

rate-limit:
  enabled: true
  max-events-per-minute: 60
```
