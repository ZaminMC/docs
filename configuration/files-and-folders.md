# Files and Folder Layout

This page explains where everything belongs and why the plugin is structured this way.

## Root folder

ZaminShop stores its files in:

```text
plugins/ZaminShop/
```

The important sub-areas are:

- `config.yml`
- `lang/`
- `guis/`
- `shops/`

## `config.yml`

This is the global runtime configuration.

Use it for:

- database settings
- enabled economy types
- startup logging
- transaction safety
- currency safety
- risk guard
- sell limits
- suspicious transaction checks
- search and recent behavior
- GUI file locations
- sell command behavior
- formatting and number settings

Do not use `config.yml` to register packs in newer setups. Shop packs are now self-contained in their own folders.

## `lang/`

Language files live here.

Example:

```text
plugins/ZaminShop/lang/en_US.yml
```

Use language files for:

- player messages
- admin messages
- validation output
- risk list formatting
- button text
- menu fallback text

## `guis/`

Shared menu files live here.

Common files:

- `amount-selector.yml`
- `bulk-buy.yml`
- `bulk-sell.yml`
- `favorites.yml`
- `recent.yml`
- `search.yml`
- `sell.yml`
- `gui-settings.yml`

These are global reusable menus, not pack-local category files.

## `shops/`

This is the main content directory.

Each folder under `shops/` is a shop pack.

Example:

```text
plugins/ZaminShop/shops/survival_shop/
  main.yml
  categories/
    blocks.yml
    ores.yml
    farming.yml
```

### `main.yml`

The pack main menu file usually controls:

- pack display name
- pack root commands
- top-level category buttons
- links to shared menus

### `categories/*.yml`

Each category file is a real shop page.

These files define:

- category title
- category commands or subcommands
- pagination
- navigation items
- shop items
- category-specific decorative items

## Raw docs copies

In the documentation repository you may also see `raw/` copies of example or mirrored files.

These are for reference and documentation support, not live server runtime.

## Recommended organization strategy

### One pack per server mode

Good examples:

- `survival_shop`
- `donator_shop`
- `event_shop`

### One category file per gameplay purpose

Good examples:

- `blocks.yml`
- `ores.yml`
- `food.yml`
- `farming.yml`

Avoid giant category files that mix unrelated economies.

## Common mistakes

### Treating `shops/` like one flat folder

Packs should be folders, not a pile of unrelated YAML files.

### Editing shared GUI files when the problem is a category

If the issue is:

- item pricing
- category navigation
- pack command structure

then the fix is usually in `shops/`, not `guis/`.

### Leaving old pack assumptions in place

Modern ZaminShop setups do not require `config.yml -> shops:` registration.

## Related pages

- [config.yml Reference](config-yml.md)
- [Shop Pack File Format](../shops/shop-file-format.md)
- [Menu File Format](../gui/menu-file-format.md)
