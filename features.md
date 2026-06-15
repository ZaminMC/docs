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

Each pack can also restrict the currency providers its items may use. See
[Multi-Currency Shops](shops/multi-currency.md).

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

### Overwatcher

Overwatcher audits loaded prices before players can exploit a mistake.

It looks for:

- suspicious sell > buy relationships
- direct arbitrage
- cross-category pricing issues
- cross-pack pricing issues
- known compaction and crafting loops

Critical findings can block the affected shops until an administrator corrects
or explicitly confirms the finding.

### Runtime Shield

Runtime Shield signs purchased items with their source price and currency
provider. When the same item is offered to ZaminShop again, the signature is
checked before the sale is allowed. This closes profitable resale paths that a
static price audit cannot prove in advance.

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

The plugin validates configuration automatically during startup and reload.

That includes:

- command collisions
- invalid menu definitions
- broken shop category targets
- unsupported item metadata
- invalid pagination definitions
- broken YAML syntax with readable diagnostics

## Multi-currency shops

One installation can expose multiple enabled providers, including Vault,
PlayerPoints, and item-backed currencies. A shop pack can restrict the
providers available to its items, while an individual item can pin one provider
or define a separate price for each provider.

When more than one provider is valid for an item, ZaminShop can open a
configurable currency selection menu before the amount selector.

## Physical shop blocks

Administrators can link a placed block to a shop pack or category. Players can
then open that shop by interacting with the block instead of typing a command.
The linking tool, access permission, left-click information, and block-breaking
behavior are configurable.

## Read next

- [Install and Launch Your First Shop](setup.md)
- [Shop Pack File Format](shops/shop-file-format.md)
- [Transaction Safety and Overwatcher](configuration/safety.md)
