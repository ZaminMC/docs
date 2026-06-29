# Example Shops

## Basic Shop Pack

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

size: 27

items:
  filler:
    type: CUSTOM
    material: GRAY_STAINED_GLASS_PANE
    slots:
      - 0-8
      - 18-26
    display-name: "&r"

  blocks:
    type: SHOP_CATEGORY
    material: GRASS_BLOCK
    slot: 11
    display-name: "&aBlocks"
    shop: blocks

  food:
    type: SHOP_CATEGORY
    material: APPLE
    slot: 15
    display-name: "&eFood"
    shop: food
```

## Category

```yaml
menu_title: "&8Blocks"
size: 27

items:
  stone:
    type: SHOP_ITEM
    material: STONE
    slot: 10
    buy-price: 16
    sell-price: 4

  oak_log:
    type: SHOP_ITEM
    material: OAK_LOG
    slot: 11
    buy-price: 24
    sell-price: 6

  back:
    type: BACK
    material: BARRIER
    slot: 22
    display-name: "&cBack"
```

## Rank Shop Button

```yaml
vip_items:
  type: CUSTOM
  material: DIAMOND
  slot: 13
  display-name: "&bVIP Items"
  view-requirement:
    requirements:
      vip:
        type: has permission
        permission: "group.vip"
  left-click-actions:
    - "[shop] vip_items"
```

## Multi-Currency Item

```yaml
nether_star:
  type: SHOP_ITEM
  material: NETHER_STAR
  slot: 13
  buy-price: 100
  sell-price: 25
  currency-provider: playerpoints
```

## HeadDatabase Item

```yaml
coin_head:
  type: SHOP_ITEM
  material: hdb-12345
  slot: 14
  buy-price: 1000
  sell-price: 100
```

## Search Button

```yaml
search:
  type: CUSTOM
  material: COMPASS
  slot: 49
  display-name: "&eSearch"
  lore:
    - "&7Search all shop items."
  left-click-actions:
    - "[open] search"
```

## Custom Amount Input Button

```yaml
custom_amount:
  type: AMOUNT_SIGN
  material: OAK_SIGN
  slot: 22
  display-name: "&eCustom Amount"
  lore:
    - "&7Amount: &f%amount_input%"
    - "&7Cost: &f%cost% %currency%"
    - "&eLeft-click &7confirm this amount."
    - "&eRight-click &7change the amount."
```
