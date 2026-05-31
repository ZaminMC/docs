# ZaminShop

ZaminShop is a configurable, pack-driven shop plugin for Bukkit, Spigot, and Paper servers.

It is built for servers that want more than a basic buy and sell menu. The plugin gives you:

- manual shop pack control instead of automatic folder guessing
- shared GUI files for consistent player experience
- category-based shop menus
- search, favorites, recent history, and sell GUI flows
- multiple economy providers
- transaction locking and rollback-focused safety
- sell limits, suspicious transaction alerts, and risk guard checks
- PlaceholderAPI integration
- a public API for addons

## Why ZaminShop exists

Running a shop plugin on a live server is rarely just about listing items.

You usually also need to solve:

- how to organize several shop packs cleanly
- how to stop risky or broken price setups
- how to keep sell systems from becoming exploit machines
- how to let players move quickly between categories, search, recent items, and favorites
- how to keep menus editable without turning the config into a mess

ZaminShop is built around those real server-owner problems.

## What makes it different

### Pack-based shop system

Shops are grouped into manually registered packs. That gives you predictable control over what loads and what does not.

### Shared menu architecture

Amount selector, bulk buy, bulk sell, favorites, search, recent history, and sell GUI menus are all separate editable files.

### Centralized transaction safety

Buy and sell behavior is guarded by:

- per-player transaction locks
- economy response validation
- rollback-aware transaction execution
- sell limits
- suspicious transaction checks
- risk guard validation

### Modern placeholder and menu flow

The plugin supports dynamic menus, pagination layouts, context placeholders, and shared action handling without forcing every menu to be hardcoded.

## Read this first

If you are starting fresh, go in this order:

1. [Install and Launch Your First Shop](setup.md)
2. [Configure the Plugin](configuration/README.md)
3. [Build Shop Packs](shops/README.md)
4. [Customize Menus](gui/README.md)
5. [Commands](commands.md)
6. [Fixing Common Problems](troubleshooting.md)

## Documentation scope

This wiki is written from the current ZaminShop source and bundled files.

It does not try to document imaginary features, and it does not treat internal class names as the product structure. The goal is to help:

- server owners
- administrators
- builders and content pack authors
- plugin developers

get real work done with the plugin.
