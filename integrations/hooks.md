# Item and Spawner Hooks

ZaminShop supports a range of optional integrations for custom items, external item ecosystems, and spawner handling.

## Why hooks matter

Hooks let the shop system work with more than plain vanilla materials.

That matters when your server uses:

- custom item plugins
- external weapon systems
- head databases
- custom spawner logic

## Supported item-side integrations in source

Current hook providers include support for ecosystems such as:

- Brewery
- CrackShot
- CraftEngine
- CustomItems
- ExecutableBlocks
- ExecutableItems
- HeadDatabase
- ItemsAdder
- MMOItems
- MythicMobs items
- Nexo
- Oraxen
- QualityArmory
- Slimefun
- WeaponMechanics

## Spawner handling

Spawner support is split between:

- internal handling
- external provider handling

That allows the plugin to work with both built-in spawner logic and supported external spawner providers.

## How optional hooks behave

Optional integrations are designed so that missing plugins do not crash ZaminShop startup.

That means:

- installed plugin present -> hook can activate
- plugin missing -> hook is skipped

## When to care about this page

You should read this section if:

- items are loading as invalid when they are not vanilla
- a custom item plugin was installed but shop items still do not resolve
- you are building a server that mixes several item ecosystems together
