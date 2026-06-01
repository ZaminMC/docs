# ZaminShop

ZaminShop is a premium-style, pack-driven GUI shop plugin for Bukkit, Spigot, and Paper servers.

It is built for servers that want their shop system to feel deliberate, polished, and safe instead of looking like a loose pile of menus and price files.

## What you get

- pack-based shop organization
- configurable category menus
- favorites and recent history
- scoped search
- sell GUI support
- bulk buy and bulk sell flows
- price modifiers
- suspicious transaction monitoring
- risk guard and sell-limit systems
- multiple economy provider support

## Why server owners use it

Most shop plugins can open a menu and sell an item.

The harder part is everything around that:

- keeping multiple shop experiences separated cleanly
- avoiding broken pricing that damages the economy
- letting players find items quickly instead of getting lost in categories
- controlling high-volume sell behavior on farm-heavy servers
- reloading safely without turning the plugin folder into a mess

ZaminShop is built around those real server problems.

## Start here

### I want `/shop` online quickly

- [Install and Launch Your First Shop](setup.md)
- [First Shop Pack Walkthrough](shops/first-shop-pack.md)
- [Commands](commands.md)

### I want to understand why the plugin is structured this way

- [Why ZaminShop Exists](why-zaminshop.md)
- [What ZaminShop Does](overview.md)
- [Core Feature Areas](features.md)

### I want to customize the experience

- [Build Shop Packs](shops/README.md)
- [Customize Menus](gui/README.md)
- [Common Server Setups](configuration/common-server-setups.md)

### I want to protect the economy before players touch the shop

- [Safety, Risk Guard, and Audit](configuration/safety.md)
- [Sell Limits and Suspicious Transactions](configuration/sell-limits.md)
- [Price Modifiers](configuration/price-modifiers.md)

## What kind of server is this for?

ZaminShop is a strong fit for:

- survival servers
- SMP communities
- prison-style economies
- mixed-mode networks
- donor or premium shop packs
- seasonal or event-driven shop rotations

## What makes it feel premium instead of improvised

### The shop is treated as a system

Categories, search, selling, favorites, and navigation are designed to work together.

### The economy is treated as a risk surface

Validation, transaction locks, risk guard, suspicious transaction monitoring, and sell limits exist because pricing mistakes and spam actions are real production problems.

### The file layout is built for growth

Shop packs, shared GUI files, and menu-specific responsibilities make the plugin easier to expand without turning one folder into a maintenance problem.

## Documentation philosophy

This wiki is written around server-owner goals:

- what the feature does
- why it exists
- when to use it
- how to configure it
- where people usually make mistakes

Implementation details exist where they are useful, but the main job of this wiki is to help you launch and maintain a shop system successfully.
