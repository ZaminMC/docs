# Customize Menus

This section is for menu layout, navigation, click actions, and player-facing GUI flow.

ZaminShop uses shared menu files for features such as:

- amount selector
- bulk buy
- bulk sell
- favorites
- recent history
- search
- sell GUI

## Use this section when you want to

- move buttons around
- change filler items
- add custom menu items
- add click actions
- tune pagination layout
- change how favorites, recent, search, or sell menus look

## Read these pages in order

1. [Menu File Format](menu-file-format.md)
2. [Menu Item Types](item-types.md)
3. [Actions](actions.md)
4. [Requirements](requirements.md)
5. [Built-in Menus](built-in-menus.md)

Then move to the specific menu you want to change.

## Important distinction

- files under `plugins/ZaminShop/guis/` are shared menus
- files under `plugins/ZaminShop/shops/<pack>/categories/` are shop category menus

That means a sell menu edit and a block shop edit live in different places even though both are inventory menus.
