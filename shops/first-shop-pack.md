# First Shop Pack Walkthrough

This page shows the simplest practical path to building your first usable shop pack.

## Step 1: register the pack

In `config.yml`:

```yaml
shops:
  survival:
    folder: survival_shop
    enabled: true
    file: main.yml
```

## Step 2: create the folder

Create:

```text
plugins/ZaminShop/shops/survival_shop/
  main.yml
  categories/
```

## Step 3: build the main menu

Your `main.yml` is the entry point for the pack.

It should usually contain:

- one or more category buttons
- a sell button
- favorites button
- recent button

Minimal example:

```yaml
menu_title: "&8Survival Shop"
rows: 6

items:
  category_blocks:
    type: SHOP_CATEGORY
    material: GRASS_BLOCK
    slot: 20
    display-name: "&eBlocks"
    shop: blocks
```

## Step 4: add the first category file

Create:

```text
plugins/ZaminShop/shops/survival_shop/categories/blocks.yml
```

Minimal example:

```yaml
menu_title: "&8Blocks"
rows: 6

pagination:
  shop-item-slots:
    - 10-16
    - 19-25
    - 28-34

items:
  stone:
    type: SHOP_ITEM
    material: STONE
    amount: 64
    quantity: 64
    buy-price: 10
    sell-price: 2

  back:
    type: BACK
    material: BARRIER
    slot: 49
    display-name: "&cBack"
    left_click_actions:
      - "[back]"
```

## Step 5: validate

Run:

```text
/zaminshop validate
```

If the plugin reports issues, fix those first before adding more categories.

## Step 6: expand

Once one category works, repeat the same pattern for:

- food
- ores
- tools
- armor

## Common mistakes

### The category button does nothing

Check that:

- the category file exists
- the category file name matches the `shop:` target
- the pack loaded cleanly

### The pack folder exists but nothing opens

Make sure the folder is registered in `config.yml`. ZaminShop will not load an unregistered folder just because it exists.
