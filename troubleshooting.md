# Fixing Common Problems

This page focuses on symptoms, likely causes, and the fastest checks to run first.

## `/shop` does not open

Check:

1. the player has `zaminshop.player.shop`
2. the player's world is not blocked in `disableShopsInWorlds`
3. the player's gamemode is not blocked in `disableShopsInGamemodes`
4. `disableMainMenu` is not blocking the flow you expect
5. at least one folder under `plugins/ZaminShop/shops/` contains an enabled, valid `main.yml`

Then run:

```text
/zaminshop validate
```

## A shop pack is skipped

The usual causes are:

- folder missing
- `main.yml` missing
- invalid YAML in the pack files

Check the console startup warnings first, then validate again after fixing the file.

## Search returns nothing

Check:

- `config.yml -> search.enabled`
- whether the current pack actually contains matching shop items
- whether the player has `zaminshop.player.search`

Remember that `/shop search <query>` searches the current pack scope, not every possible pack automatically.

## Sell GUI does not open

Check:

- `zaminshop.player.sell-gui` permission
- `guis/gui-settings.yml -> sellGui.enabled`
- the sell GUI file path under `config.yml -> gui_menus.sell.file`

## Sell GUI opens but items are rejected

That usually means one of these:

- the item has no valid sell price
- the item metadata does not match what the shop expects
- the item is not part of any currently loaded sellable shop item

If the same item sells through one path and fails through another, validate the shop setup and inspect item comparison settings.

## Prices look wrong

Check these layers in order:

1. the base item price in the category file
2. the active economy type
3. player or command price modifiers
4. sell limits or suspicious transaction actions
5. number formatting and price rounding settings

## Items appear as barriers, air, or invalid placeholders

Most of the time this is caused by:

- invalid material names for the server version
- unsupported metadata on that server version
- menu items using bad placeholder-driven materials
- malformed YAML

Use:

```text
/zaminshop validate
/zaminshop check
```

and read the startup warnings closely.

## Risk guard blocks a shop or item

Run:

```text
/zaminshop risk list
```

Then decide whether to:

- fix the prices
- confirm the risk intentionally
- reset the risk state after cleanup

## GUI items leaked into a player inventory

The current command tree does not expose a manual sanitize command. ZaminShop automatically sanitizes GUI-owned items during managed menu close, player lifecycle, cursor, drag, drop, and reload paths.

If an item remains after a clean restart, preserve the item and console logs and report the exact menu and click sequence.

## Reload does not fix the issue

Reload is useful, but not everything should be treated as a reload problem.

Use reload when you changed:

- config values
- GUI files
- shop files
- language files

Use a full restart when:

- the `/sell` command registration changed
- you installed or removed a hook dependency
- startup failed before the runtime finished booting cleanly
