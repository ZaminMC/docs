---
description: Know when to reload ZaminShop and when a complete server restart is required.
---

# Reloading and Restarts

## Reload command

```text
/zaminshop reload
```

Permission:

```text
zaminshop.admin.reload
```

The command can be run by a player or the console.

## Automatic validation

Validation runs during startup and `/zaminshop reload`. The removed `/zaminshop validate` command is not used in version `1.20.0`.

Read both console blocks after reloading:

```text
ZaminShop: Validation
ZaminShop: Overwatcher
```

## Reload is appropriate for

- shop pack YAML changes;
- category item changes;
- menu layout changes;
- language file changes;
- most `config.yml` values;
- `currency.yml`;
- `overwatcher.yml`;
- `gui-settings.yml`;
- price modifier configuration.

## Restart is required for

| Change | Reason |
| --- | --- |
| Install, remove, or upgrade an integration plugin | Bukkit plugin discovery and APIs are established during startup. |
| `disableCommands.sell` | Command registration happens during startup. |
| Change economy plugins or provider availability | Economy services and external APIs are discovered during startup. |
| Change the preferred external spawner provider | Provider registration occurs during startup. |
| Replace the ZaminShop JAR | Plugin classes must be loaded again. |

## Safe workflow

1. Edit one logical area at a time.
2. Run `/zaminshop reload`.
3. Read the automatic Validation and Overwatcher reports.
4. Correct every error tied to the changed files.
5. Test opening, buying, selling, permissions, currency selection, and navigation with a non-op account.

{% hint style="warning" %}
Do not use Bukkit's `/reload` as a substitute for a controlled plugin reload or full restart. External plugin state, listeners, services, and scheduled tasks may not be reconstructed safely.
{% endhint %}

## Item currency changes

Changing denomination values or item identity does not migrate currency already held by players. Stop trading activity, update `currency.yml`, then reload and review automatic validation. Restart when also installing, removing, or replacing an economy plugin.

## Failed reload

If the plugin reports invalid YAML or a failed shop load:

1. keep the console error;
2. inspect the exact path named in the message;
3. use the automatic report to correct the named path;
4. restore the last known valid YAML if the error cannot be corrected immediately.

On a failed menu reload, ZaminShop restores the previous working configuration snapshot.
