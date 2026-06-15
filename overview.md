# What ZaminShop Does

ZaminShop is not just a single shop menu. It is a complete shop runtime made of shop packs, category menus, shared utility GUIs, transaction safety, and compatibility services.

## The high-level model

At runtime, the plugin is built around four layers:

1. **Shop packs**
   Each pack lives in its own folder under `plugins/ZaminShop/shops/<pack>/`.

2. **Category shop files**
   These define the actual purchasable and sellable items players interact with.

3. **Shared GUI menus**
   Sell, search, favorites, recent, amount selector, and bulk flows are configured separately and reused across the plugin.

4. **Protection systems**
   Automatic validation, transaction locking, rollback safety, Overwatcher, Runtime Shield, suspicious transaction detection, and sell limits protect the economy and the player experience.

## What players experience

Players typically see the plugin as:

- a main shop menu
- category pages
- search
- favorites
- recent transactions
- amount selectors
- bulk buy and bulk sell menus
- a sell GUI

The important part is that these are not isolated features. They are expected to work together.

Examples:

- a player searches inside the current shop pack, not across unrelated packs
- back buttons return to the correct previous menu context
- favorites and recent items remember the correct source item and pack context
- pagination items follow the same behavior rules across menus

## What admins manage

Admins work with:

- `config.yml` for global behavior
- `currency.yml` for named economy providers, item currency, and currency selection
- `overwatcher.yml` for static price auditing and Runtime Shield
- `lang/*.yml` for messages
- `guis/*.yml` for shared menus
- `shops/<pack>/main.yml` for pack-level presentation and commands
- `shops/<pack>/categories/*.yml` for actual shop content
- optional integrations such as PlaceholderAPI, Vault, custom item plugins, and spawner providers

That separation is intentional. It stops one giant config file from becoming the whole plugin.

## The design goals

### Pack isolation

Different shop experiences should not collapse into one file tree.

You should be able to run:

- a survival shop pack
- a donor shop pack
- an event shop pack

without mixing their commands, categories, and menus into one flat structure.

### Menu consistency

Search, recent, favorites, sell flows, and paged category menus should behave consistently:

- same placeholder rules
- same page control behavior
- same action system
- same disabled-state handling

### Economy safety

The plugin treats shop configuration as part of the economy, not just decoration.

That is why ZaminShop includes:

- validation
- Overwatcher
- Runtime Shield
- suspicious transaction checks
- transaction locks
- rollback-aware transaction flow
- sell limits

### Multi-version support

The plugin supports modern item naming and directives while still running on older runtimes where practical. Compatibility is handled through runtime-aware item resolution, not by forcing modern-only features into servers that cannot support them.

## Typical deployment patterns

### One server, one main shop

You register one pack, give it the command `/shop`, and build out categories such as:

- blocks
- ores
- food
- tools
- armor

### One server, multiple shop experiences

You keep gameplay stores separate:

- `/shop` for survival progression
- `/donator` for premium conveniences
- `/eventshop` for seasonal items

### Strict economy control

You rely on:

- sell limits
- suspicious transaction checks
- Overwatcher confirmations
- validation

to protect the server from config mistakes and player abuse.

## What to read next

- [Core Feature Areas](features.md)
- [Install and Launch Your First Shop](setup.md)
- [Files and Folder Layout](configuration/files-and-folders.md)
