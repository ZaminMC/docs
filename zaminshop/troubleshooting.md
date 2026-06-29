# Troubleshooting

## Plugin Did Not Start

Check:

* the server is running a supported Bukkit/Spigot/Paper version
* the jar is inside `plugins/`
* the console does not show YAML load errors
* optional plugins are installed before ZaminShop if your config depends on them

## Commands Do Not Work

Check:

* the command is enabled in `config.yml`
* the command label is not used by another plugin
* the player has the required permission
* dynamic commands were reloaded or the server was restarted

For pack commands:

```yaml
open_command: shop
register_command: true
```

## Menu Does Not Open

Check:

* the file is in the correct folder
* `size` is a multiple of 9
* actions use valid tokens
* requirements pass
* the menu passed validation

## Item Does Not Appear

Check:

* the slot is inside the menu size
* the item has a supported `type`
* the material exists on your Minecraft version
* `view-requirement` is not hiding the item
* another item with a higher priority is not using the same slot

## Material Does Not Work

Use Bukkit material names for your server version.

For custom items, make sure the provider plugin is installed and the key format is correct.

Examples:

```yaml
material: STONE
material: hdb-12345
material: oraxen-example_item
material: itemsadder-namespace:item
material: mmoitems-MATERIAL:EXAMPLE
```

## Economy Provider Not Detected

Check:

* the provider plugin is installed
* `currency.yml` has the provider enabled
* the shop pack lists the provider ID under `currencies`
* Vault has a registered economy if using `VAULT`

## Placeholder Not Replacing

Check:

* PlaceholderAPI is installed for external placeholders
* the placeholder is valid in that context
* local amount placeholders are only used in amount selector menus
* shop/item placeholders require a shop or item context

## Search Input Not Working

Check:

* `shops.search.enabled` is `true`
* `gui-settings.yml` input mode is valid
* ProtocolLib is installed if you rely on sign input
* the fallback input mode is valid

## Reload Did Not Apply Changes

Run:

```text
/zaminshop reload
```

Restart the server after changing:

* installed plugins
* database settings
* command registration layout
* the ZaminShop jar

## YAML Errors

Check indentation first.

Correct:

```yaml
items:
  stone:
    type: SHOP_ITEM
    material: STONE
```

Wrong:

```yaml
items:
stone:
type: SHOP_ITEM
```
