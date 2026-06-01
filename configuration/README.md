# Configure the Plugin

This section is about turning a working plugin into a shop system that actually fits your server.

If installation gets ZaminShop online, configuration is what makes it usable, safe, and pleasant to maintain.

## What you configure here

Use this section when you want to:

- choose a database backend
- choose a default economy provider
- register shop packs
- point shared menus to custom file locations
- tune safety and sell-limits
- adjust how prices, sounds, and text behave globally

## Read this section in order

For most servers, this is the best sequence:

1. [config.yml Reference](config-yml.md)
2. [Files and Folder Layout](files-and-folders.md)
3. [Database Setup](database.md)
4. [Language and Messages](language.md)
5. [Safety, Risk Guard, and Audit](safety.md)
6. [Sell Limits and Suspicious Transactions](sell-limits.md)

## What does not belong here

If your goal is:

- building categories
- adding items
- changing main menu category buttons
- changing favorites, search, or sell menu layout

you should move to:

- [Build Shop Packs](../shops/README.md)
- [Customize Menus](../gui/README.md)

## Good admin mindset

Do not try to edit everything at once.

A stable workflow is:

1. set the economy and pack registrations
2. confirm the plugin boots cleanly
3. validate the setup
4. adjust safety systems
5. only then start polishing menus and category content
