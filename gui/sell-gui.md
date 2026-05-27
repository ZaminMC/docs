# Sell GUI

The sell GUI is opened with:

```text
/shop sell
```

Default permission in `guis/gui-settings.yml`:

```yaml
sellGui:
  permission: "zaminshop.sellgui"
```

Default `sell.yml` uses dynamic item types:

- `SELL_SLOT`
- `SELL_SUMMARY`
- `CUSTOM`

Default file:

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
```
