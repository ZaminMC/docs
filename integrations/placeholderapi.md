# PlaceholderAPI

PlaceholderAPI is one of the most useful integrations in ZaminShop.

It allows menu titles, lore, messages, and context-driven displays to react to the player and the current shop state.

## What PlaceholderAPI is used for

Use PlaceholderAPI when you want:

- balance values
- player names
- rank or stat values
- custom plugin values
- context-aware menu text

## Basic requirement

Install PlaceholderAPI on the server and start the server with it present.

ZaminShop registers its own expansion when PlaceholderAPI is available.

## Where placeholders work

Placeholders can be used in:

- menu titles where supported
- custom menu item names
- custom lore
- current-context displays
- language messages
- pack and category displays

## ZaminShop-specific context placeholders

ZaminShop provides current-context values such as:

- current item
- current category
- current shop pack name
- current shop pack id
- current page
- current transaction data

This is especially useful in:

- amount selector menus
- favorites and recent menus
- pack menus
- category menus

## Example

```yml
display-name: "&fBalance: &a%vault_eco_balance_commas%"
```

## Good uses

### Pack main menu profile item

Show:

- player name
- balance
- favorite count

### Current category banners

Show:

- current category name
- current pack name

### Amount selector

Show:

- current item name
- selected quantity
- current player balance

## Common mistakes

### Assuming every placeholder works in every context

Some placeholders depend on the current menu or shop state.

### Forgetting PlaceholderAPI is optional

If the server does not have PlaceholderAPI, those placeholders will not resolve through PlaceholderAPI.

## Related pages

- [Menu File Format](../gui/menu-file-format.md)
- [Built-in Menus](../gui/built-in-menus.md)
- [Language and Messages](../configuration/language.md)
