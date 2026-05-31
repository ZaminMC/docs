# PlaceholderAPI

ZaminShop includes a PlaceholderAPI expansion so your menus, messages, and other plugin text can show live shop-related values.

## Identifier

```text
zaminshop
```

Format:

```text
%zaminshop_<placeholder>%
```

## What you can use it for

PlaceholderAPI becomes most useful when you want to show:

- player balance
- favorite counts
- recent history counts
- sell-limit progress
- current item or shop context inside menus

## Direct placeholders

These placeholders are handled explicitly by the ZaminShop expansion:

| Placeholder | Meaning |
|---|---|
| `%zaminshop_balance%` | Current player balance from the default economy provider |
| `%zaminshop_favorites%` | Favorite item count |
| `%zaminshop_favoritescount%` | Favorite item count |
| `%zaminshop_favoritelimit%` | Current favorite limit value returned by source |
| `%zaminshop_recentcount%` | Total recent entries stored |
| `%zaminshop_recentboughtcount%` | Recent buy entries |
| `%zaminshop_recentsoldcount%` | Recent sell entries |
| `%zaminshop_lasttransactionamount%` | Amount from the latest recent entry |
| `%zaminshop_lasttransactionprice%` | Price from the latest recent entry |
| `%zaminshop_lasttransactiontype%` | Latest transaction action |
| `%zaminshop_dailysellmoney%` | Daily earned sell money so far |
| `%zaminshop_dailysellmoneylimit%` | Daily sell money limit |
| `%zaminshop_dailysellmoneyremaining%` | Daily sell money remaining |
| `%zaminshop_weeklysellmoney%` | Weekly earned sell money so far |
| `%zaminshop_weeklysellmoneylimit%` | Weekly sell money limit |
| `%zaminshop_weeklysellmoneyremaining%` | Weekly sell money remaining |
| `%zaminshop_dailyitemssold%` | Daily sold item count |
| `%zaminshop_dailyitemssoldlimit%` | Daily item sell limit |
| `%zaminshop_dailyitemssoldremaining%` | Daily items remaining before limit |
| `%zaminshop_weeklyitemssold%` | Weekly sold item count |
| `%zaminshop_weeklyitemssoldlimit%` | Weekly item sell limit |
| `%zaminshop_weeklyitemssoldremaining%` | Weekly items remaining before limit |

## Context placeholders

ZaminShop also fills context-driven placeholders while a relevant menu, transaction, validation run, or search flow is active.

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

These are especially useful inside:

- menu titles
- menu lore
- language-backed GUI labels
- validation and transaction messages

## Language fallback

If a placeholder is not handled directly and matches a language key, ZaminShop falls back to:

```text
zaminshop_<placeholder>
```

This is why some GUI text can stay in the language file while still behaving like a placeholder-backed label.

## Practical advice

Use PlaceholderAPI for values that actually help the player make decisions:

- current balance
- buy and sell values
- favorite counts
- search query feedback

Do not overload every lore block just because the placeholders exist.
