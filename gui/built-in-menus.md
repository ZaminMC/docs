# Built-in Menus

ZaminShop ships with several shared menu files. Each one serves a different stage of the player shopping flow.

## Amount selector

File:

```text
plugins/ZaminShop/guis/amount-selector.yml
```

### What it does

Lets the player choose a specific amount before buying or selling.

### When players see it

- when a shop item uses the amount selector buy flow
- when a shop item uses the amount selector sell flow

### Typical customizations

- change filler items
- move the action buttons
- rename confirm or cancel buttons
- add informational custom items

## Bulk buy

File:

```text
plugins/ZaminShop/guis/bulk-buy.yml
```

### What it does

Lets players buy multiple stacks quickly.

### Good use case

Useful for common materials such as:

- blocks
- ores
- farm goods

## Bulk sell

File:

```text
plugins/ZaminShop/guis/bulk-sell.yml
```

### What it does

Lets players sell multiple stacks quickly without repeated right-click loops.

## Favorites

File:

```text
plugins/ZaminShop/guis/favorites.yml
```

### What it does

Shows the player's saved favorite items across the shop system.

### Why players use it

Favorites reduce travel time through category menus for items bought or sold often.

## Recent

File:

```text
plugins/ZaminShop/guis/recent.yml
```

### What it does

Shows recently used items and recent buying or selling history.

### Why it matters

This menu helps players quickly repeat common actions without remembering which category an item came from.

## Search

File:

```text
plugins/ZaminShop/guis/search.yml
```

### What it does

Renders search results for the current pack command scope.

### Why it matters

Search becomes much more valuable as your category count and item count grow.

## Sell GUI

File:

```text
plugins/ZaminShop/guis/sell.yml
```

### What it does

Provides a dedicated menu where players can place sellable items and have them processed through the plugin's normal sell-price logic.

### Why it matters

This is the safer and more user-friendly alternative to forcing players into command-only selling.

## GUI settings

File:

```text
plugins/ZaminShop/guis/gui-settings.yml
```

### What it controls

- shared click mappings
- shared lore formats
- shared sounds
- shared navigation button defaults
- sell GUI behavior toggles

## Practical advice

Do not edit every menu at once.

Start with:

1. the main pack menu
2. one category menu
3. the sell GUI
4. favorites and search after the main flow feels right
