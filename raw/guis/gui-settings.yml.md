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
      sound: "VILLAGER_NO"
      volume: 1.0
      pitch: 1.0

  messages:
    disabled: "&cThe sell GUI is disabled."
    invalidItem: "&cYou cannot sell this item here."
    sold: "&aSold &f%amount%x &aitems for &6%money%&a."
    noItemsSold: "&cNo sellable items were found."
    inventoryFullReturned: "&eSome items were returned because they could not be sold."
```
