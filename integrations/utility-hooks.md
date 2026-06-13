---
description: Understand ZaminShop's non-economy integration points.
---

# Utility Hooks

ZaminShop declares optional compatibility with several plugins that support permissions, placeholders, item stacks, language handling, and other server functions.

## PlaceholderAPI

When PlaceholderAPI is installed, ZaminShop registers its expansion and resolves external placeholders in supported text.

[Placeholder reference](placeholderapi.md)

## Vault

Vault can serve two roles:

- economy provider through `VAULT`;
- permission bridge used by permission-purchase shop items.

A Vault-compatible permission plugin is required when selling permissions through Vault.

## LuckPerms

LuckPerms is recognized as an optional permission integration. Normal Bukkit permission checks still control commands, shops, items, and GUI requirements.

[Permission reference](../permissions.md)

## LanguageUtils

ZaminShop includes a language provider adapter for LanguageUtils. The adapter is loaded only when that plugin and API are available.

[Language configuration](../configuration/language.md)

## API-provided integrations

The public API supports custom registrations including economy and spawner providers. `CUSTOM` in the economy enum refers to an economy registered through that API; it is unrelated to the `CUSTOM` GUI item type.

[Developer API](../developer/api.md)

## Restart rule

Use a full server restart whenever an integration plugin is installed, removed, upgraded, or replaced. `/zaminshop reload` is for ZaminShop configuration and shop resources, not Bukkit dependency discovery.
