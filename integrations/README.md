---
description: Connect ZaminShop to economy, item, placeholder, spawner, and utility plugins.
---

# Integrations

ZaminShop discovers supported integrations when the server starts. An integration is only loaded when its required plugin and API are available.

{% hint style="warning" %}
Adding an integration name to YAML does not install or enable the other plugin. Install the dependency, restart the server, and check the startup log before configuring shops that depend on it.
{% endhint %}

## Integration groups

| Group | Documentation | Used for |
| --- | --- | --- |
| Economy | [Economy providers](economies.md) | Money, points, tokens, experience, or physical-item balances |
| Physical currency | [Item currency](item-currency.md) | Inventory items used as the shop economy |
| Custom items | [Custom item providers](custom-items.md) | Buying, selling, and displaying items created by other plugins |
| Spawners | [Spawner providers](spawners.md) | Creating and matching mob spawner items |
| Placeholders | [PlaceholderAPI](placeholderapi.md) | Dynamic menu, shop, and transaction text |
| Utility hooks | [Utility hooks](utility-hooks.md) | Permissions, languages, stack sizes, and related compatibility |

## Startup order

Provider discovery happens during plugin startup. A normal `/zaminshop reload` reloads ZaminShop configuration, but it cannot make Bukkit load a missing dependency or register a plugin that was installed after startup.

Use a full server restart after:

- installing or removing an integration plugin;
- changing which plugin supplies an economy;
- changing the preferred external spawner provider;
- enabling a custom-item provider for the first time.

## Provider failures

If a configured custom item cannot be loaded, ZaminShop cannot create the corresponding shop item. Check:

1. the exact YAML key and capitalization documented on the provider page;
2. the external plugin's item ID;
3. whether the provider appears in the startup log;
4. whether the external plugin finished loading its item database.

HeadDatabase and ItemsAdder have late-loading support in ZaminShop. Their items may become available after those plugins signal that their item registries are ready.
