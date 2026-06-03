# Core Feature Areas

This page is the product tour. It explains the major systems in ZaminShop and why they exist.

## Shop packs

Shop packs are the top-level organization unit.

Each pack has:

- a `main.yml`
- a `categories/` folder
- its own display name
- its own command labels
- its own pack-scoped category commands

Use packs when you want to separate:

- game mode shops
- donor or premium shops
- event shops
- region-specific shops

## Category shop menus

Category files are where the actual shop items live.

A category file controls:

- menu title
- rows or inventory size
- category-only commands
- navigation items
- pagination slot layouts
- shop items
- custom decorative items

This is the layer players spend most of their time in.

## Shared utility GUIs

ZaminShop includes reusable menu systems for:

- amount selection
- bulk buy
- bulk sell
- search
- favorites
- recent transactions
- sell GUI

These menus are not hardcoded throwaways. They are configurable and support the same item, placeholder, action, and requirement systems used elsewhere in the plugin.

## Pagination system

Pagination is layout-aware.

Instead of assuming one fixed slot grid for every page, you can define:

- `single-page`
- `first-page`
- `middle-page`
- `last-page`

That lets your menus visually communicate:

- a one-page menu
- the beginning of a longer result set
- a middle page
- the end of a result set

It also supports item visibility controls such as page-specific display rules.

## Search, favorites, and recent history

These systems exist to reduce friction for repeat players.

### Search

Search helps players jump straight to a known item instead of walking category by category.

### Favorites

Favorites make repeat purchases faster and keep useful items one click away.

### Recent

Recent history helps players revisit items they actually used, not just items you expected them to use.

## Sell workflows

Selling is more than a `/sell all` shortcut.

ZaminShop supports:

- selling a specific item
- amount selector selling
- bulk sell menus
- sell GUI inventory workflows
- sell-all style flows depending on configuration

These systems are tied into the same safety rules as normal transactions.

## Safety systems

This is where ZaminShop separates itself from casual menu plugins.

### Transaction safety

- per-player transaction locking
- rollback-aware inventory handling
- invalid amount blocking
- inventory consistency checks

### Risk guard

Risk guard is designed to catch pricing mistakes before they turn into server-wide damage.

It looks for:

- suspicious sell > buy relationships
- direct arbitrage
- cross-category pricing issues
- cross-pack pricing issues
- known compaction and crafting loops

### Suspicious transaction monitoring

This watches player behavior patterns such as:

- extremely high sale volume
- repeated same-item sales
- rapid sale frequency
- unusual money earned in a short window

### Sell limits

Sell limits let you cap monetization pressure over a day or week without disabling selling entirely.

## Item compatibility and hooks

ZaminShop supports:

- normal Minecraft materials
- modern material directives
- player heads and texture-based heads
- spawners
- custom item hooks
- runtime-aware compatibility for older server versions

It also distinguishes between:

- what can be represented on a given server version
- what should fail cleanly with a useful warning

## Diagnostics and validation

The plugin validates configuration more aggressively than the average shop plugin.

That includes:

- command collisions
- invalid menu definitions
- broken shop category targets
- unsupported item metadata
- invalid pagination definitions
- broken YAML syntax with readable diagnostics

## Read next

- [Install and Launch Your First Shop](setup.md)
- [Shop Pack File Format](shops/shop-file-format.md)
- [Safety, Risk Guard, and Audit](configuration/safety.md)
