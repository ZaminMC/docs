# PlaceholderAPI

ZaminShop registers a PlaceholderAPI expansion when PlaceholderAPI is installed.

Use placeholders as:

```text
%zaminshop_<placeholder>%
```

Example:

```yaml
profile:
  type: CUSTOM
  material: PLAYER_HEAD
  slot: 4
  display-name: "&b%player_name%"
  lore:
    - "&7Balance: &a%zaminshop_balance%"
    - "&7Favorites: &e%zaminshop_favorites%"
```

## Player Placeholders

| Placeholder | Description |
| ----------- | ----------- |
| `%zaminshop_favorites_count%` | Number of favorite items. |
| `%zaminshop_favorites%` | Alias for favorite count in menu contexts. |
| `%zaminshop_recent_count%` | Recent transaction count in menu contexts. |
| `%zaminshop_recent_bought_count%` | Bought transaction count. |
| `%zaminshop_recent_sold_count%` | Sold transaction count. |
| `%zaminshop_last_transaction_amount%` | Amount from the latest transaction. |
| `%zaminshop_last_transaction_price%` | Price from the latest transaction. |
| `%zaminshop_last_transaction_type%` | Latest transaction type. |

## Menu Placeholders

| Placeholder | Description |
| ----------- | ----------- |
| `%zaminshop_page%` | Current page. |
| `%zaminshop_max_page%` | Max page. |
| `%zaminshop_search_query%` | Current search query. |
| `%zaminshop_search_count%` | Current search result count. |
| `%zaminshop_balance%` | Player balance formatted for menus. |
| `%query%` | Local search query placeholder. |
| `%page%` | Local page placeholder. |
| `%max_page%` | Local max page placeholder. |

## Shop and Item Placeholders

| Placeholder | Description |
| ----------- | ----------- |
| `%zaminshop_shop%` | Current shop ID. |
| `%zaminshop_shop_id%` | Current shop ID. |
| `%zaminshop_shop_name%` | Current shop display name. |
| `%zaminshop_category%` | Current category name. |
| `%zaminshop_category_id%` | Current category ID. |
| `%zaminshop_category_name%` | Current category name. |
| `%zaminshop_current_category%` | Current category name. |
| `%zaminshop_current_category_id%` | Current category ID. |
| `%zaminshop_current_category_name%` | Current category name. |
| `%zaminshop_current_shop%` | Current shop ID. |
| `%zaminshop_current_shop_id%` | Current shop ID. |
| `%zaminshop_current_shop_name%` | Current shop display name. |
| `%zaminshop_item%` | Current item display name. |
| `%zaminshop_item_id%` | Current item ID. |
| `%zaminshop_current_item%` | Current item display name. |
| `%zaminshop_current_item_id%` | Current item ID. |
| `%zaminshop_current_item_name%` | Current item display name. |
| `%zaminshop_material%` | Current item material. |
| `%zaminshop_damage%` | Current item durability/data value. |
| `%zaminshop_buy_price%` | Current buy price. |
| `%zaminshop_sell_price%` | Current sell price. |
| `%zaminshop_buy%` | Current buy price. |
| `%zaminshop_sell%` | Current sell price. |
| `%zaminshop_buyprice%` | Legacy menu placeholder for buy price. |
| `%zaminshop_sellprice%` | Legacy menu placeholder for sell price. |

## Amount Input Placeholders

These are local placeholders used in amount selector menus:

| Placeholder | Description |
| ----------- | ----------- |
| `%amount%` | Current amount. |
| `%quantity%` | Current amount. |
| `%input%` | Current input display value. |
| `%amount_input%` | Current amount input display value. |
| `%currency%` | Selected currency display name. |
| `%cost%` | Current action price. |

## Shop Pack Placeholders

| Placeholder | Description |
| ----------- | ----------- |
| `%zaminshop_current_shop_pack%` | Current shop pack display name. |
| `%zaminshop_current_shop_pack_name%` | Current shop pack display name. |
| `%zaminshop_current_shop_pack_id%` | Current shop pack ID. |

## Validation and Transaction Context

The placeholder context service stores runtime values such as:

```text
%zaminshop_transaction_id%
%zaminshop_reason%
%zaminshop_amount%
%zaminshop_quantity%
%zaminshop_price%
```

These require the relevant transaction or menu context. They are not global static values.

## Language-Backed Placeholders

If a `%zaminshop_*%` placeholder matches a language key, ZaminShop can return the language value.

Example keys in `lang/en_US.yml`:

```text
zaminshop_favorites_title
zaminshop_recent_title
zaminshop_sell_summary_name
```

Use these mainly inside bundled menus and language-driven text.
