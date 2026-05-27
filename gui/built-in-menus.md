# Built-in Menus

## `amount-selector.yml`

```yaml
menu_title: "&8Amount Selector"
size: 54

items:
  filler:
    type: CUSTOM
    material: BLACK_STAINED_GLASS_PANE
    slots:
      - 0-53
    display-name: " "
    priority: 999

  selected-item:
    type: SHOP_ITEM
    slot: 22
    priority: 1

  set1:
    type: CUSTOM
    material: RED_STAINED_GLASS_PANE
    amount: 1
    slot: 18
    display-name: "&c&lSet to 1"

  remove10:
    type: CUSTOM
    material: RED_STAINED_GLASS_PANE
    amount: 10
    slot: 19
    display-name: "&c&lRemove 10"

  remove1:
    type: CUSTOM
    material: RED_STAINED_GLASS_PANE
    amount: 1
    slot: 20
    display-name: "&c&lRemove 1"

  add1:
    type: CUSTOM
    material: LIME_STAINED_GLASS_PANE
    amount: 1
    slot: 24
    display-name: "&a&lAdd 1"

  add10:
    type: CUSTOM
    material: LIME_STAINED_GLASS_PANE
    amount: 10
    slot: 25
    display-name: "&a&lAdd 10"

  set16:
    type: CUSTOM
    material: LIME_STAINED_GLASS_PANE
    amount: 16
    slot: 26
    display-name: "&a&lSet to 16"

  set64:
    type: CUSTOM
    material: LIME_STAINED_GLASS_PANE
    amount: 64
    slot: 27
    display-name: "&a&lSet to 64"

  confirm:
    type: CUSTOM
    material: GREEN_STAINED_GLASS
    amount: 1
    slot: 39
    display-name: "&a&lConfirm"

  sellAll:
    type: CUSTOM
    material: GREEN_STAINED_GLASS
    amount: 1
    slot: 40
    display-name: "&a&lSell all"

  cancel:
    type: CUSTOM
    material: RED_STAINED_GLASS
    amount: 1
    slot: 41
    display-name: "&c&lCancel"

  buyMore:
    type: CUSTOM
    material: CHEST
    amount: 1
    slot: 35
    display-name: "&a&lBuy more"

  sellMore:
    type: CUSTOM
    material: CHEST
    amount: 1
    slot: 49
    display-name: "&a&lSell more"
```


## `bulk-buy.yml`

```yaml
menu_title: "&8Bulk Buy"
size: 18

items:
  filler:
    type: CUSTOM
    material: BLACK_STAINED_GLASS_PANE
    slots:
      - 0-17
    display-name: " "
    priority: 999

  buy1:
    type: CUSTOM
    material: CHEST
    amount: 1
    slot: 0
    display-name: "&aBuy 1 stack"
    lore:
      - "&7Price: &c%buy%"
    value: 1

  buy2:
    type: CUSTOM
    material: CHEST
    amount: 2
    slot: 1
    display-name: "&aBuy 2 stacks"
    lore:
      - "&7Price: &c%buy%"
    value: 2

  buy3:
    type: CUSTOM
    material: CHEST
    amount: 3
    slot: 2
    display-name: "&aBuy 3 stacks"
    lore:
      - "&7Price: &c%buy%"
    value: 3

  buy4:
    type: CUSTOM
    material: CHEST
    amount: 4
    slot: 3
    display-name: "&aBuy 4 stacks"
    lore:
      - "&7Price: &c%buy%"
    value: 4

  buy5:
    type: CUSTOM
    material: CHEST
    amount: 5
    slot: 4
    display-name: "&aBuy 5 stacks"
    lore:
      - "&7Price: &c%buy%"
    value: 5

  buy6:
    type: CUSTOM
    material: CHEST
    amount: 6
    slot: 5
    display-name: "&aBuy 6 stacks"
    lore:
      - "&7Price: &c%buy%"
    value: 6

  buy7:
    type: CUSTOM
    material: CHEST
    amount: 7
    slot: 6
    display-name: "&aBuy 7 stacks"
    lore:
      - "&7Price: &c%buy%"
    value: 7

  buy8:
    type: CUSTOM
    material: CHEST
    amount: 8
    slot: 7
    display-name: "&aBuy 8 stacks"
    lore:
      - "&7Price: &c%buy%"
    value: 8

  buy9:
    type: CUSTOM
    material: CHEST
    amount: 9
    slot: 8
    display-name: "&aBuy 9 stacks"
    lore:
      - "&7Price: &c%buy%"
    value: 9

  cancel:
    type: CUSTOM
    material: RED_STAINED_GLASS
    amount: 1
    slot: 13
    display-name: "&c&lCancel"
```


