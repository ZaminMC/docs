---
description: Complete commented reference for plugins/ZaminShop/guis/gui-settings.yml.
---

# GUI Settings

`plugins/ZaminShop/guis/gui-settings.yml` controls behavior shared by shop menus. It does not define the layout of the amount selector, search, favorites, recent, or sell menus; those have separate files.

{% hint style="info" %}
The examples below use the exact hierarchy and defaults shipped with ZaminShop. Comments explain each option beside the value you edit.
{% endhint %}

## Global behavior

```yaml
# Enable the buy amount GUI flow.
enableBuyGUI: true

# Enable the sell amount GUI flow.
enableSellGUI: true

# Enable sell-all behavior.
enableSellAll: true

# Enable sell-all inside the sell GUI flow.
enableSellGUISellAll: true

# Return players to the shop after supported actions.
returnToShop: true

# Use quick buy/sell behavior instead of the normal amount flow.
quickBuySell: false
```

## Price visibility

```yaml
# Hide the buy-price lore line when an item cannot be bought.
hideBuyPriceForUnbuyable: true

# Text displayed when an unavailable buy price is not hidden.
# The current loader uses this key despite its "Unsellable" name.
buyPriceForUnsellablePlaceholder: "&cN/A"

# Hide the sell-price lore line when an item cannot be sold.
hideSellPriceForUnsellable: true

# Text displayed when an unavailable sell price is not hidden.
sellPriceForUnsellablePlaceholder: "&cN/A"
```

## Default click actions

```yaml
clickActions:
  # Left-click a normal shop item to buy.
  LEFT: BUY

  # Right-click a normal shop item to sell.
  RIGHT: SELL

  # Shift-right-click to sell all matching items.
  SHIFT_RIGHT: SELL_ALL

  # Middle-click to toggle the item as a favorite.
  MIDDLE: Favorite
```

Per-item configured actions can provide more specific behavior.

## Shop item lore

```yaml
shopItemLoreFormat:
  # Normal buy/sell shop items.
  item:
    - "&r"
    - "&r   &e▪ &fBuy Price: &e%buy%   &r"
    - "&r   &c▪ &fSell Price: &e%sell%   &r"
    - "&r"

  # Item shown in the buy GUI.
  itemBuyGUI:
    - "&r"
    - "&r   &e▪ &fBuy Price: &e%buy%   &r"
    - "&r"

  # Item shown in the sell GUI.
  itemSellGUI:
    - "&r"
    - "&r   &c▪ &fSell Price: &e%sell%   &r"
    - "&r"

  # Sell-all item shown in the sell GUI.
  itemSellGUISellAll:
    - "&r"
    - "&r   &c▪ &fSell Price: &e%sell%   &r"
    - "&r"

  # Permission products.
  permission:
    - "&r"
    - "&r   &e▪ &fBuy Price: &e%buy%   &r"
    - "&r"

  # Enchantment products.
  enchantment:
    - "&r"
    - "&r   &e▪ &fBuy Price: &e%buy%   &r"
    - "&r"

  # Command products.
  command:
    - "&r"
    - "&r   &e▪ &fBuy Price: &e%buy%   &r"
    - "&r"
```

`%buy%` and `%sell%` are replaced with formatted prices.

## Stack-size caps

```yaml
# Override the displayed/selected stack cap for specific materials.
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
```

Each numbered child is an independent material-to-size rule.

## Shared sounds

```yaml
sounds:
  # Opening the main shop directory.
  MAIN_MENU_OPEN: UI_BUTTON_CLICK

  # Opening a category shop.
  SHOP_OPEN: UI_BUTTON_CLICK

  # Selecting a shop item.
  SHOP_SELECT_ITEM: UI_BUTTON_CLICK

  # Changing shop pages.
  SHOP_SWITCH_PAGE: UI_BUTTON_CLICK

  # Successful transaction sounds.
  BUY_ITEM: ENTITY_EXPERIENCE_ORB_PICKUP
  SELL_ITEM: ENTITY_EXPERIENCE_ORB_PICKUP
  SELL_ALL_ITEM: ENTITY_EXPERIENCE_ORB_PICKUP

  # Failure and cancellation sounds.
  FULL_INVENTORY: UI_BUTTON_CLICK
  INSUFFICIENT_FUNDS: UI_BUTTON_CLICK
  CANCEL: UI_BUTTON_CLICK
```

Sound names are resolved against the running Minecraft/Bukkit version. A sound available on one version may not exist on another.

## Transaction failure feedback

```yaml
# Temporary feedback shown in the clicked slot after a safe transaction refusal.
# enabled=true + send-message=false: GUI feedback only
# enabled=true + send-message=true: GUI feedback and chat message
# enabled=false + send-message=true: chat message only
transaction-failure-feedback:
  enabled: true
  send-message: false

  # Number of ticks before the original slot item is restored.
  duration-ticks: 40

  failures:
    insufficient-funds:
      enabled: true
      # References the INSUFFICIENT_FUNDS key under sounds.
      sound: INSUFFICIENT_FUNDS
      item:
        material: BARRIER
        quantity: 1
        name: "&c&lInsufficient funds"
        lore:
          - "&7You cannot afford this purchase."
          - "&7Required: &f%price%"

    insufficient-items:
      enabled: true
      sound: CANCEL
      item:
        material: BARRIER
        quantity: 1
        name: "&c&lNot enough items"
        lore:
          - "&7You need &f%amount%x %item%&7."

    inventory-full:
      enabled: true
      sound: FULL_INVENTORY
      item:
        material: BARRIER
        quantity: 1
        name: "&c&lInventory full"
        lore:
          - "&7Make room before buying this item."
```

The shipped failure templates use `%price%`, `%amount%`, and `%item%` where relevant.

## Navigation buttons

```yaml
buttons:
  goBack:
    # Inventory slot used by the back button.
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
```

Each `item` block uses the normal [Item Construction Reference](../shops/item-options.md).

## Sell GUI

```yaml
sellGui:
  # Enable the inventory sell menu.
  enabled: true

  # Permission required to use the sell GUI.
  permission: "zaminshop.player.sell-gui"

  # Process eligible items when the GUI closes.
  sellOnClose: true

  # Return items that cannot be sold when the GUI closes.
  returnInvalidItemsOnClose: true

  # Allow shift-clicking items into the sell inventory.
  allowShiftClick: true

  # Allow dragging items into sell slots.
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
    # Available placeholders: %amount% and %money%.
    sold: "&aSold &f%amount%x &aitems for &6%money%&a."
    noItemsSold: "&cNo sellable items were found."
    inventoryFullReturned: "&eSome items were returned because they could not be sold."
```

## Reloading

Run:

```text
/zaminshop reload
```

Then reopen the menu. Inventories that were already open are not a reliable preview of the newly loaded settings.
