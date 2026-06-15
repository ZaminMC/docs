# How the Runtime Fits Together

This page exists so addon developers and maintainers can understand the plugin's runtime boundaries without reading the entire source tree first.

## High-level flow

ZaminShop runtime is split into six practical areas:

1. bootstrap and reload
2. configuration snapshots and validation
3. currency and economy providers
4. pack and menu loading
5. player-facing menu sessions
6. transaction execution and safety

## Bootstrap and reload

Bootstrap owns:

- `config.yml`, `currency.yml`, and `overwatcher.yml` loading
- language loading
- GUI registry loading
- shop pack loading
- hook startup
- automatic lifecycle audits

Reload follows the same broad path, but it swaps runtime state instead of starting from a blank JVM.

## Configuration snapshots

Runtime services read immutable configuration snapshots rather than repeatedly
walking live YAML objects. Menu schema validators and compatibility validators
report malformed or unsupported definitions during startup and reload.

## Currency flow

Currency provider definitions are loaded before shops. Item prices are resolved
against the item, pack, legacy category economy, and configured default
provider. When multiple providers remain valid, the currency selection service
can open the provider menu before the amount selector.

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
- Runtime Shield purchase fingerprints
- sell-limit and suspicious-transaction checks

Do not bypass that boundary in your own integrations.

## Practical rule for developers

If your code needs to:

- open a menu -> use the API
- react to lifecycle or transaction moments -> use events
- change money or items -> let ZaminShop own that path
