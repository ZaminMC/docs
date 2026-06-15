# Version Compatibility

ZaminShop is designed to run across old and modern Minecraft server versions without forcing you to maintain separate config trees by hand.

## What compatibility covers

Compatibility in practice includes:

- material name resolution
- legacy durability/data handling
- sound resolution
- long-title and inventory capability differences
- custom model data support on newer servers

## Why this matters

A menu or shop file that looks correct on one server version may fail on another if the plugin does not normalize:

- materials
- sounds
- metadata expectations

ZaminShop uses runtime capability detection and compatibility validation to reduce those problems.

## Admin commands that help here

Use:

```text
/zaminshop reload
```

The validation output reports compatibility warnings such as:

- flattening differences
- missing modern capabilities
- material or sound resolution issues

## Practical advice

If you are supporting older servers:

- validate after every major menu or shop edit
- watch the startup warnings for compatibility resolution messages
- avoid assuming every modern material or sound exists on every server version

If you are targeting only modern servers, you can still benefit from the same validation flow because it catches bad names early.
