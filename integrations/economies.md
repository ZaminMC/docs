---
description: Register economy implementations as named currency providers and expose them to shop packs.
---

# Economy Providers

Economies are registered in:

```text
plugins/ZaminShop/currency.yml
```

Each provider has:

- a provider ID chosen by the server owner;
- an implementation `type`;
- an enabled state;
- player-facing display settings.

## Supported types

| Type | Required plugin or source | Stored value |
|---|---|---|
| `EXP` | None | Total Minecraft experience points |
| `EXP_LEVELS` | None | Minecraft experience levels |
| `ITEM` | None | Configured physical inventory items |
| `VAULT` | Vault and a Vault economy | Vault balance |
| `EXCELLENT_ECONOMY` | ExcellentEconomy | Its `coins` currency |
| `GEMS_ECONOMY` | GemsEconomy | Gems |
| `MYSQL_TOKENS` | MySQL-Tokens | Tokens |
| `PLAYER_POINTS` | PlayerPoints | Points |
| `TOKEN_ENCHANT` | TokenEnchant | Tokens |
| `TOKEN_MANAGER` | TokenManager | Tokens |
| `VOTING_PLUGIN` | VotingPlugin | Voting points |
| `COINS_ENGINE` | CoinsEngine | Its `coins` currency |
| `CUSTOM` | ZaminShop API registration | External custom provider |

Whole-number provider implementations should use integer prices. This applies to `EXP_LEVELS`, MySQL-Tokens, PlayerPoints, TokenManager, and VotingPlugin.

## Single-currency Vault setup

`plugins/ZaminShop/currency.yml`:

```yaml
default-provider: vault

providers:
  vault:
    type: VAULT
    enabled: true
    display-name: Money
    icon:
      material: EMERALD
    prefix: "$"
    suffix: ""
```

`plugins/ZaminShop/shops/survival_shop/main.yml`:

```yaml
menu_title: "&8Survival Shop"
open_command:
  - shop
currencies:
  - vault
size: 54
```

Vault is an adapter, not an economy. Install Vault and a Vault-compatible economy plugin, then restart the server.

## Registering several providers

```yaml
default-provider: vault

providers:
  vault:
    type: VAULT
    enabled: true
    display-name: Money
    icon:
      material: EMERALD
    prefix: "$"
    suffix: ""

  points:
    type: PLAYER_POINTS
    enabled: true
    display-name: Points
    icon:
      material: NETHER_STAR
    prefix: ""
    suffix: " points"
```

Provider IDs are `vault` and `points`. The type names remain `VAULT` and `PLAYER_POINTS`.

## Selecting providers in a pack

```yaml
currencies:
  - vault
  - points
```

The pack list controls which registered providers its categories inherit.

See [Multi-Currency Shops](../shops/multi-currency.md) for complete price examples.

## Legacy category economy

Category files still accept:

```yaml
economy: PLAYER_POINTS
```

This is a compatibility route based on an implementation type. New multi-currency packs should use provider IDs in the pack `currencies` list.

## Physical item currency

The `ITEM` type uses exact configured items from the player's 36 normal inventory slots. See [Built-in Item Currency](item-currency.md).

## Reloading

Use:

```text
/zaminshop reload
```

after configuration-only changes. Restart after installing, removing, or replacing an economy plugin.

## Common mistakes

### Using provider types where IDs are required

Given:

```yaml
providers:
  points:
    type: PLAYER_POINTS
```

the pack value is:

```yaml
currencies:
  - points
```

not `PLAYER_POINTS`.

### Enabling a provider without its dependency

The implementation cannot register when the external API is unavailable. Read the startup hook and validation output.

### Using `GRINGOTTS`

`GRINGOTTS` is not a current `EconomyType` value.

### Copying the removed primary layout

`economyTypes` remains a compatibility fallback, but current installations should use `currency.yml`.
