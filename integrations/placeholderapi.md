---
description: Complete reference for ZaminShop's PlaceholderAPI expansion and runtime context values.
---

# PlaceholderAPI

When PlaceholderAPI is installed, ZaminShop registers the persistent `zaminshop` expansion.

Use placeholders as:

```text
%zaminshop_<identifier>%
```

Identifiers are normalized by removing punctuation and underscores and ignoring case. For readability, this page uses underscores.

## Always available for a player

| Placeholder | Value |
| --- | --- |
| `%zaminshop_player%` | Player name |
| `%zaminshop_player_name%` | Player name |
| `%zaminshop_player_display_name%` | Bukkit display name |
| `%zaminshop_player_uuid%` | UUID |
| `%zaminshop_player_world%` | World name |
| `%zaminshop_player_world_name%` | World name |
| `%zaminshop_world%` | World name |
| `%zaminshop_gamemode%` | Lowercase game mode |
| `%zaminshop_balance%` | Formatted balance of the default economy |
| `%zaminshop_prefix%` | Configured ZaminShop language prefix |

## Favorites and recent transactions

| Placeholder | Value when unavailable |
| --- | --- |
| `%zaminshop_favorites%` | `0` |
| `%zaminshop_favorites_count%` | `0` |
| `%zaminshop_favorite_limit%` | `-` |
| `%zaminshop_recent_count%` | `0` |
| `%zaminshop_recent_bought_count%` | `0` |
| `%zaminshop_recent_sold_count%` | `0` |
| `%zaminshop_last_transaction_amount%` | `0` |
| `%zaminshop_last_transaction_price%` | `0` |
| `%zaminshop_last_transaction_type%` | empty |

`last_transaction_type` is the action enum name, such as `BUY` or `SELL`.

## Sell limits

| Placeholder |
| --- |
| `%zaminshop_daily_sell_money%` |
| `%zaminshop_daily_sell_money_limit%` |
| `%zaminshop_daily_sell_money_remaining%` |
| `%zaminshop_weekly_sell_money%` |
| `%zaminshop_weekly_sell_money_limit%` |
| `%zaminshop_weekly_sell_money_remaining%` |
| `%zaminshop_daily_items_sold%` |
| `%zaminshop_daily_items_sold_limit%` |
| `%zaminshop_daily_items_sold_remaining%` |
| `%zaminshop_weekly_items_sold%` |
| `%zaminshop_weekly_items_sold_limit%` |
| `%zaminshop_weekly_items_sold_remaining%` |

These return `0` when a sell-limit snapshot is unavailable.

## Current menu and shop context

The following values depend on the menu the player most recently opened or the transaction context most recently recorded:

| Placeholder | Meaning |
| --- | --- |
| `%zaminshop_menu_type%` | Current menu type |
| `%zaminshop_page%` | Current page |
| `%zaminshop_query%` | Current search query |
| `%zaminshop_shop%` | Shop ID |
| `%zaminshop_shop_id%` | Shop ID |
| `%zaminshop_shop_name%` | Display name |
| `%zaminshop_category%` | Formatted category name |
| `%zaminshop_category_id%` | Local category ID |
| `%zaminshop_category_name%` | Formatted category name |
| `%zaminshop_current_category%` | Formatted category name |
| `%zaminshop_current_category_id%` | Local category ID |
| `%zaminshop_current_category_name%` | Formatted category name |
| `%zaminshop_current_shop%` | Shop ID |
| `%zaminshop_current_shop_id%` | Shop ID |
| `%zaminshop_current_shop_name%` | Display name |
| `%zaminshop_current_shop_pack%` | Pack display name |
| `%zaminshop_current_shop_pack_name%` | Pack display name |
| `%zaminshop_current_shop_pack_id%` | Pack folder name |

Without current context, these values are empty.

## Current item and transaction context

| Placeholder | Meaning |
| --- | --- |
| `%zaminshop_item%` | Formatted item name |
| `%zaminshop_item_id%` | Shop item ID |
| `%zaminshop_current_item%` | Formatted item name |
| `%zaminshop_current_item_id%` | Shop item ID |
| `%zaminshop_current_item_name%` | Formatted item name |
| `%zaminshop_amount%` | Selected or transacted amount |
| `%zaminshop_quantity%` | Selected or transacted amount |
| `%zaminshop_price%` | Formatted transaction price |
| `%zaminshop_buy%` | Formatted unit buy price |
| `%zaminshop_buy_price%` | Formatted unit buy price |
| `%zaminshop_sell%` | Formatted unit sell price |
| `%zaminshop_sell_price%` | Formatted unit sell price |
| `%zaminshop_material%` | Bukkit material name |
| `%zaminshop_damage%` | Item durability/damage value exposed by the context service |
| `%zaminshop_transaction_id%` | Current transaction ID |
| `%zaminshop_reason%` | Current reason text |
| `%zaminshop_command%` | Command-product display value |
| `%zaminshop_permission%` | Permission-product display value |
| `%zaminshop_owned%` | Permission ownership context; currently stored as an empty value by the item context updater |
| `%zaminshop_enchantment%` | Enchantment name |
| `%zaminshop_level%` | Enchantment level |

## Current currency context

| Placeholder | Meaning |
|---|---|
| `%zaminshop_currency_id%` | Selected provider ID |
| `%zaminshop_currency_name%` | Provider display name |
| `%zaminshop_currency_balance%` | Formatted balance for the selected provider |
| `%zaminshop_currency_icon%` | Configured provider icon material |
| `%zaminshop_currency_description%` | Provider description joined into one line |

## Other registered context identifiers

The expansion also accepts these context keys when another ZaminShop flow has populated them:

```text
buy_page, buy_shop, buy_shop_id, buy_slot,
detail, errors, global, max, modifier, period,
purchasable, remaining_items, remaining_money,
finding_id, sell_all, sell_page, sell_shop, sell_shop_id,
sell_slot, sellable, severity, skipped_items,
skipped_shops, shops, items, type, usage, warnings
```

**Needs verification in code for a particular screen:** these identifiers are
accepted by `ZaminShopPlaceholderExpansion`, but their value is only useful
after another command or menu flow has populated
`PlaceholderContextService`. The current automatic startup validation path does
not expose a documented player placeholder workflow for the validation-related
keys.

## Language-backed placeholders

If an identifier is not one of the direct values above, ZaminShop checks the language manager for:

```text
zaminshop_<identifier>
```

The exact available language-backed identifiers therefore follow the active language resources.

## External PlaceholderAPI placeholders

ZaminShop also applies PlaceholderAPI to supported menu and item text. For example, with a compatible Vault expansion installed:

```yaml
display-name: "&fBalance: &a%vault_eco_balance_commas%"
```

That identifier belongs to the external expansion, not ZaminShop.

## Context warning

Context placeholders describe the player's latest ZaminShop menu or transaction state. Do not use them as permanent database fields. Open the relevant menu before testing them.
