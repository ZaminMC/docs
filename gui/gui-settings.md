---
description: Complete reference for plugins/ZaminShop/guis/gui-settings.yml.
---

# GUI Settings

`gui-settings.yml` controls behavior shared by shop menus. It does not define the layout of the amount selector, search, favorites, recent, or sell menus; those have separate files.

## Global toggles

| Option | Default | Effect |
| --- | --- | --- |
| `enableBuyGUI` | `true` | Enables the buy amount GUI flow. |
| `enableSellGUI` | `true` | Enables the sell amount GUI flow. |
| `enableSellAll` | `true` | Enables sell-all behavior. |
| `enableSellGUISellAll` | `true` | Enables sell-all from the sell GUI flow. |
| `returnToShop` | `true` | Returns players to the shop after supported actions. |
| `quickBuySell` | `false` | Uses quick transaction behavior. |

## Price visibility

| Option | Default |
| --- | --- |
| `hideBuyPriceForUnbuyable` | `true` |
| `buyPriceForUnsellablePlaceholder` | `&cN/A` |
| `hideSellPriceForUnsellable` | `true` |
| `sellPriceForUnsellablePlaceholder` | `&cN/A` |

Despite its name, `buyPriceForUnsellablePlaceholder` is the loaded key for the unavailable buy-price placeholder in the current settings class.

## Default click actions

```yaml
clickActions:
  LEFT: BUY
  RIGHT: SELL
  SHIFT_RIGHT: SELL_ALL
  MIDDLE: Favorite
```

These mappings set the normal shop-item action associated with each click. Per-item configured actions can provide more specific behavior.

## Lore formats

`shopItemLoreFormat` has separate lists for:

| Key | Applied to |
| --- | --- |
| `item` | Normal buy/sell shop items |
| `itemBuyGUI` | Buy GUI item |
| `itemSellGUI` | Sell GUI item |
| `itemSellGUISellAll` | Sell-all GUI item |
| `permission` | Permission products |
| `enchantment` | Enchantment products |
| `command` | Command products |

The shipped item format is:

```yaml
shopItemLoreFormat:
  item:
    - "&r"
    - "&r   &e▪ &fBuy Price: &e%buy%   &r"
    - "&r   &c▪ &fSell Price: &e%sell%   &r"
    - "&r"
```

`%buy%` and `%sell%` are replaced with formatted prices.

## Stack-size caps

```yaml
itemStackSizeCappedAt:
  1:
    material: ENDER_PEARL
    size: 16
```

Each numbered entry associates a material with a cap. The shipped file defines:

- `ENDER_PEARL`: `16`;
- `SNOWBALL`: `16`;
- `OAK_SIGN`: `16`;
- `EGG`: `16`;
- `BUCKET`: `1`.

## Shared sounds

| Key | Default |
| --- | --- |
| `MAIN_MENU_OPEN` | `UI_BUTTON_CLICK` |
| `SHOP_OPEN` | `UI_BUTTON_CLICK` |
| `SHOP_SELECT_ITEM` | `UI_BUTTON_CLICK` |
| `SHOP_SWITCH_PAGE` | `UI_BUTTON_CLICK` |
| `BUY_ITEM` | `ENTITY_EXPERIENCE_ORB_PICKUP` |
| `SELL_ITEM` | `ENTITY_EXPERIENCE_ORB_PICKUP` |
| `SELL_ALL_ITEM` | `ENTITY_EXPERIENCE_ORB_PICKUP` |
| `FULL_INVENTORY` | `UI_BUTTON_CLICK` |
| `INSUFFICIENT_FUNDS` | `UI_BUTTON_CLICK` |
| `CANCEL` | `UI_BUTTON_CLICK` |

Sound names are resolved against the running Minecraft/Bukkit version. A name available on one version may not exist on another.

## Transaction failure feedback

```yaml
transaction-failure-feedback:
  enabled: true
  send-message: false
  duration-ticks: 40
```

Behavior:

| `enabled` | `send-message` | Result |
| --- | --- | --- |
| `true` | `false` | Temporary GUI feedback only |
| `true` | `true` | GUI feedback and chat message |
| `false` | `true` | Chat message only |

Configured failure IDs:

- `insufficient-funds`;
- `insufficient-items`;
- `inventory-full`.

Each failure supports:

```yaml
enabled: true
sound: INSUFFICIENT_FUNDS
item:
  material: BARRIER
  quantity: 1
  name: "&c&lInsufficient funds"
  lore:
    - "&7You cannot afford this purchase."
    - "&7Required: &f%price%"
```

The shipped templates use `%price%`, `%amount%`, and `%item%` where relevant.

## Navigation buttons

Shared button definitions:

| Path | Default slot |
| --- | --- |
| `buttons.goBack` | `49` |
| `buttons.previousPage` | `48` |
| `buttons.nextPage` | `50` |

Each contains an `item` section using the normal item parser:

```yaml
buttons:
  nextPage:
    slot: 50
    item:
      material: PAPER
      quantity: 1
      name: "&e&lNext page"
```

## Sell GUI

| Option | Default | Effect |
| --- | --- | --- |
| `sellGui.enabled` | `true` | Enables the inventory sell menu. |
| `sellGui.permission` | `zaminshop.player.sell-gui` | Required permission. |
| `sellGui.sellOnClose` | `true` | Processes eligible items when the GUI closes. |
| `sellGui.returnInvalidItemsOnClose` | `true` | Returns items that cannot be sold. |
| `sellGui.allowShiftClick` | `true` | Allows shift-click insertion. |
| `sellGui.allowDragIntoSellSlots` | `true` | Allows dragging into sell slots. |

Sell GUI sound blocks:

- `open`;
- `invalidItem`;
- `sold`;
- `noItemsSold`.

Each block accepts:

```yaml
enabled: true
sound: "CHEST_OPEN"
volume: 1.0
pitch: 1.0
```

Sell GUI message keys:

| Key | Available shipped placeholders |
| --- | --- |
| `disabled` | none |
| `invalidItem` | none |
| `sold` | `%amount%`, `%money%` |
| `noItemsSold` | none |
| `inventoryFullReturned` | none |

## Reloading

Run:

```text
/zaminshop reload
```

Then reopen the menu. Existing open inventories do not become a reliable preview of the newly loaded layout.
