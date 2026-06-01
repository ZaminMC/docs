# Core Feature Areas

This page is the fast product tour.

If you want to understand what the plugin is capable of before going into file syntax, start here.

## Pack-driven shop architecture

ZaminShop organizes shops into manually registered packs.

Each pack can have:

- its own main menu
- its own category files
- its own command scope
- its own navigation flow

Use this when your server needs clean separation between different shop experiences.

## Category-based buying and selling

The core shopping flow lives in category menus.

These menus handle:

- shop items
- pricing
- pagination
- category navigation
- custom menu items

This is the layer players interact with most often, so keeping it readable and structured matters.

## Shared convenience menus

ZaminShop includes reusable shared menus for:

- amount selector
- bulk buy
- bulk sell
- sell GUI
- favorites
- recent history
- search

These menus exist to reduce repetitive clicks and help players reach items faster.

## Search, favorites, and recent history

These are quality-of-life systems, but they are also retention systems.

They help players:

- find items without remembering categories
- repeat purchases faster
- keep personal shortcuts through favorites
- return to items they use often

On larger servers, these systems matter more than admins usually expect.

## Sell GUI flow

The sell GUI gives players a dedicated place to process sellable items using the normal pricing system.

This is useful when:

- players sell in large volumes
- you want a clearer selling workflow than command-only actions
- you want better sell-related menu control

## Price and economy controls

The plugin supports:

- multiple economy providers
- price modifiers
- price validation
- risk guard rules
- sell limits
- transaction audit logging

This is the part that keeps the plugin operational instead of merely functional.

## Strong runtime safety

ZaminShop is designed to treat transaction safety seriously.

That includes:

- transaction locks
- click cooldowns
- economy response checks
- rollback-aware handling
- suspicious transaction monitoring
- safe menu ownership rules

These systems are what separate a presentable demo from a plugin that survives real player traffic.

## Menu customization

The menu system is meant to be configurable without turning into a maintenance nightmare.

Server owners can customize:

- menu titles
- rows and size
- item slots
- pagination layouts
- click actions
- navigation items
- built-in shared menus

## Where to go next

Choose the next page based on what you care about:

- [Build Shop Packs](shops/README.md)
- [Customize Menus](gui/README.md)
- [Safety, Risk Guard, and Audit](configuration/safety.md)
- [Economy Providers](integrations/economies.md)
