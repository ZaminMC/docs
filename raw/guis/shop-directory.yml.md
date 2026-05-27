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
    slot: 21
    display-name: "&eBuilding Blocks"
    shop: blocks

  category_colorful_blocks:
    type: SHOP_CATEGORY
    material: WHITE_WOOL
    slot: 22
    display-name: "&eColorful Blocks"
    shop: colorful_blocks

  category_food:
    type: SHOP_CATEGORY
    material: GOLDEN_CARROT
    slot: 23
    display-name: "&eFood & Farming"
    shop: food

  category_minerals:
    type: SHOP_CATEGORY
    material: DIAMOND
    slot: 24
    display-name: "&eMinerals"
    shop: minerals

  category_spawner:
    type: SHOP_CATEGORY
    material: MOB_SPAWNER
    slot: 25
    display-name: "&eSpawners"
    shop: spawner

  category_redstone:
    type: SHOP_CATEGORY
    material: REDSTONE
    slot: 31
    display-name: "&eRedstone Items"
    shop: REDSTONE

  category_mob_drops:
    type: SHOP_CATEGORY
    material: STRING
    slot: 32
    display-name: "&eMob Drops"
    shop: drops

  category_miscellaneous:
    type: SHOP_CATEGORY
    material: BEACON
    slot: 33
    display-name: "&eMiscellaneous"
    shop: miscellaneous
```
