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
          - "&r &8| &e▪&r &eMost Expansive ◄"
          - "&r &8| &7▪&r &fAlphabetical"
          - "&r"
          - "&e► &lClick &fto switch mode"
          - "&8► Right click to go backwards"
      ALPHABETICAL:
        material: HOPPER
        display-name: "&e&lSort"
        lore:
          - "&8Sort favorites alphabetically."
          - "&r"
          - "&7Switch between:&r "
          - "&r &8| &7▪&r &fRecently Added&r"
          - "&r &8| &7▪&r &fMost Bought"
          - "&r &8| &7▪&r &fCheapest"
          - "&r &8| &7▪&r &fMost Expansive"
          - "&r &8| &e▪&r &eAlphabetical ◄"
          - "&r"
          - "&e► &lClick &fto switch mode"
          - "&8► Right click to go backwards"

  compact-mode:
    type: CUSTOM
    material: PAPER
    slot: 39
    display-name: "&fCompact Mode"
    lore:
      - "&7Toggle compact item display."
      - ""
      - "&eClick to toggle"
    left_click_actions:
      - "[toggle_compact_mode]"

  clear-favorites:
    type: CUSTOM
    material: REDSTONE
    slot: 42
    display-name: "&cClear Favorites"
    lore:
      - "&7Remove all favorite items."
      - ""
      - "&cClick to clear"
    left_click_actions:
      - "[clear_favorites]"
      - "[message] &cAll favorites removed."

  favorite-item:
    type: FAVORITE_ITEM
    slots:
      - 9-17
      - 18-26
    display-name: "&e%zaminshop_item%"
    lore:
      - "&7Shop: &f%zaminshop_shop_name%"
      - "&7Buy: &a%zaminshop_buyprice%"
      - "&7Sell: &c%zaminshop_sellprice%"
      - "&7Favorited: &f%zaminshop_favorited_since%"
      - ""
      - "&eLeft-click &7Buy"
      - "&eRight-click &7Sell"
      - "&bShift-click &7Favorite"

  empty:
    type: CUSTOM
    material: NETHER_STAR
    slot: 4
    display-name: "&cNo Favorite Items"
    lore:
      - "&7Middle-click items in shops"
      - "&7to add them to favorites."
    show-when-empty: true
    priority: 1

  previous-page:
    type: PREVIOUS_PAGE
    material: ARROW
    slot: 36
    show-when-unavailable: false
    display-name: "&ePrevious Page"
    left_click_actions:
      - "[previous_page]"
    priority: 50

  shop:
    type: CUSTOM
    material: EMERALD
    slot: 40
    display-name: "&a&lGo back to Shop"
    click_actions:
      - "[player] shop"

  next-page:
    type: NEXT_PAGE
    material: ARROW
    slot: 44
    show-when-unavailable: false
    display-name: "&eNext Page"
    left_click_actions:
      - "[next_page]"
    priority: 50

  information:
    type: CUSTOM
    material: SIGN
    slot: 41
    display-name: "&e&lWhat is this Menu?"

  profile:
    type: CUSTOM
    material: "head-%player_name%"
    slot: 4
    display-name: "&b&lProfile"
    lore:
      - "&7Favorites: &e%zaminshop_favorites%"
      - "&7Favorite Limit: &e%zaminshop_favorite_limit%"
    priority: 5
```