## `bulk-sell.yml`

```yaml
menu_title: "&8Bulk Sell"
size: 18

items:
  filler:
    type: CUSTOM
    material: BLACK_STAINED_GLASS_PANE
    slots:
      - 0-17
    display-name: " "
    priority: 999

  sell1:
    type: CUSTOM
    material: CHEST
    amount: 1
    slot: 0
    display-name: "&aSell 1 stack"
    lore:
      - "&7Price: &c%sell%"
    value: 1

  sell2:
    type: CUSTOM
    material: CHEST
    amount: 2
    slot: 1
    display-name: "&aSell 2 stacks"
    lore:
      - "&7Price: &c%sell%"
    value: 2

  sell3:
    type: CUSTOM
    material: CHEST
    amount: 3
    slot: 2
    display-name: "&aSell 3 stacks"
    lore:
      - "&7Price: &c%sell%"
    value: 3

  sell4:
    type: CUSTOM
    material: CHEST
    amount: 4
    slot: 3
    display-name: "&aSell 4 stacks"
    lore:
      - "&7Price: &c%sell%"
    value: 4

  sell5:
    type: CUSTOM
    material: CHEST
    amount: 5
    slot: 4
    display-name: "&aSell 5 stacks"
    lore:
      - "&7Price: &c%sell%"
    value: 5

  sell6:
    type: CUSTOM
    material: CHEST
    amount: 6
    slot: 5
    display-name: "&aSell 6 stacks"
    lore:
      - "&7Price: &c%sell%"
    value: 6

  sell7:
    type: CUSTOM
    material: CHEST
    amount: 7
    slot: 6
    display-name: "&aSell 7 stacks"
    lore:
      - "&7Price: &c%sell%"
    value: 7

  sell8:
    type: CUSTOM
    material: CHEST
    amount: 8
    slot: 7
    display-name: "&aSell 8 stacks"
    lore:
      - "&7Price: &c%sell%"
    value: 8

  sell9:
    type: CUSTOM
    material: CHEST
    amount: 9
    slot: 8
    display-name: "&aSell 9 stacks"
    lore:
      - "&7Price: &c%sell%"
    value: 9

  cancel:
    type: CUSTOM
    material: RED_STAINED_GLASS
    amount: 1
    slot: 13
    display-name: "&c&lCancel"
```


## `favorites.yml`

