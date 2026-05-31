# Sell Menu

The sell GUI is the dedicated menu for selling inventory items through ZaminShop.

## What it does

Players can open a menu, move sellable items into the sell area, and let the plugin resolve prices through the normal shop item logic instead of a disconnected fallback system.

Command:

```text
/shop sell
```

Permission:

```text
zaminshop.sellgui
```

## Why it exists

The sell GUI is useful because command-only selling becomes clumsy once players are dealing with:

- mixed inventories
- partial stacks
- large farm output
- frequent category switching

## Main behavior switches

These are controlled in `guis/gui-settings.yml`:

```yaml
sellGui:
  enabled: true
  permission: "zaminshop.sellgui"
  sellOnClose: true
  returnInvalidItemsOnClose: true
  allowShiftClick: true
  allowDragIntoSellSlots: true
```

## What those options mean

- `enabled`: turns the menu on or off
- `permission`: permission required to open it
- `sellOnClose`: sells valid items when the menu closes
- `returnInvalidItemsOnClose`: protects players from losing invalid items
- `allowShiftClick`: allows fast movement from inventory into the sell area
- `allowDragIntoSellSlots`: controls drag behavior

## Menu item types used here

The sell menu relies on these dynamic types:

- `SELL_SLOT`
- `SELL_SUMMARY`
- `CUSTOM`

## Recommended customization targets

Most servers should adjust:

- sell area size
- filler layout
- summary item wording
- info/help item wording
- the navigation items around the sell flow

## Common mistakes

### Treating the sell GUI as a second pricing system

It is not supposed to have its own economy logic. It should stay a visual entry point into the existing sell-price resolver.

### Removing all guidance text

Players still need to understand:

- where to place items
- whether closing the menu sells items
- what the summary means

One good info item usually prevents a lot of confusion.
