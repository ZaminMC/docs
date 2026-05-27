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
    display-name: "&e%zaminshop_item%"
    lore:
      - "&7Shop: &f%zaminshop_shop_name%"
      - "&7Buy: &a%zaminshop_buyprice%"
      - "&7Sell: &c%zaminshop_sellprice%"
      - "&7Bought: &f%zaminshop_buy_count%x"
      - "&7Last Used: &f%zaminshop_last_used%"
      - ""
      - "&eLeft-click &7Buy"
      - "&eRight-click &7Sell"
      - "&bShift-click &7Favorite"

  empty:
    type: CUSTOM
    material: CHEST
    slot: 4
    display-name: "&eNo Recent Items"
    lore:
      - "&7Items you recently interact with"
      - "&7will appear here."
    show-when-empty: true
    priority: 25

  previous-page:
    type: PREVIOUS_PAGE
    material: ARROW
    slot: 37
    show-when-unavailable: false
    display-name: "&ePrevious Page"
    left_click_actions:
      - "[previous_page]"
    priority: 50

#  favorites:
#    type: CUSTOM
#    material: NETHER_STAR
#    slot: 47
#    display-name: "&bFavorites"
#    lore:
#      - "&7Open your favorite items."
#    left_click_actions:
#      - "[open] favorites"
#
#  back:
#    type: BACK
#    material: ARROW
#    slot: 49
#    display-name: "&aBack"
#    left_click_actions:
#      - "[back]"

  next-page:
    type: NEXT_PAGE
    material: ARROW
    slot: 43
    show-when-unavailable: false
    display-name: "&eNext Page"
    left_click_actions:
      - "[next_page]"
    priority: 50


  shop:
    type: CUSTOM
    material: EMERALD
    slot: 40
    display-name: "&a&lGo back to Shop"
    click_actions:
      - "[player] shop"
```
