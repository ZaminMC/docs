# Troubleshooting

## Shops are not opening

Run:

```text
/zaminshop validate
```

Check:

- YAML syntax
- invalid material names
- missing economy plugin
- denied world/gamemode
- missing player permission
- `disableMainMenu`

## Console says startup failed

The command handler sends `MSG.STARTUPFAILED` when startup did not complete.

Fix the reported config/shop error in console, then restart or reload.

## Search returns nothing

Check:

```yaml
search:
  enabled: true
```

Also verify shops actually loaded with:

```text
/zaminshop validate
```

## Sell GUI does not open

Check:

```yaml
sellGui:
  enabled: true
  permission: "zaminshop.sellgui"
```

Then give the player:

```text
zaminshop.sellgui
```

## Risk guard blocks an item

Run:

```text
/zaminshop risk list
```

Fix the buy/sell prices, or confirm the risk intentionally.

## GUI items leaked into player inventory

Use:

```text
/zaminshop sanitize <player>
```

Permission:

```text
zaminshop.admin.sanitize
```

## Reload denied

Reload is denied while active transactions are locked. Wait until transactions finish, then run:

```text
/zaminshop reload
```

## `/sell` still exists after disabling it

`disableCommands.sell` requires a full server restart.
