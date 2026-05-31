# What ZaminShop Does

ZaminShop lets players buy from and sell to server-managed shops through configurable menus.

That part is straightforward. What matters is how the plugin handles the details around it.

## Core feature areas

### Shop packs

ZaminShop does not treat all shops as one flat folder.

Instead, you register named shop packs in `config.yml`, and each pack has:

- one main menu
- one categories folder
- its own command scope and navigation flow

This is useful when you want clean separation between:

- survival shops
- prison shops
- donor or premium shops
- event or seasonal packs

### Shared GUI system

Shared GUI files define the recurring menus used across the plugin:

- amount selector
- bulk buy
- bulk sell
- favorites
- recent
- search
- sell GUI

This gives you consistent player UX without repeating the same layout inside every category shop.

### Buy and sell safety

ZaminShop is designed to keep economy actions centralized.

That matters because shop systems break when too many places can move money or items independently.

The plugin includes:

- transaction locking
- click cooldown protection
- currency validation
- risk guard
- suspicious transaction checks
- sell limits
- GUI-owned item cleanup

### Player convenience systems

The player-facing flow includes:

- favorites
- recent item history
- scoped search
- configurable pagination
- configurable sell GUI
- bulk buy and bulk sell menus

These systems are there to make repeated shopping faster instead of forcing players through the same clicks every time.

## Typical workflows

### New server setup

You install the plugin, register one pack, point `/shop` at that pack, tune economy and safety settings, then validate the setup before players join.

### Multiple server modes

You can keep separate shop packs for different gameplay modes instead of stuffing everything into one giant menu tree.

### Economy balancing

You can tune prices, add modifiers, use worth checks, and rely on risk guard to catch obviously dangerous configurations before they go live.

### High-volume sell environments

If your server has farms, grinders, or heavy mob drop income, the sell limit and suspicious transaction systems matter as much as the item prices themselves.

## Before you go deeper

If you are deciding whether the plugin fits your use case, focus on these sections next:

- [Install and Launch Your First Shop](setup.md)
- [Safety, Risk Guard, and Audit](configuration/safety.md)
- [Build Shop Packs](shops/README.md)
- [Customize Menus](gui/README.md)
