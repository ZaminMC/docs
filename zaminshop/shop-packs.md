# Shop Packs

Shop packs are separate shop groups.

Use them when you want different shops for different game modes, ranks, worlds, or events.

Shop packs live in:

```text
plugins/ZaminShop/shops/packs/<pack>/
```

Each pack has:

```text
main.yml
categories/
```

## Example

```yaml
menu_title: "&8Survival Shop"
open_command: shop
register_command: true

amount-selector: "default.yml"
bulk-buy: "default.yml"
bulk-sell: "default.yml"
purchase-confirmation: "default.yml"

currencies:
  - vault

size: 54

items:
  filler:
    type: CUSTOM
    material: GRAY_STAINED_GLASS_PANE
    slots:
      - 0-8
    display-name: "&r"

  blocks:
    type: SHOP_CATEGORY
    material: GRASS_BLOCK
    slot: 20
    display-name: "&aBlocks"
    lore:
      - "&7Buy building blocks."
      - "&eClick to open."
    shop: building_blocks
```

## Options

| Option | Description |
| ------ | ----------- |
| `menu_title` | Inventory title for the pack menu. |
| `open_command` | Command label or labels that open this pack. |
| `register_command` | Registers the pack command dynamically. |
| `amount-selector` | File from `shops/shared_menus/amount-selectors/`. |
| `bulk-buy` | File from `shops/shared_menus/bulk-buy/`. |
| `bulk-sell` | File from `shops/shared_menus/bulk-sell/`. |
| `purchase-confirmation` | File from `shops/shared_menus/purchase-confirmation/`. |
| `currencies` | Provider IDs from `currency.yml` exposed by this pack. |
| `size` | Inventory size. Use a multiple of 9. |
| `rows` | Alternative to `size`. |
| `items` | Menu items displayed in the pack menu. |

## Category Buttons

Use `type: SHOP_CATEGORY` to open a category file.

```yaml
minerals:
  type: SHOP_CATEGORY
  material: DIAMOND
  slot: 24
  display-name: "&bMinerals"
  shop: minerals
```

This opens:

```text
plugins/ZaminShop/shops/packs/<pack>/categories/minerals.yml
```

## Shared Menus

Each pack can use a different amount selector, bulk buy menu, bulk sell menu, or purchase confirmation menu.

```yaml
amount-selector: "compact.yml"
bulk-buy: "default.yml"
bulk-sell: "default.yml"
purchase-confirmation: "default.yml"
```

The amount selector above must exist here:

```text
plugins/ZaminShop/shops/shared_menus/amount-selectors/compact.yml
```
