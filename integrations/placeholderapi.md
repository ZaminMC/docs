# PlaceholderAPI

The plugin registers PlaceholderAPI identifier:

```text
zaminshop
```

Format:

```text
%zaminshop_<placeholder>%
```

## Direct placeholders

| Placeholder | Meaning |
|---|---|
| `%zaminshop_dailysellmoney%` | Source-defined PlaceholderAPI value. |
| `%zaminshop_dailysellmoneylimit%` | Source-defined PlaceholderAPI value. |
| `%zaminshop_dailysellmoneyremaining%` | Source-defined PlaceholderAPI value. |
| `%zaminshop_weeklysellmoney%` | Source-defined PlaceholderAPI value. |
| `%zaminshop_weeklysellmoneylimit%` | Source-defined PlaceholderAPI value. |
| `%zaminshop_weeklysellmoneyremaining%` | Source-defined PlaceholderAPI value. |
| `%zaminshop_dailyitemssold%` | Source-defined PlaceholderAPI value. |
| `%zaminshop_dailyitemssoldlimit%` | Source-defined PlaceholderAPI value. |
| `%zaminshop_dailyitemssoldremaining%` | Source-defined PlaceholderAPI value. |
| `%zaminshop_weeklyitemssold%` | Source-defined PlaceholderAPI value. |
| `%zaminshop_weeklyitemssoldlimit%` | Source-defined PlaceholderAPI value. |
| `%zaminshop_weeklyitemssoldremaining%` | Source-defined PlaceholderAPI value. |
| `%zaminshop_favoritescount%` | Source-defined PlaceholderAPI value. |
| `%zaminshop_favorites%` | Source-defined PlaceholderAPI value. |
| `%zaminshop_favoritelimit%` | Source-defined PlaceholderAPI value. |
| `%zaminshop_recentcount%` | Source-defined PlaceholderAPI value. |
| `%zaminshop_recentboughtcount%` | Source-defined PlaceholderAPI value. |
| `%zaminshop_recentsoldcount%` | Source-defined PlaceholderAPI value. |
| `%zaminshop_lasttransactionamount%` | Source-defined PlaceholderAPI value. |
| `%zaminshop_lasttransactionprice%` | Source-defined PlaceholderAPI value. |
| `%zaminshop_lasttransactiontype%` | Source-defined PlaceholderAPI value. |
| `%zaminshop_balance%` | Source-defined PlaceholderAPI value. |

## Context placeholders

These are populated by menus, validation, worth checks, transaction context, and player context.

| Placeholder |
|---|
| `%zaminshop_amount%` |
| `%zaminshop_balance%` |
| `%zaminshop_buy%` |
| `%zaminshop_buypage%` |
| `%zaminshop_buyprice%` |
| `%zaminshop_buyshop%` |
| `%zaminshop_buyshopid%` |
| `%zaminshop_buyslot%` |
| `%zaminshop_category%` |
| `%zaminshop_command%` |
| `%zaminshop_damage%` |
| `%zaminshop_detail%` |
| `%zaminshop_enchantment%` |
| `%zaminshop_errors%` |
| `%zaminshop_gamemode%` |
| `%zaminshop_global%` |
| `%zaminshop_item%` |
| `%zaminshop_itemid%` |
| `%zaminshop_items%` |
| `%zaminshop_level%` |
| `%zaminshop_material%` |
| `%zaminshop_max%` |
| `%zaminshop_menutype%` |
| `%zaminshop_modifier%` |
| `%zaminshop_owned%` |
| `%zaminshop_page%` |
| `%zaminshop_period%` |
| `%zaminshop_permission%` |
| `%zaminshop_player%` |
| `%zaminshop_playerdisplayname%` |
| `%zaminshop_playername%` |
| `%zaminshop_playeruuid%` |
| `%zaminshop_playerworld%` |
| `%zaminshop_playerworldname%` |
| `%zaminshop_prefix%` |
| `%zaminshop_price%` |
| `%zaminshop_purchasable%` |
| `%zaminshop_quantity%` |
| `%zaminshop_query%` |
| `%zaminshop_reason%` |
| `%zaminshop_remainingitems%` |
| `%zaminshop_remainingmoney%` |
| `%zaminshop_riskid%` |
| `%zaminshop_sell%` |
| `%zaminshop_sellable%` |
| `%zaminshop_sellall%` |
| `%zaminshop_sellpage%` |
| `%zaminshop_sellprice%` |
| `%zaminshop_sellshop%` |
| `%zaminshop_sellshopid%` |
| `%zaminshop_sellslot%` |
| `%zaminshop_severity%` |
| `%zaminshop_shop%` |
| `%zaminshop_shopid%` |
| `%zaminshop_shopname%` |
| `%zaminshop_shops%` |
| `%zaminshop_skippeditems%` |
| `%zaminshop_skippedshops%` |
| `%zaminshop_transactionid%` |
| `%zaminshop_type%` |
| `%zaminshop_usage%` |
| `%zaminshop_warnings%` |
| `%zaminshop_world%` |

## Language fallback

If a placeholder is not directly handled, the expansion checks language key:

```text
zaminshop_<placeholder>
```
