# FAQ

## Does ZaminShop require Vault?

No. ZaminShop does not require Vault to start.

Vault is needed if you use the `VAULT` currency provider.

## Can I use multiple currencies?

Yes. Register providers in `currency.yml`, then list provider IDs in the shop pack `currencies` section.

## Can I use custom items?

Yes. Confirmed providers include HeadDatabase, Oraxen, Nexo, ItemsAdder, MMOItems, MythicMobs, Slimefun, CraftEngine, CrackShot, QualityArmory, WeaponMechanics, CustomItems, Brewery, ExecutableItems, and ExecutableBlocks.

## Can I make multiple shops?

Yes. Use multiple shop packs under `shops/packs/`.

## Does it support older Minecraft versions?

ZaminShop includes legacy material and inventory compatibility code. Use material names that match your server version and test custom item features on your target version.

## Can I reload without restarting?

Use `/zaminshop reload` for normal config, shop, menu, and language changes.

Restart after changing installed plugins, database settings, command registration layout, or the plugin jar.

## Can players exploit buy and sell prices?

ZaminShop includes price checks, transaction locks, click cooldowns, suspicious transaction checks, and sell limits. Keep safety settings enabled.

## Can I use PlaceholderAPI?

Yes. Install PlaceholderAPI and use `%zaminshop_<placeholder>%` or placeholders from other plugins in supported text fields.

## Can I make rank-only shops?

Yes. Use menu requirements or permission checks.

```yaml
view-requirement:
  requirements:
    vip:
      type: has permission
      permission: "group.vip"
```
