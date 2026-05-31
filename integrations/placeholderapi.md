# PlaceholderAPI

ZaminShop registers the PlaceholderAPI identifier:

```text
zaminshop
```

Format:

```text
%zaminshop_<placeholder>%
```

## Direct placeholders

These are handled explicitly by `ZaminShopPlaceholderExpansion`.

| Placeholder | Description | Example |
|---|---|---|
| `%zaminshop_balance%` | Current player balance from the default economy provider | `125,000` |
| `%zaminshop_favorites%` | Favorite item count | `8` |
| `%zaminshop_favoritescount%` | Favorite item count | `8` |
| `%zaminshop_favoritelimit%` | Current favorite limit value returned by source | `-` |
| `%zaminshop_recentcount%` | Total recent entries stored | `12` |
| `%zaminshop_recentboughtcount%` | Recent buy entries | `7` |
| `%zaminshop_recentsoldcount%` | Recent sell entries | `5` |
| `%zaminshop_lasttransactionamount%` | Amount from the latest recent entry | `64` |
| `%zaminshop_lasttransactionprice%` | Price from the latest recent entry | `320` |
| `%zaminshop_lasttransactiontype%` | Latest transaction action | `BUY` |
| `%zaminshop_dailysellmoney%` | Daily earned sell money so far | `1500` |
| `%zaminshop_dailysellmoneylimit%` | Daily sell money limit | `50000` |
| `%zaminshop_dailysellmoneyremaining%` | Daily sell money remaining | `48500` |
| `%zaminshop_weeklysellmoney%` | Weekly earned sell money so far | `9200` |
| `%zaminshop_weeklysellmoneylimit%` | Weekly sell money limit | `500000` |
| `%zaminshop_weeklysellmoneyremaining%` | Weekly sell money remaining | `490800` |
| `%zaminshop_dailyitemssold%` | Daily sold item count | `320` |
| `%zaminshop_dailyitemssoldlimit%` | Daily item sell limit | `50000` |
| `%zaminshop_dailyitemssoldremaining%` | Daily items remaining before limit | `49680` |
| `%zaminshop_weeklyitemssold%` | Weekly sold item count | `2150` |
| `%zaminshop_weeklyitemssoldlimit%` | Weekly item sell limit | `500000` |
| `%zaminshop_weeklyitemssoldremaining%` | Weekly items remaining before limit | `497850` |

## Context placeholders

ZaminShop also exposes context-driven placeholders that are filled while menus, searches, validation, risk output, or transactions are active.

Common examples:

- `%zaminshop_item%`
- `%zaminshop_material%`
- `%zaminshop_buyprice%`
- `%zaminshop_sellprice%`
- `%zaminshop_shopname%`
- `%zaminshop_shopid%`
- `%zaminshop_page%`
- `%zaminshop_query%`
- `%zaminshop_amount%`
- `%zaminshop_quantity%`

These are most useful inside:

- menu titles
- menu lore
- language strings
- validation messages
- transaction messages

## Language fallback

If a placeholder is not handled directly and matches a language key, ZaminShop falls back to:

```text
zaminshop_<placeholder>
```

That means menu text can reuse language keys without writing custom parsing logic in the menu itself.

## Notes

- `%zaminshop_balance%` uses the plugin's default configured economy provider
- context placeholders only return useful values when that context exists
- external placeholders such as `%vault_eco_balance_commas%` still require the external plugin that owns them
