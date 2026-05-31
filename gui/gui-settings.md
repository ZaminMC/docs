# GUI Settings

`gui-settings.yml` is the shared behavior file for menu-wide defaults.

It is not a replacement for your actual menu layouts. Instead, it controls the pieces that several menus should share.

## File location

```text
plugins/ZaminShop/guis/gui-settings.yml
```

## What this file controls

### Global GUI toggles

These settings decide whether certain GUI flows are available at all.

Examples:

- `enableBuyGUI`
- `enableSellGUI`
- `enableSellAll`
- `enableSellGUISellAll`
- `returnToShop`
- `quickBuySell`

### Price visibility

These settings control what players see when an item cannot be bought or sold.

Examples:

- `hideBuyPriceForUnbuyable`
- `buyPriceForUnsellablePlaceholder`
- `hideSellPriceForUnsellable`
- `sellPriceForUnsellablePlaceholder`

### Click mappings

The shared click mapping section defines the default action meaning for click types.

Example:

```yaml
clickActions:
  LEFT: BUY
  RIGHT: SELL
  SHIFT_RIGHT: SELL_ALL
  MIDDLE: Favorite
```

That gives you one place to change expected click behavior across the shop experience.

### Shared lore formats

This section controls the default lore lines used for:

- normal items
- buy GUI items
- sell GUI items
- sell-all GUI items
- permission items
- enchantment items
- command items

This is where you make the shop feel visually consistent.

### Shared sounds

The sound section lets you keep a unified feedback style for:

- opening menus
- switching pages
- buying
- selling
- inventory full responses
- insufficient funds responses

### Shared navigation buttons

The button definitions provide default back, previous-page, and next-page items that shop menus can reuse.

### Sell GUI behavior

The `sellGui` section controls:

- whether the sell GUI is enabled
- which permission it requires
- whether items sell on close
- whether invalid items are returned
- whether shift-click and drag interactions are allowed
- which sounds and messages the sell GUI uses

## When to edit this file

Edit `gui-settings.yml` when you want to change global shop feel.

Do not use it when your goal is only:

- moving one button in one menu
- changing one menu's filler pattern
- changing one menu title

Those belong in the specific menu file instead.
