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

## Validate after editing

```text
/zaminshop validate
```

Permission:

```text
zaminshop.admin.validate
```

Validation reports configuration problems without requiring players to discover them through a failed transaction.

## Reload is appropriate for

- shop pack YAML changes;
- category item changes;
- menu layout changes;
- language file changes;
- most `config.yml` values;
- `gui-settings.yml`;
- price modifier configuration.

## Restart is required for

| Change | Reason |
| --- | --- |
| Install, remove, or upgrade an integration plugin | Bukkit plugin discovery and APIs are established during startup. |
| `disableCommands.sell` | Command registration happens during startup. |
| Add or remove a dynamically registered shop command | Bukkit command registration is a startup concern. |
| Change economy plugins or provider availability | Economy services and external APIs are discovered during startup. |
| Change the preferred external spawner provider | Provider registration occurs during startup. |
| Replace the ZaminShop JAR | Plugin classes must be loaded again. |

## Safe workflow

1. Edit one logical area at a time.
2. Run `/zaminshop validate`.
3. Correct every error tied to the changed files.
4. Run `/zaminshop reload`.
5. Test opening, buying, selling, permissions, and navigation with a non-op account.

{% hint style="warning" %}
Do not use Bukkit's `/reload` as a substitute for a controlled plugin reload or full restart. External plugin state, listeners, services, and scheduled tasks may not be reconstructed safely.
{% endhint %}

## Item currency changes

Changing denomination values or item identity does not migrate currency already held by players. Stop trading activity, update the definition, validate it, then reload. A restart is recommended when also changing the enabled `economyTypes` list.

## Failed reload

If the plugin reports invalid YAML or a failed shop load:

1. keep the console error;
2. inspect the exact path named in the message;
3. run `/zaminshop validate`;
4. restore the last known valid YAML if the error cannot be corrected immediately.
