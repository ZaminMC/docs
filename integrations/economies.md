# Economy Providers

ZaminShop supports multiple economy backends. This lets you use more than plain Vault money when your server design needs it.

## Supported economy types

The default config lists these built-in economy types:

- `EXP`
- `EXP_LEVELS`
- `VAULT`
- `GEMS_ECONOMY`
- `GRINGOTTS`
- `MYSQL_TOKENS`
- `PLAYER_POINTS`
- `TOKEN_ENCHANT`
- `TOKEN_MANAGER`
- `VOTING_PLUGIN`
- `COINS_ENGINE`

## How the default economy is chosen

`config.yml` uses an ordered list:

```yaml
economyTypes:
  - VAULT
```

The first valid entry becomes the default economy for the plugin.

## When to override per shop

Use a per-shop `economy` override when:

- one category should use points instead of cash
- one donor or event category uses a separate currency
- one server mode has a special economy path

## Practical advice

Do not add every possible provider just because it is supported.

Only enable the currencies your server actually intends to use. The simpler your economy routing is, the easier it is to balance and debug.
