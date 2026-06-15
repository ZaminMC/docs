---
description: Understand the automatic validation and audit reports printed at startup and after every successful reload.
---

# Automatic Validation

ZaminShop validates the active configuration automatically. There is no `/zaminshop validate` command in version `1.20.0`.

Validation runs:

- during plugin startup;
- after `/zaminshop reload`;
- before a new configuration snapshot replaces the currently working snapshot.

## What is checked

The lifecycle audit combines three independent reports:

1. **Configuration compatibility**
   Checks configuration structure and server capabilities.
2. **Menus**
   Checks menu roots, item definitions, pagination, actions, requirements, commands, and material directives.
3. **Shops**
   Loads shop packs, categories, and items while collecting file-specific warnings and errors.

After those checks, Overwatcher audits the loaded prices separately.

## Reading the report

The console prints a bounded summary:

```text
################ ZaminShop: Validation ################
Status: PASSED
Configuration: 0 error(s), 0 warning(s)
Menus: 0 error(s), 0 warning(s)
Shops: 8 loaded, 120 items, 0 error(s), 0 warning(s)
######################################################
```

Possible validation statuses:

- `PASSED`: no errors or warnings;
- `PASSED WITH WARNINGS`: configuration loaded, but review is recommended;
- `FAILED`: at least one validation error exists.

The report prints at most ten detailed validation issues. When more exist, the console states how many additional issues were omitted from the summary.

## Reload protection

ZaminShop loads configuration into a snapshot. If a reload fails during menu validation, the plugin restores the previous working snapshot and menu registry instead of leaving the runtime partially updated.

The reload command is also denied while a transaction lock is active.

## Recommended workflow

1. Edit the required YAML files.
2. Run:

   ```text
   /zaminshop reload
   ```

3. Read the complete `ZaminShop: Validation` block in the console.
4. Fix every error.
5. Review warnings before allowing players to trade.
6. Read the following `ZaminShop: Overwatcher` report.

{% hint style="warning" %}
Do not use examples that instruct administrators to run `/zaminshop validate`. That command was removed when validation became part of startup and reload.
{% endhint %}

## Related pages

- [Reloading and Restart Requirements](configuration/reloading.md)
- [Transaction Safety and Overwatcher](configuration/safety.md)
- [Troubleshooting](troubleshooting.md)