```yaml
menu_title: "&8Favorite Items"
size: 45

pagination:
  mode: Fancy
  item-slots:
    single-page:
      - 9-17
      - 18-26
    first-page:
      - 9-17
      - 18-26
    middle-page:
      - 9-17
      - 18-26
    last-page:
      - 9-17
      - 18-26

items:
  filler:
    type: CUSTOM
    material: GRAY_STAINED_GLASS_PANE
    display-name: "&f"
    slots:
      - 0-8
      - 27-36
      - 37
      - 43-44
    priority: 100

  sort:
    type: SORT_CYCLE
    slot: 38
    default: FAVORITE_RECENT
    modes:
      - FAVORITE_RECENT
      - MOST_BOUGHT
      - CHEAPEST
      - MOST_EXPENSIVE
      - ALPHABETICAL
    current:
      FAVORITE_RECENT:
        material: HOPPER
        display-name: "&e&lSort"
        lore:
          - "&8Newest favorite items first."
          - "&r"
          - "&7Switch between:&r "
          - "&r &8| &e▪&r &eRecently Added ◄"
          - "&r &8| &7▪&r &fMost Bought"
          - "&r &8| &7▪&r &fCheapest"
          - "&r &8| &7▪&r &fMost Expansive"
          - "&r &8| &7▪&r &fAlphabetical"
          - "&r"
          - "&e► &lClick &fto switch mode"
          - "&8► Right click to go backwards"
      MOST_BOUGHT:
        material: HOPPER
        display-name: "&e&lSort"
        lore:
          - "&8Favorites you buy most often."
          - "&r"
          - "&7Switch between:&r "
          - "&r &8| &7▪&r &fRecently Added&r"
          - "&r &8| &e▪&r &eMost Bought ◄"
          - "&r &8| &7▪&r &fCheapest"
          - "&r &8| &7▪&r &fMost Expansive"
          - "&r &8| &7▪&r &fAlphabetical"
          - "&r"
          - "&e► &lClick &fto switch mode"
          - "&8► Right click to go backwards"
      CHEAPEST:
        material: HOPPER
        display-name: "&e&lSort"
        lore:
          - "&8Cheapest favorite items first."
          - "&r"
          - "&7Switch between:&r "
          - "&r &8| &7▪&r &fRecently Added&r"
          - "&r &8| &7▪&r &fMost Bought"
          - "&r &8| &e▪&r &eCheapest ◄"
          - "&r &8| &7▪&r &fMost Expansive"
          - "&r &8| &7▪&r &fAlphabetical"
          - "&r"
          - "&e► &lClick &fto switch mode"
          - "&8► Right click to go backwards"
      MOST_EXPENSIVE:
        material: HOPPER
        display-name: "&e&lSort"
        lore:
          - "&8Most expensive favorites first."
          - "&r"
          - "&7Switch between:&r "
          - "&r &8| &7▪&r &fRecently Added&r"
          - "&r &8| &7▪&r &fMost Bought"
          - "&r &8| &7▪&r &fCheapest"
          - "&r &8| &e▪&r &
```


## `gui-settings.yml`

```yaml
﻿# Shared GUI behavior and formatting settings

# Global GUI toggles
enableBuyGUI: true
enableSellGUI: true
enableSellAll: true
enableSellGUISellAll: true
returnToShop: true
quickBuySell: false

# Price visibility and placeholders
hideBuyPriceForUnbuyable: true
buyPriceForUnsellablePlaceholder: "-"
hideSellPriceForUnsellable: true
sellPriceForUnsellablePlaceholder: "-"

# Click behavior
clickActions:
  LEFT: BUY
  RIGHT: SELL
  SHIFT_RIGHT: SELL_ALL
  MIDDLE: Favorite

# Item lore formats
shopItemLoreFormat:
  item:
    - "&7Buy price: &c%buy%"
    - "&7Sell price: &a%sell%"

  itemBuyGUI:
    - "&7Buy price: &c%buy%"

  itemSellGUI:
    - "&7Sell price: &a%sell%"

  itemSellGUISellAll:
    - "&7Sell all for: &a%sell%"

  permission:
    - "&7Buy price: &c%buy%"

  enchantment:
    - "&7Buy price: &c%buy%"

  command:
    - "&7Buy price: &c%buy%"

# Item stack-size caps
itemStackSizeCappedAt:
  1:
    material: ENDER_PEARL
    size: 16
  2:
    material: SNOWBALL
    size: 16
  3:
    material: OAK_SIGN
    size: 16
  4:
    material: EGG
    size: 16
  5:
    material: BUCKET
    size: 1

# Shared GUI sounds
sounds:
  MAIN_MENU_OPEN: UI_BUTTON_CLICK
  SHOP_OPEN: UI_BUTTON_CLICK
  SHOP_SELECT_ITEM: UI_BUTTON_CLICK
  SHOP_SWITCH_PAGE: UI_BUTTON_CLICK
  BUY_ITEM: ENTITY_EXPERIENCE_ORB_PICKUP
  SELL_ITEM: ENTITY_EXPERIENCE_ORB_PICKUP
  SELL_ALL_ITEM: ENTITY_EXPERIENCE_ORB_PICKUP
  FULL_INVENTORY: UI_BUTTON_CLICK
  INSUFFICIENT_FUNDS: UI_BUTTON_CLICK
  CANCEL: UI_BUTTON_CLICK

# Shared navigation buttons
buttons:
  goBack:
    slot: 49
    item:
      material: BARRIER
      amount: 1
      damage: 0
      name: "&c&lGo back to categories"
      lore:
        - "&7Click here to return"
        - "&7to the shop directory"

  previousPage:
    slot: 48
    item:
      material: PAPER
      quantity: 1
      name: "&e&lPrevious page"

  nextPage:
    slot: 50
    item:
      material: PAPER
      quantity: 1
      name: "&e&lNext page"

# Sell GUI
sellGui:
  enabled: true
  permission: "zaminshop.sellgui"
  sellOnClose: true
  returnInvalidItemsOnClose: true
  allowShiftClick: true
  allowDragIntoSellSlots: true

  sounds:
    open:
      enabled: true
      sound: "CHEST_OPEN"
      volume: 1.0
      pitch: 1.0

    invalidItem:
      enabled: true
      sound: "ENDERMAN_TELEPORT"
      volume: 1.0
      pitch: 1.0

    sold:
      enabled: true
      sound: "ORB_PICKUP"
      volume: 1.0
      pitch: 1.2

    noItemsSold:
      enabled: true
      sound: "VILLA
```


