# What ZaminShop Does

ZaminShop gives your server a complete GUI-driven shop workflow rather than a single menu with items in it.

At player level, that means:

- open the main shop
- move through categories
- buy and sell items
- search the current pack
- use favorites and recent history
- use sell-focused convenience menus

At admin level, it means you can structure, protect, and maintain that whole experience without fighting the file layout every time the server grows.

## The player-facing experience

Players interact with ZaminShop as a system, not as isolated commands.

That system can include:

- a pack main menu
- category menus
- search results
- favorites
- recent item history
- amount selector
- bulk transaction menus
- sell GUI

The goal is to let common actions become faster over time instead of forcing players through the same slow path forever.

## The admin-facing experience

Server owners work with:

- manual pack registration
- pack-specific main menus
- category files
- shared GUI files
- global safety settings
- economy provider routing
- validation and risk checking

This makes the plugin easier to reason about when your server needs more than one shop experience.

## Where it fits best

ZaminShop is strongest on servers where the shop is part of the gameplay loop instead of a minor side utility.

Examples:

- survival servers with a central economy
- SMP servers with regular buying and selling
- prison-style setups where price balance matters
- mixed-mode networks with multiple shop themes
- donor or event packs that should stay isolated from the main progression store

## What separates it from a basic shop menu

The plugin is built around four practical concerns:

### 1. Structure

Shop packs keep different store experiences separate.

### 2. Speed

Search, favorites, recent history, amount selector, and bulk menus reduce repeated friction.

### 3. Safety

Transactions, pricing, suspicious activity, and sell volume all have explicit controls.

### 4. Maintainability

Manual registration, shared menu files, and validation tools make the plugin easier to expand without losing control of it.

## Typical server-owner use cases

### One clean survival shop

Register one pack, point `/shop` to that pack, tune the sell flow, and keep the category menus readable.

### Multiple shop packs

Use one pack for survival, one for donor content, one for limited-time events, and keep each experience separate.

### Strict economy administration

Use price modifiers, risk guard, sell limits, and transaction audit tools to keep the economy from drifting quietly into bad territory.

## Read next

- [Why ZaminShop Exists](why-zaminshop.md)
- [Core Feature Areas](features.md)
- [Install and Launch Your First Shop](setup.md)
