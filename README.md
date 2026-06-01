# ZaminShop

ZaminShop is a configurable, pack-driven GUI shop plugin for Bukkit, Spigot, and Paper servers.

At the most basic level, it lets players:

- browse shop categories
- buy items
- sell items
- search for items
- revisit recent purchases
- favorite commonly used items

That is the visible part.

The reason ZaminShop is built the way it is comes from everything that happens behind those clicks:

- multiple shop packs
- different server modes
- price balancing
- safe sell handling
- player convenience menus
- economy protection
- reload-safe configuration workflows

## What the plugin is designed for

ZaminShop fits servers that want a shop system to feel like part of the server, not a disconnected utility menu.

That includes:

- survival servers
- SMP communities
- prison-style economies
- mixed-mode networks
- custom packs or donor stores that should stay separated from the default survival shop

## Core strengths

### Pack-driven design

Instead of treating the whole shop as one giant folder, ZaminShop lets you register named packs manually in `config.yml`.

That gives you predictable control over:

- what loads
- what stays disabled
- which pack owns which command scope
- how categories are grouped

### Shared GUI system

Search, favorites, recent history, amount selector, bulk buy, bulk sell, and sell GUI flows are all editable in their own shared files.

That means the plugin can feel polished without forcing every category menu to repeat the same layout logic.

### Transaction safety

Buying and selling are not scattered across menus and listeners.

The plugin includes:

- per-player transaction locks
- click cooldown protection
- rollback-aware transaction flow
- economy response validation
- suspicious transaction monitoring
- sell limits
- risk guard validation

### Server-owner workflow

ZaminShop is meant to support the way servers are actually maintained:

- edit files
- validate changes
- review price risk
- reload when safe
- keep pack structure organized

## Read this first

If you are starting fresh:

1. [Install and Launch Your First Shop](setup.md)
2. [Configure the Plugin](configuration/README.md)
3. [Build Shop Packs](shops/README.md)
4. [Customize Menus](gui/README.md)
5. [Commands](commands.md)
6. [Fixing Common Problems](troubleshooting.md)

## Recommended reading by goal

### I just want `/shop` working

Read:

- [Install and Launch Your First Shop](setup.md)
- [Shop Packs](shops/README.md)
- [First Shop Pack Walkthrough](shops/first-shop-pack.md)

### I want the menus to look better

Read:

- [Customize Menus](gui/README.md)
- [Built-in Menus](gui/built-in-menus.md)
- [GUI Settings](gui/gui-settings.md)

### I want to keep the economy safe

Read:

- [Safety, Risk Guard, and Audit](configuration/safety.md)
- [Sell Limits and Suspicious Transactions](configuration/sell-limits.md)
- [Price Modifiers](configuration/price-modifiers.md)

## Documentation scope

This wiki is written from the current ZaminShop source and bundled files.

It does not document imaginary features, and it does not organize the user-facing documentation around Java implementation names. The goal is simple:

help server owners, admins, and developers make the plugin successful on a real server.