## `recent.yml`

```yaml
menu_title: "&8Recent Items"
size: 45

pagination:
  mode: Fancy
  item-slots:
    single-page:
      - 9-17
      - 18-26
    first-page:
      - 10-16
      - 19-24
    middle-page:
      - 9-17
      - 18-26
    last-page:
      - 11-17
      - 20-26

items:
  filler:
    type: CUSTOM
    material: GRAY_STAINED_GLASS_PANE
    display-name: "&f"
    slots:
      - 0-8
      - 27-38
      - 42-44
    priority: 100

  profile:
    type: CUSTOM
    material: "head-%player_name%"
    slot: 4
    display-name: "&b&lProfile"
    lore:
      - "&7Player: &f%player_name%"
      - "&7Balance: &a%zaminshop_balance%"
      - "&7Favorites: &e%zaminshop_favorites%"
      - "&7Recent Items: &e%zaminshop_recent_count%"
    priority: 50


  sort:
    type: SORT_CYCLE
    slot: 39
    default: RECENT
    modes:
      - RECENT
      - MOST_BOUGHT
      - OLDEST
    current:
      RECENT:
        material: HOPPER
        display-name: "&e&lSort"
        lore:
          - "&8Newest viewed/bought items first."
          - "&r"
          - "&7Switch between:&r "
          - "&r &8| &e▪&r &eRecently Added ◄"
          - "&r &8| &7▪&r &fMost Bought"
          - "&r &8| &7▪&r &fOldest"
          - "&r"
          - "&e► &lClick &fto switch mode"
          - "&8► Right click to go backwards"
      MOST_BOUGHT:
        material: HOPPER
        display-name: "&e&lSort"
        lore:
          - "&8Items bought most often."
          - "&r"
          - "&7Switch between:&r "
          - "&r &8| &7▪&r &fRecently Added"
          - "&r &8| &e▪&r &eMost Bought ◄"
          - "&r &8| &7▪&r &fOldest"
          - "&r"
          - "&e► &lClick &fto switch mode"
          - "&8► Right click to go backwards"
      OLDEST:
        material: HOPPER
        display-name: "&e&lSort"
        lore:
          - "&8Oldest recent items first."
          - "&r"
          - "&7Switch between:&r "
          - "&r &8| &7▪&r &fRecently Added"
          - "&r &8| &7▪&r &fMost Bought"
          - "&r &8| &e▪&r &eOldest ◄"
          - "&r"
          - "&e► &lClick &fto switch mode"
          - "&8► Right click to go backwards"

  clear:
    type: CUSTOM
    material: REDSTONE
    slot: 41
    display-name: "&cClear Recent"
    lore:
      - "&7Remove all recent history."
      - ""
      - "&cClick to clear"
    left_click_actions:
      - "[clear_recent]"
      - "[message] &aRecent items cleared."

  recent-item:
    type: RECENT_ITEM
    slots:
      - 9-17
      - 18-26
    display-name: "&e%zaminshop_ite
```


## `search.yml`

