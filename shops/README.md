# Build Shop Packs

Shop packs are the top-level content unit in ZaminShop.

If you understand packs, categories, and shared menus, you understand the plugin.

## What a pack is

A pack is a folder under:

```text
plugins/ZaminShop/shops/<pack>/
```

Each pack normally contains:

- `main.yml`
- `categories/`

The pack is responsible for:

- its display identity
- its entry commands
- its pack-level main menu
- the category set it exposes to players

## Why packs exist

Packs solve a real problem:

servers often need more than one store experience.

Examples:

- a normal survival shop
- a donor shop
- a seasonal event shop
- a rank-only shop

Trying to manage all of that in one flat menu and one flat list of files gets messy quickly.

## What belongs in `main.yml`

Your pack `main.yml` is usually where you define:

- whether the pack is enabled
- the pack display name
- the pack root commands
- top-level custom buttons
- category buttons
- links to shared menus such as sell, favorites, recent, or search

Think of `main.yml` as the landing page for the pack.

## What belongs in `categories/*.yml`

Category files define the actual pages players browse and purchase from.

That includes:

- title
- rows or size
- pagination
- previous/next/back buttons
- shop items
- custom filler or decorative items
- category-only commands

## Pack design recommendations

### Keep each pack focused

A pack should answer one design question clearly.

Good pack themes:

- survival progression
- donor convenience
- event rotation
- skill or profession store

### Keep categories readable

Players should understand the category list quickly.

Good categories:

- blocks
- ores
- food
- farming
- armor
- tools
- drops
- miscellaneous

### Use category commands deliberately

Category commands are useful, but they should reflect player behavior:

- a frequently used category can justify its own direct command
- everything does not need a standalone root command

## Related pages

- [First Shop Pack Walkthrough](first-shop-pack.md)
- [Shop Pack File Format](shop-file-format.md)
- [Adding Shop Items](shop-items.md)
