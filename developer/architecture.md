# How the Runtime Fits Together

This page exists so addon developers and maintainers can understand the plugin's runtime boundaries without reading the entire source tree first.

## High-level flow

ZaminShop runtime is split into four practical areas:

1. bootstrap and reload
2. pack and menu loading
3. player-facing menu sessions
4. transaction execution and safety

## Bootstrap and reload

Bootstrap owns:

- config loading
- language loading
- GUI registry loading
- shop pack loading
- hook startup

Reload follows the same broad path, but it swaps runtime state instead of starting from a blank JVM.

## Menu flow

Menu rendering is server-side.

That means:

- GUI state lives in plugin-managed sessions
- click handling is validated before action execution
- GUI-owned items are protected from escaping into normal player inventories

## Shop pack flow

Each registered shop pack provides:

- one main menu
- one or more category menus

Category menus are menu definitions with shop-aware item types layered on top.

## Transaction boundary

The transaction system is the authority for:

- buy checks
- sell checks
- balance checks
- inventory mutation
- rollback behavior

Do not bypass that boundary in your own integrations.

## Practical rule for developers

If your code needs to:

- open a menu -> use the API
- react to lifecycle or transaction moments -> use events
- change money or items -> let ZaminShop own that path
