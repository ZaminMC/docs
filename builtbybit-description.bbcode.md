[CENTER][IMG]https://raw.githubusercontent.com/ZaminMC/ZaminShop/main/assets/zaminshop-banner.png[/IMG][/CENTER]

[CENTER][SIZE=7][B]ZaminShop[/B][/SIZE][/CENTER]
[CENTER][SIZE=4]A pack-driven GUI shop plugin built for serious server economies[/SIZE][/CENTER]

[HR][/HR]

[HEADING=2]Why premium?[/HEADING]

Running a good shop plugin is not hard for the first ten minutes.

The real work starts after launch:

[LIST]
[*]your server grows beyond one menu
[*]players start finding buy and sell loops
[*]custom items and spawners need to work cleanly
[*]you need search, favorites, recent history, and sell flows to feel connected
[*]bad YAML should not turn into unreadable parser spam
[*]reloads, validation, and version compatibility have to behave predictably
[/LIST]

ZaminShop was built around those real production problems.

It is designed for server owners who want a shop system that looks polished to players, stays manageable for staff, and protects the economy instead of quietly breaking it.

[HR][/HR]

[HEADING=2]What ZaminShop is[/HEADING]

ZaminShop is a [B]pack-driven shop system[/B].

Instead of forcing your whole economy into one flat config, it gives you:

[LIST]
[*]self-contained shop packs
[*]pack main menus
[*]category shop files
[*]shared GUI menus
[*]search, favorites, and recent history
[*]amount selector and bulk transaction flows
[*]sell GUI support
[*]transaction safety, rollback protection, and economy risk detection
[/LIST]

This makes it a strong fit for:

[LIST]
[*]survival servers
[*]SMP servers
[*]prison-style economies
[*]donor or premium shop packs
[*]event or seasonal stores
[*]servers that need multiple shop experiences without turning the config into a mess
[/LIST]

[HEADING=2]Core features[/HEADING]

[HEADING=3]Pack-based shop architecture[/HEADING]

Each shop pack lives in its own folder:

[CODE]plugins/ZaminShop/shops/&lt;pack&gt;/[/CODE]

Inside each pack:

[LIST]
[*][CODE]main.yml[/CODE] for the pack menu and command entry
[*][CODE]categories/*.yml[/CODE] for category shop pages
[/LIST]

This keeps:

[LIST]
[*]survival shops
[*]donor shops
[*]event shops
[*]seasonal content
[/LIST]

cleanly separated.

[HEADING=3]Modern GUI system[/HEADING]

ZaminShop includes configurable menus for:

[LIST]
[*]shop pack main menus
[*]category menus
[*]sell GUI
[*]search
[*]favorites
[*]recent history
[*]amount selector
[*]bulk buy
[*]bulk sell
[/LIST]

Menus support:

[LIST]
[*]custom decorative items
[*]page-specific items
[*]placeholder rendering
[*]requirements
[*]actions
[*]back navigation
[*]custom commands
[*]priority control
[/LIST]

[HEADING=3]Advanced pagination[/HEADING]

Pagination is layout-aware instead of rigid.

You can define:

[LIST]
[*][CODE]single-page[/CODE]
[*][CODE]first-page[/CODE]
[*][CODE]middle-page[/CODE]
[*][CODE]last-page[/CODE]
[/LIST]

This makes large menus feel intentional instead of mechanically repeated.

[HEADING=3]Search, favorites, and recent history[/HEADING]

Players can:

[LIST]
[*]search inside the current pack context
[*]favorite useful items
[*]revisit recently used items quickly
[/LIST]

This removes a lot of repeated friction for active players.

[HEADING=3]Sell workflows[/HEADING]

ZaminShop supports:

[LIST]
[*]normal selling
[*]sell GUI inventory flows
[*]amount selector selling
[*]bulk selling
[*]sell-all style workflows
[/LIST]

[HEADING=3]Economy safety systems[/HEADING]

ZaminShop includes real safety systems, not just menus:

[LIST]
[*]transaction locking
[*]rollback-aware inventory handling
[*]price normalization
[*]sell limits
[*]suspicious transaction monitoring
[*]Overwatcher price auditing with confirmation support
[*]Runtime Shield purchase tracking and unsafe-resale protection
[/LIST]

[HEADING=3]Overwatcher[/HEADING]

Overwatcher is designed to catch common economy mistakes before players exploit them.

It can detect:

[LIST]
[*]bad buy/sell relationships
[*]direct arbitrage
[*]cross-category arbitrage
[*]cross-pack arbitrage
[*]common compaction and crafting loops
[/LIST]

[HEADING=3]Version-aware item support[/HEADING]

The plugin supports modern config formats while still handling older runtime differences where practical.

It includes compatibility handling for:

[LIST]
[*]legacy block vs item splits
[*]color variants
[*]dyes
[*]heads
[*]spawn eggs
[*]banners and shields
[*]spawners
[/LIST]

[HEADING=3]Unified material directives[/HEADING]

You can define special materials through a single [CODE]material:[/CODE] path, including:

[LIST]
[*]normal materials
[*]player heads
[*]BaseHead values
[*]HeadDatabase entries
[*]texture heads
[*]ItemsAdder items
[*]Oraxen items
[*]Nexo items
[*]MMOItems items
[*]spawners
[*]placeholder-driven material values
[/LIST]

[HEADING=3]Optional integrations[/HEADING]

ZaminShop supports multiple optional integrations including:

[LIST]
[*]Vault
[*]PlaceholderAPI
[*]HeadDatabase
[*]Oraxen
[*]ItemsAdder
[*]Nexo
[*]MMOItems
[*]custom spawner providers
[*]other item hooks depending on your server stack
[/LIST]

[HEADING=3]Readable diagnostics[/HEADING]

YAML errors are easier to read than the usual raw parser dump.

Validation also catches:

[LIST]
[*]broken commands
[*]bad menu links
[*]invalid category targets
[*]unsupported item metadata
[*]pagination mistakes
[/LIST]

[HEADING=2]Who should buy this?[/HEADING]

Buy ZaminShop if you want:

[LIST]
[*]a polished shop plugin with real server-owner workflow in mind
[*]multiple shop packs without flat-config chaos
[*]better menu tooling than basic shop plugins
[*]stronger economy protection
[*]a modern config style with legacy-aware runtime handling
[/LIST]

[HEADING=2]Documentation[/HEADING]

Full documentation covers:

[LIST]
[*]installation
[*]shop packs
[*]category file format
[*]menu format
[*]pagination
[*]placeholders
[*]commands and permissions
[*]hooks and custom items
[*]automatic validation and Overwatcher auditing
[/LIST]

[HEADING=2]Summary[/HEADING]

ZaminShop is built for servers that want their shop to feel like a complete system instead of a single menu file.

If you need structure, safety, modern GUI control, and cleaner long-term maintenance, this is what the plugin was designed for.
