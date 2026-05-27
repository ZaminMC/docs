# Language System

Default language file:

```text
lang/en_US.yml
```

## Language metadata

```yaml
LANGUAGE:
  CODE: "en_US"
  NAME: "English"
  AUTHOR: "Zamin"
PREFIX: "&aZaminShop > &f"
```

## Important message groups

- General messages
- Validation
- Risk guard
- Search / recent / favorites
- Language
- Help
- Command usage
- Modifier commands
- Worth/check command messages
- Shop transaction messages
- Placeholder text used by GUI items

## Real language keys

| Key | Default |
|---|---|
| `LANGUAGE.CODE` | `en_US` |
| `LANGUAGE.NAME` | `English` |
| `LANGUAGE.AUTHOR` | `Zamin` |
| `PREFIX` | `&aZaminShop > &f` |
| `LANG.CONSOLE` | `Console` |
| `MSG.AND` | ` and ` |
| `MSG.ERROR` | `An internal error occurred. Ask the server owner to review the console for details.` |
| `MSG.INGAMEONLY` | `Only in-game players can run this command.` |
| `MSG.NOACCESS` | `You do not have permission to do that.` |
| `MSG.NOTLOADED` | `ZaminShop is still starting up. Please try again in a moment.` |
| `MSG.STARTUPFAILED` | `ZaminShop failed to finish startup. Check the server log and fix the reported shop or conf` |
| `MSG.RELOADED` | `ZaminShop configuration reloaded.` |
| `MSG.RELOADFAILED` | `ZaminShop could not finish reloading. Check the server log for the reported configuration ` |
| `MSG.USAGE.SUBCOMMAND` | `Invalid command usage. Use: %usage%` |
| `MSG.VALIDATE.OK` | `Validation complete. %shops% shops and %items% items are valid. No shop load errors were f` |
| `MSG.VALIDATE.ISSUES` | `Validation complete. %shops% shops and %items% items are valid. Skipped %skippedShops% sho` |
| `MSG.VALIDATE.DETAIL` | `&7- %severity%: %detail%` |
| `MSG.RISK.BLOCKED.SHOP` | `This shop is blocked by risk guard. Review risk %riskId% before opening it.` |
| `MSG.RISK.BLOCKED.ITEM` | `This item is blocked by risk guard. Review risk %riskId% before using it.` |
| `MSG.RISK.ITEM.DISABLED.LORE` | `&cTemporarily disabled.` |
| `MSG.RISK.LIST.EMPTY` | `No active economy risks are currently blocking the shop.` |
| `MSG.RISK.LIST.ENTRY` | `&7[%level%]&f %riskId% &8/&f shop=%shop% item=%item% material=%material% buy=%buy% sell=%s` |
| `MSG.RISK.CONFIRM.OK` | `Risk %riskId% confirmed. The current config fingerprint is now allowed.` |
| `MSG.RISK.CONFIRM.UNKNOWN` | `Risk %riskId% was not found.` |
| `MSG.RISK.RESET.OK` | `Risk confirmations were cleared. Current risks will require confirmation again.` |
| `MSG.SEARCH.DISABLED` | `Shop search is disabled.` |
| `MSG.SEARCH.NO.RESULTS` | `No shop items matched &c%query%&f.` |
| `MSG.RECENT.DISABLED` | `Recent transactions are disabled.` |
| `MSG.RECENT.EMPTY` | `You do not have any recent transactions yet.` |
| `MSG.FAVORITES.EMPTY` | `You do not have any favorite items yet.` |
| `MSG.FAVORITE.ADDED` | `Added &c%item%&f to favorites.` |
| `MSG.FAVORITE.REMOVED` | `Removed &c%item%&f from favorites.` |
| `MSG.LANGUAGE.HEADER` | `Available languages:` |
| `MSG.LANGUAGE.RELOADED` | `Language files reloaded.` |
| `MSG.LANGUAGE.CHANGED` | `Language changed to &c%language%&f.` |
| `MSG.LANGUAGE.UNKNOWN` | `Language &c%language%&f is not available.` |
| `MSG.LANGUAGE.ALREADY.ACTIVE` | `Language &c%language%&f is already active.` |
| `HELP.COMMANDS.PER.PAGE` | `5` |
| `HELP.NEXT.BUTTON` | `&a[Next]` |
| `HELP.PREVIOUS.BUTTON` | `&c[Previous]` |
| `HELP.HEADER` | `['&a━━━━━━━━━━━━━━━━━━━━', '&a&lZaminShop &fHelp &7(%page%/%max_page%)', '&a━━━━━━━━━━━━━━` |
| `HELP.FOOTER` | `['&a━━━━━━━━━━━━━━━━━━━━']` |
| `HELP.PLAYER` | `['/shop :: Open shop menu', '/shop help :: Show player help', '/shop favorite :: Open favo` |
| `HELP.ADMIN` | `['/zaminshop help :: Show admin help', '/zaminshop reload :: Reload plugin', '/zaminshop v` |
| `MSG.CMD.ZAMINSHOP.SEARCH.USAGE` | `/shop search <query>` |
| `MSG.CMD.ZAMINSHOP.RECENT.USAGE` | `/shop recent` |
| `MSG.CMD.ZAMINSHOP.FAVORITES.USAGE` | `/shop favorites` |
| `MSG.CMD.ZAMINSHOP.ADDMODIFIER.ITEM.USAGE` | `/zaminshop addmodifier item <player> <shop> <item> <value> [buy/sell]` |
| `MSG.CMD.ZAMINSHOP.ADDMODIFIER.SHOP.USAGE` | `/zaminshop addmodifier shop <player> <shop> <value> [buy/sell]` |
| `MSG.CMD.ZAMINSHOP.ADDMODIFIER.GLOBAL.USAGE` | `/zaminshop addmodifier global <player> <value> [buy/sell]` |
| `MSG.CMD.ZAMINSHOP.RESETMODIFIER.ITEM.USAGE` | `/zaminshop resetmodifier item <player> <shop> <item> [buy/sell]` |
| `MSG.CMD.ZAMINSHOP.RESETMODIFIER.SHOP.USAGE` | `/zaminshop resetmodifier shop <player> <shop> [buy/sell]` |
| `MSG.CMD.ZAMINSHOP.RESETMODIFIER.GLOBAL.USAGE` | `/zaminshop resetmodifier global <player> [buy/sell]` |
| `MSG.CMD.ZAMINSHOP.ADDMODIFIER.ITEM.ADDED` | `Set &c%player%&f's %type% modifier for %item% in %shop% to &c%modifier%&f.` |
| `MSG.CMD.ZAMINSHOP.ADDMODIFIER.ITEM.ADDEDBY` | `&c%player%&f set your %type% modifier for %item% in %shop% to &c%modifier%&f.` |
| `MSG.CMD.ZAMINSHOP.ADDMODIFIER.SHOP.ADDED` | `Set &c%player%&f's %type% modifier for every item in %shop% to &c%modifier%&f.` |
| `MSG.CMD.ZAMINSHOP.ADDMODIFIER.SHOP.ADDEDBY` | `&c%player%&f set your %type% modifier for every item in %shop% to &c%modifier%&f.` |
| `MSG.CMD.ZAMINSHOP.ADDMODIFIER.GLOBAL.ADDED` | `Set &c%player%&f's global %type% modifier to &c%modifier%&f.` |
| `MSG.CMD.ZAMINSHOP.ADDMODIFIER.GLOBAL.ADDEDBY` | `&c%player%&f set your global %type% modifier to &c%modifier%&f.` |
| `MSG.CMD.ZAMINSHOP.CHECKMODIFIERS.VIEW` | `Command modifiers for &c%player%&f:
Global modifiers:
%global%
Shop modifiers:
%shop%
Item` |
| `MSG.CMD.ZAMINSHOP.CHECKMODIFIERS.PERMISSION.VIEW` | `Permission modifiers for &c%player%&f:
Global modifiers:
%global%Shop modifiers:
%shop%
It` |
| `MSG.CMD.ZAMINSHOP.CHECKMODIFIERS.ENTRY.ITEM` | `&7Item &c%item%&7 in &c%shop%&7: buy=&c%buy%&7, sell=&c%sell%` |
| `MSG.CMD.ZAMINSHOP.CHECKMODIFIERS.ENTRY.SHOP` | `&7Shop &c%shop%&7: buy=&c%buy%&7, sell=&c%sell%` |
| `MSG.CMD.ZAMINSHOP.CHECKMODIFIERS.ENTRY.GLOBAL` | `&7Global: buy=&c%buy%&7, sell=&c%sell%` |
| `MSG.CMD.ZAMINSHOP.RESETMODIFIER.ITEM.RESET` | `Cleared &c%player%&f's %type% modifier for %item% in %shop%.` |
| `MSG.CMD.ZAMINSHOP.RESETMODIFIER.ITEM.RESETBY` | `&c%player%&f cleared your %type% modifier for %item% in %shop%.` |
| `MSG.CMD.ZAMINSHOP.RESETMODIFIER.SHOP.RESET` | `Cleared &c%player%&f's %type% modifier for every item in %shop%.` |
| `MSG.CMD.ZAMINSHOP.RESETMODIFIER.SHOP.RESETBY` | `&c%player%&f cleared your %type% modifier for every item in %shop%.` |
| `MSG.CMD.ZAMINSHOP.RESETMODIFIER.GLOBAL.RESET` | `Cleared &c%player%&f's global %type% modifier.` |
| `MSG.CMD.ZAMINSHOP.RESETMODIFIER.GLOBAL.RESETBY` | `&c%player%&f cleared your global %type% modifier.` |
| `MSG.MODIFIER.INVALIDAMOUNT` | `Modifier value must be a decimal multiplier, such as 0.5 for half price or 2.0 for double ` |
| `MSG.MODIFIER.INVALIDTYPE` | `Modifier type must be buy, sell, or both.` |
| `MSG.MODIFIER.BUY` | `buy` |
| `MSG.MODIFIER.SELL` | `sell` |
| `MSG.MODIFIER.BOTH` | `buy & sell` |
| `MSG.CMD.ZAMINSHOP.CHECK.ITEM` | `Held item material: &c%material%&f, damage: &c%damage%&f.` |
| `MSG.CMD.ZAMINSHOP.CHECK.NOITEM` | `Hold an item first, then run the check command again.` |
| `MSG.CMD.ZAMINSHOP.WORTH.NOITEM` | `Hold an item first, then run the worth command again.` |
| `MSG.CMD.ZAMINSHOP.WORTH.NOTFOUND` | `No shop entry matches the item in your hand.` |
| `MSG.CMD.ZAMINSHOP.WORTH.FOUND` | `This item is currently %purchasable%&f and %sellable%&f.` |
| `MSG.CMD.ZAMINSHOP.WORTH.FOUNDPURCHASEABLE` | `buyable for &a%buyprice%&f in &a%buyShopId%` |
| `MSG.CMD.ZAMINSHOP.WORTH.FOUNDSELLABLE` | `sellable for &a%sellprice%&f in &a%sellShopId%` |
| `MSG.CMD.ZAMINSHOP.WORTH.FOUNDNOTPURCHASEABLE` | `not buyable` |
| `MSG.CMD.ZAMINSHOP.WORTH.FOUNDNOTSELLABLE` | `not accepted for selling` |
| `MSG.MISSINGPLAYER` | `Missing player name. Usage: %usage%` |
| `MSG.INVALIDPLAYER` | `That player could not be found.` |
| `MSG.INVALIDSHOP` | `No shop exists with ID &c%shop%&f.` |
| `MSG.INVALIDPAGE` | `Page &c%page%&f is not available for shop &c%shop%&f.` |
| `MSG.INVALIDITEM` | `Shop &c%shop%&f does not contain item &c%item%&f.` |
| `MSG.NOACCESSTOSHOP` | `You are not allowed to open &c%shop%&f.` |
| `MSG.NODIRECTACCESSTOSHOP` | `&c%shop%&f cannot be opened directly.` |
| `MSG.MAIN.MENU.DISABLED` | `The shop directory is disabled. Use /zaminshop <shop> instead.` |
| `MSG.WORLDBLACKLISTED` | `%shop% is not available in this world.` |
| `MSG.WORLDBANNED` | `The shop is not available in this world.` |
| `MSG.WORLDBANNEDTARGET` | `%player% cannot use the shop in that world.` |
| `MSG.GAMEMODEBANNED` | `The shop is not available while you are in %gamemode%.` |
| `MSG.GAMEMODEBANNEDTARGET` | `%player% cannot use the shop while in %gamemode%.` |
| `MSG.ITEM.FULLINVENTORY` | `Make more inventory space before buying this item.` |
| `MSG.ITEM.CANNOTAFFORD` | `You need &c%price%&f for &c%amount% x %item%&f.` |
| `MSG.ITEM.CANNOTBUY` | `This item is not available for purchase.` |
| `MSG.ITEM.CANNOTSELL` | `This item is not accepted for selling.` |
| `MSG.ITEM.BOUGHT` | `Purchased &c%amount% x %item%&f for &c%price%&f.` |
| `MSG.ITEM.BOUGHTFREE` | `Received &c%amount% x %item%&f.` |
| `MSG.ITEM.NOTENOUGH` | `You need &c%amount% x %item%&f to complete this sale.` |
| `MSG.ITEM.SOLD` | `Sold &a%amount% x %item%&f for &a%price%&f.` |
| `MSG.ITEM.SOLDFREE` | `Removed &a%amount% x %item%&f.` |
| `MSG.ITEM.SOLDALL` | `Sold all matching &a%item%&f (&a%amount% total&f) for &a%price%&f.` |
| `MSG.ITEM.SOLDALLFREE` | `Removed all matching &a%item%&f (&a%amount% total&f).` |
| `MSG.SELL.LIMIT.REACHED` | `You reached the %period% sell limit for this item. Remaining money: &c%remaining_money%&f,` |
| `MSG.SUSPICIOUS.SELL.BLOCKED` | `Selling is temporarily blocked due to suspicious activity checks. Please wait and try agai` |
| `MSG.ITEM.NOACCESS` | `You are not allowed to use this item.` |
| `MSG.ENCHANT.CANNOTAPPLY` | `&c%enchantment%&f cannot be applied to the item in your hand.` |
| `MSG.ENCHANT.ALREADYAPPLIED` | `The item already has &c%enchantment%&f.` |
| `MSG.ENCHANT.LEVELDIFF` | `The item must already have &c%enchantment% %level%&f or higher.` |
| `MSG.ENCHANT.CANNOTAFFORD` | `You need &c%price%&f for &c%enchantment%&f.` |
| `MSG.ENCHANT.MAX` | `This item has reached its enchantment limit (%amount%).` |
| `MSG.ENCHANT.TOOMANY` | `You may enchant at most %amount% items at once.` |
| `MSG.ENCHANT.BOUGHT` | `Purchased &c%enchantment%&f for &c%price%&f.` |
| `MSG.ENCHANT.BOUGHTFREE` | `Received &c%enchantment%&f.` |
| `MSG.PERMISSION.PERMISSIONSDISABLED` | `Permission purchases are unavailable on this server.` |
| `MSG.PERMISSION.ALREADYHAVE` | `You already own &c%permission%&f.` |
| `MSG.PERMISSION.CANNOTAFFORD` | `You need &c%price%&f for &c%permission%&f.` |
| `MSG.PERMISSION.BOUGHT` | `Purchased &c%permission%&f for &c%price%&f.` |
| `MSG.PERMISSION.BOUGHTFREE` | `Received &c%permission%&f.` |
| `MSG.COMMAND.BOUGHT` | `Purchased command &c%command%&f for &c%price%&f.` |
| `MSG.COMMAND.BOUGHTFREE` | `Received command &c%command%&f.` |
| `MSG.COMMAND.CANNOTAFFORD` | `You need &c%price%&f for command &c%command%&f.` |
| `MSG.SELLHAND.NOITEM` | `Hold the item you want to sell, then try again.` |
| `MSG.SELLHAND.INVALIDQUANTITY` | `Quantity must be between 1 and %max%.` |
| `MSG.SELLHAND.CANNOTSELL` | `The item in your hand cannot be sold.` |
| `MSG.SELLHAND.MULTIPLEQUANTITYONLY` | `This item can only be sold in multiples of %quantity%.` |
| `MSG.SELLHANDALL.SOLD` | `Sold &a%quantity% x %item%&f for &a%price%&f total.` |
| `MSG.SELLALL.NOITEMS` | `No sellable items were found in your inventory.` |
| `MSG.SELLALL.NOITEMSOTHER` | `No sellable items were found for %player%.` |
| `MSG.SELLALL.SOLD` | `Sold &a%quantity% items&f for &a%price%&f total.` |
| `MSG.SELLALL.SOLDOTHER` | `&a%player% &fsold &a%quantity% items&f for &a%price%&f total.` |
| `MSG.SELLALL.INVALIDSHOP` | `That shop cannot be used for sell-all.` |
| `DIALOG.FAVORITES.NAME` | `&8Favorite items` |
| `DIALOG.RECENT.NAME` | `&8Recent transactions` |
| `DIALOG.SEARCH.RESULTS.NAME` | `&8Search: %query%` |
| `DIALOG.AMOUNTSELECTION.BUY.NAME` | `&2Buy %item%` |
| `DIALOG.AMOUNTSELECTION.SELL.NAME` | `&cSell %item%` |
| `DIALOG.AMOUNTSELECTION.BULKBUY.NAME` | `&cBulk buy %item%` |
| `DIALOG.AMOUNTSELECTION.BULKSELL.NAME` | `&cBulk sell %item%` |
| `SHOP.PERMISSION.ALREADYOWNED` | `&4(Owned)` |
| `SHOP.PERMISSION.NOTOWNED` | `&a(Available)` |
| `MSG.NUMBERFORMAT.SHORTSCALE.THOUSAND` | ` Thousand` |
| `MSG.NUMBERFORMAT.SHORTSCALE.MILLION` | ` Million` |
| `MSG.NUMBERFORMAT.SHORTSCALE.BILLION` | ` Billion` |
| `MSG.NUMBERFORMAT.SHORTSCALE.TRILLION` | ` Trillion` |
| `MSG.NUMBERFORMAT.SHORTSCALE.QUADRILLION` | ` quadrillion` |
| `MSG.NUMBERFORMAT.SHORTSCALE.QUINTILLION` | ` quintillion` |
| `MSG.NUMBERFORMAT.SHORTSCALE.SEXTILLION` | ` Sextillion` |
| `MSG.NUMBERFORMAT.SHORTSCALE.SEPTILLION` | ` Septillion` |
| `MSG.NUMBERFORMAT.SHORTSCALE.OCTILLION` | ` Octillion` |
| `MSG.NUMBERFORMAT.SHORTSCALE.NONILLION` | ` Nonillion` |
| `MSG.NUMBERFORMAT.SHORTSCALE.DECILLION` | ` Decillion` |
| `zaminshop_bulk_buy` | `Bulk Buy` |
| `zaminshop_bulk_buy_1` | `&aBuy 1 stack` |
| `zaminshop_bulk_buy_2` | `&aBuy 2 stacks` |
