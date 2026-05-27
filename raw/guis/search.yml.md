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
          - "&r &8| &e▪&r &eMost Expansive ◄"
          - "&r &8| &7▪&r &fAlphabetica"
          - "&r"
          - "&e► &lClick &fto switch mode"
          - "&8► Right click to go backwards"
      ALPHABETICAL:
        material: HOPPER
        display-name: "&e&lSort"
        lore:
          - "&8Sorts results alphabetically."
          - "&r"
          - "&7Switch between:&r "
          - "&r &8| &7▪&r &fRelevance"
          - "&r &8| &7▪&r &fCheapest"
          - "&r &8| &7▪&r &fMost Expansive"
          - "&r &8| &e▪&r &eAlphabetica ◄"
          - "&r"
          - "&e► &lClick &fto switch mode"
          - "&8► Right click to go backwards"

  previous:
    type: PREVIOUS_PAGE
    material: ARROW
    slot: 47
    show-when-unavailable: false
    display-name: "&ePrevious Page"
    left_click_actions:
      - "[previous_page]"
    priority: 50

  back:
    type: BACK
    material: EMERALD
    slot: 49
    display-name: "&a&lGo back to Shop"
    left_click_actions:
      - "[back]"

  next:
    type: NEXT_PAGE
    material: ARROW
    slot: 51
    show-when-unavailable: false
    display-name: "&eNext Page"
    left_click_actions:
      - "[next_page]"
    priority: 50

  information:
    type: CUSTOM
    material: SIGN
    slot: 50
    display-name: "&e&lWhat is this Menu?"
```
