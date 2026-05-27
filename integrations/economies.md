# Economy Providers

Supported economy types listed by the default config:

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

Example:

```yaml
economyTypes:
  - VAULT
```

The first economy in `economyTypes` becomes the default economy provider.

Individual shops may override economy using the shop `economy` key.