```yaml
menu_title: "&8ZaminShop ➔ Search: %query%"
size: 54

pagination:
  mode: Fancy
  item-slots:
    single-page:
      - 10-16
      - 19-25
      - 28-34
    first-page:
      - 10-16
      - 19-25
      - 28-33
    middle-page:
      - 9-17
      - 18-26
      - 27-35
    last-page:
      - 10-16
      - 19-25
      - 28-34

items:
  filler:
    type: CUSTOM
    material: GRAY_STAINED_GLASS_PANE
    display-name: "&r"
    slots:
      - 0-8
      - 36-44
      - 45-47
      - 51-53
    priority: 100

  search-item:
    type: SEARCH_ITEM
    slots:
      - 9-17
      - 18-26
      - 27-35
    display-name: "&e%zaminshop_item%"
    lore:
      - "&7Shop: &f%zaminshop_shop_name%"
      - "&7Buy: &a%zaminshop_buyprice%"
      - "&7Sell: &c%zaminshop_sellprice%"
      - ""
      - "&eLeft-click &7Buy"
      - "&eRight-click &7Sell"
      - "&bMiddle-click &7Favorite"
    priority: 50

  profile:
    type: CUSTOM
    material: "head-%player_name%"
    slot: 4
    display-name: "&b&lSearch"
    lore:
      - "&7Query: &f%query%"
      - "&7Results: &e%zaminshop_search_count%"
    priority: 50

  sort:
    type: SORT_CYCLE
    slot: 48
    priority: 1
    default: RELEVANCE
    modes:
      - RELEVANCE
      - CHEAPEST
      - MOST_EXPENSIVE
      - ALPHABETICAL
    current:
      RELEVANCE:
        material: HOPPER
        display-name: "&e&lSort"
        lore:
          - "&8Best search matches first."
          - "&r"
          - "&7Switch between:&r "
          - "&r &8| &e▪&r &eRelevance ◄"
          - "&r &8| &7▪&r &fCheapest"
          - "&r &8| &7▪&r &fMost Expansive"
          - "&r &8| &7▪&r &fAlphabetica"
          - "&r"
          - "&e► &lClick &fto switch mode"
          - "&8► Right click to go backwards"
      CHEAPEST:
        material: HOPPER
        display-name: "&e&lSort"
        lore:
          - "&8Cheapest items first."
          - "&r"
          - "&7Switch between:&r "
          - "&r &8| &7▪&r &fRelevance"
          - "&r &8| &e▪&r &eCheapest ◄"
          - "&r &8| &7▪&r &fMost Expansive"
          - "&r &8| &7▪&r &fAlphabetica"
          - "&r"
          - "&e► &lClick &fto switch mode"
          - "&8► Right click to go backwards"
      MOST_EXPENSIVE:
        material: HOPPER
        display-name: "&e&lSort"
        lore:
          - "&8Most expensive items first."
          - "&r"
          - "&7Switch between:&r "
          - "&r &8| &7▪&r &fRelevance"
          - "&r &8| &7▪&r &fCheapest"
          - "&r &8| &e▪&r &eMost Expans
```


## `sell.yml`

