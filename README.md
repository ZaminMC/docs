# ZaminShop

ZaminShop is a pack-driven GUI shop plugin for Bukkit, Spigot, Paper, and legacy-compatible server stacks that need more than a single `/shop` menu.

It was built for server owners who care about three things at the same time:

- a polished player-facing shop experience
- an economy that does not quietly break under bad pricing or bad configs
- a file layout that still makes sense once the server grows beyond one category menu

## Why premium?

Good shop systems are not hard because of the first menu.

They are hard because of everything that happens after launch:

- prices drift over time
- admins add packs and event shops
- players find sell loops
- custom items and hooked items have to keep working across versions
- YAML mistakes should be readable, not a wall of SnakeYAML stack traces
- menu behavior has to stay consistent across search, recent, favorites, sell flows, and category shops

ZaminShop has been shaped around those production problems instead of pretending they are edge cases.

If your server needs a shop that feels deliberate, safe, and maintainable, this is what the plugin is built to do.

## What ZaminShop actually gives you

- self-contained shop packs loaded from `plugins/ZaminShop/shops/<pack>/`
- pack main menus plus category shop files
- configurable GUI menus for sell, search, favorites, recent, amount selector, and bulk flows
- shared pagination layouts with first-page, middle-page, last-page, and single-page behavior
- placeholder-aware menu rendering
- configurable category commands and subcommands
- transaction locking and rollback protection
- sell limits and suspicious transaction monitoring
- cross-shop and cross-pack risk guard checks
- multi-economy routing
- modern item directives with legacy runtime compatibility
- custom item and spawner hooks
- readable validation and startup diagnostics

## Who this plugin is for

ZaminShop is a strong fit for:

- survival servers with a real economy
- SMP servers where buy and sell volume matters
- prison or grind servers with heavy item throughput
- mixed-mode servers that want separate shop experiences
- donor or premium packs that must stay isolated
- seasonal servers that rotate shop content often

## Start here

### I want a shop online quickly

- [Install and Launch Your First Shop](setup.md)
- [First Shop Pack Walkthrough](shops/first-shop-pack.md)
- [Commands](commands.md)

### I want to understand the system before I configure it

- [Why ZaminShop Exists](why-zaminshop.md)
- [What ZaminShop Does](overview.md)
- [Core Feature Areas](features.md)

### I want to build my own packs and menus

- [Build Shop Packs](shops/README.md)
- [Shop Pack File Format](shops/shop-file-format.md)
- [Menu File Format](gui/menu-file-format.md)

### I want to protect the economy first

- [Safety, Risk Guard, and Audit](configuration/safety.md)
- [Sell Limits and Suspicious Transactions](configuration/sell-limits.md)
- [Price Modifiers](configuration/price-modifiers.md)

## Documentation standard

This wiki is written for operators, not just developers.

Each major section is meant to answer:

- what the feature does
- why it exists
- when to use it
- how to configure it
- common mistakes
- what happens at runtime

Where implementation details matter, they are explained. Where they do not, the docs stay focused on the job of running a real server.
