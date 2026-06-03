# Built-in Menus

ZaminShop ships with a set of shared menus configured under `plugins/ZaminShop/guis/`.

These menus are part of the core player workflow.

## Amount selector

File:

```text
guis/amount-selector.yml
```

Use it when:

- players should choose a quantity before buying or selling
- you want a controlled amount flow instead of only left-click and right-click

It supports:

- custom filler items
- dynamic control visibility
- priorities
- placeholders
- selected item preview

## Bulk buy

File:

```text
guis/bulk-buy.yml
```

Use it when:

- you want stack-based quantity shortcuts
- frequent purchases should take fewer clicks

## Bulk sell

File:

```text
guis/bulk-sell.yml
```

Use it when:

- players commonly sell repeated stack quantities
- you want a faster sell workflow than manual amount stepping

## Favorites

File:

```text
guis/favorites.yml
```

Use it to give players a curated list of items they actually care about.

Good for:

- repeat purchases
- donor utility items
- everyday economy items

## Recent

File:

```text
guis/recent.yml
```

Use it to surface recently interacted-with items without asking players to remember where everything lives.

## Search

File:

```text
guis/search.yml
```

Use it to reduce browsing friction in larger shops.

## Sell GUI

File:

```text
guis/sell.yml
```

Use it when you want:

- inventory-driven selling
- a dedicated selling workflow
- a cleaner player experience than only command-based selling

## GUI settings

File:

```text
guis/gui-settings.yml
```

This file controls shared GUI behavior and defaults used across the system.

## Moving built-in menus

If you move a built-in menu file, update the path in:

```text
config.yml -> gui_menus
```

## Common mistakes

### Editing the wrong menu

If the problem happens in search, recent, or favorites, fix the matching shared menu, not a category file.

### Forgetting that these menus share the same item system

These menus support the same modern material directives, placeholder rendering, actions, and page controls as the rest of the plugin.

## Related pages

- [Menu File Format](menu-file-format.md)
- [Actions and Requirements](actions-requirements.md)
- [Sell Menu](sell-gui.md)