```yaml
menu_title: "&8Sell Items"
size: 54

items:
#################################################
#             SHOP Menu Decoration              #
#################################################
  filler:
    type: CUSTOM
    material: GRAY_STAINED_GLASS_PANE
    slots:
      - 0-8
      - 10
      - 28
      - 37
      - 45-46
    display-name: "&r"

  selection:
    type: CUSTOM
    material: LIME_STAINED_GLASS_PANE
    slot: 19
    display-name: "&r"


#################################################
#              Sell Menu Items                  #
#################################################

  sell-area:
    type: SELL_SLOT
    slots:
      - 11-17
      - 20-26
      - 29-35
      - 38-44

  summary:
    type: SELL_SUMMARY
    slot: 49
    material: EMERALD
    display-name: "%zaminshop_sell_summary_name%"

  info:
    type: CUSTOM
    slot: 51
    material: BOOK
    display-name: "%zaminshop_sell_info_name%"
    lore:
      - "%zaminshop_sell_info_lore_1%"
      - "%zaminshop_sell_info_lore_2%"
    left_click_actions:
      - "[message] &ePlace items into the empty slots."

  sell_menu_tip:
    type: CUSTOM
    material: BLACK_STAINED_GLASS_PANE
    slots:
      - 47-48
      - 50
      - 52-53
    display-name: "&8Click items in your inventory"
    lore:
    - "&8to add to the list of items to sell"


#################################################
#              SHOP Menu Items                  #
#################################################

  server_shop:
    type: CUSTOM
    material: EMERALD
    slot: 9
    display-name: "&b&lServer Shop"
    lore:
    - "&r"
    - "&fBuy blocks, gear, and more"
    - "&fstock up on useful resources"
    - "&fall in one convenient shop"
    - "&r"
    - "&bFeatures:"
    - "&b ▪ &fBuilding Blocks"
    - "&b ▪ &fDecorative blocks"
    - "&b ▪ &fMob Drops"
    - "&b ▪ &fMinerals"
    - "&b ▪ &fSpawners"
    - "&b ▪ &fCombat items"
    - "&b ▪ &fAnd much more!"
    - "&r"
    - "&e► Click here to open"
    left_click_actions:
    - "[open] shop-directory"

  sell_menu:
    type: CUSTOM
    material: HOPPER
    slot: 18
    display-name: "&a&lSell Menu"
    lore:
    - "&r"
    - "&fSell your items here through"
    - "&fthe sell menu with just a"
    - "&ffew clicks"

  favorite_menu:
    type: CUSTOM
    material: ENDER_CHEST
    slot: 27
    display-name: "&6&lFavorites"
    lore:
    - "&r"
    - "&fView your favorite items or"
    - "&fadd new ones by &bshift-clicking "
    - "&rin the shop"
    -
```


## `shop-directory.yml`

```yaml
menu_title: "&rZaminShop"
open_command:
  - shop
size: 54

items:
#################################################
#             SHOP Menu Decoration              #
#################################################
  filler:
    type: CUSTOM
    material: GRAY_STAINED_GLASS_PANE
    slots:
      - 0-8
      - 19
      - 28
      - 37
      - 45-48
      - 51-53
    display-name: "&r"

  selection:
    type: CUSTOM
    material: LIME_STAINED_GLASS_PANE
    slot: 10
    display-name: "&r"

#################################################
#              SHOP Menu Items                  #
#################################################

  server_shop:
    type: CUSTOM
    material: EMERALD
    slot: 9
    display-name: "&b&lServer Shop"
    lore:
    - "&r"
    - "&fBuy blocks, gear, and more"
    - "&fstock up on useful resources"
    - "&fall in one convenient shop"
    - "&r"
    - "&bFeatures:"
    - "&b ▪ &fBuilding Blocks"
    - "&b ▪ &fDecorative blocks"
    - "&b ▪ &fMob Drops"
    - "&b ▪ &fMinerals"
    - "&b ▪ &fSpawners"
    - "&b ▪ &fCombat items"
    - "&b ▪ &fAnd much more!"

  sell_menu:
    type: CUSTOM
    material: HOPPER
    slot: 18
    display-name: "&a&lSell Menu"
    lore:
    - "&r"
    - "&fSell your items here through"
    - "&fthe sell menu with just a"
    - "&ffew clicks"
    - "&r"
    - "&e► Click here to open"
    left_click_actions:
    - "[open] sell"

  favorite_menu:
    type: CUSTOM
    material: ENDER_CHEST
    slot: 27
    display-name: "&6&lFavorites"
    lore:
    - "&r"
    - "&fView your favorite items or"
    - "&fadd new ones by &bmiddle-clicking "
    - "&rin the shop"
    - "&r"
    - "&e► Click here to open"
    left_click_actions:
    - "[open] favorites"

  recent_menu:
    type: CUSTOM
    material: GOLD_INGOT
    slot: 36
    display-name: "&c&lRecently Bought"
    lore:
    - "&r"
    - "&fView items you recently purchased"
    - "&ffrom the shop all in one place"
    - "&r"
    - "&e► Click here to open"
    left_click_actions:
    - "[open] recent"

  balance:
    type: CUSTOM
    material: EMERALD
    slot: 49
    display-name: "&fYou have &2$&a%vault_eco_balance_commas%"

  shop_information:
    type: CUSTOM
    material: Sign
    slot: 50
    display-name: "&e&lWhat is this menu?"

#################################################
#           Shop Category Items                 #
#################################################

  category_blocks:
    type: SHOP_CATEGORY
    material: GRASS_BLOCK
```
