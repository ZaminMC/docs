---
description: Configure the economy providers used to charge and reward players.
---

# Economy Providers

`economyTypes` is an ordered list in `config.yml`. ZaminShop attempts to enable each listed provider, and the first enabled entry becomes the default economy for shops that do not select another provider.

```yaml
economyTypes:
  - VAULT
```

## Supported types

| Type | Required plugin | Stored value |
| --- | --- | --- |
| `EXP` | None | Total Minecraft experience points |
| `EXP_LEVELS` | None | Minecraft experience levels |
| `ITEM` | None | Configured items in the 36 storage slots |
| `VAULT` | Vault and a Vault economy | Vault balance |
| `EXCELLENT_ECONOMY` | ExcellentEconomy | The provider's `coins` currency |
| `GEMS_ECONOMY` | GemsEconomy | Gems |
| `MYSQL_TOKENS` | MySQLTokens | Tokens |
| `PLAYER_POINTS` | PlayerPoints | Points |
| `TOKEN_ENCHANT` | TokenEnchant | Tokens |
| `TOKEN_MANAGER` | TokenManager | Tokens |
| `VOTING_PLUGIN` | VotingPlugin | Voting points |
| `COINS_ENGINE` | CoinsEngine | The provider's `coins` currency |
| `CUSTOM` | Registered through the ZaminShop API | A provider supplied by another plugin |

`EXP_LEVELS`, MySQLTokens, PlayerPoints, TokenManager, and VotingPlugin operate on whole-number values in their provider implementations. Use integer prices with them. The default `config.yml` also explicitly recommends integer prices for `EXP_LEVELS`.

## Enabling more than one economy

```yaml
economyTypes:
  - VAULT
  - PLAYER_POINTS
  - ITEM
```

In this example:

- `VAULT` is the default;
- shops may select `PLAYER_POINTS` or `ITEM`;
- all three providers must load successfully before they can be used.

## Selecting an economy in a shop

A shop can select an enabled economy by type:

```yaml
shop:
  economy: PLAYER_POINTS
```

The exact shop file location depends on the pack:

```text
plugins/ZaminShop/shops/<pack>/categories/<shop>.yml
```

{% hint style="warning" %}
An economy named in a shop must also be enabled in `economyTypes`. Installing its dependency alone does not add it to ZaminShop's enabled economy list.
{% endhint %}

## Vault setup

Vault is an adapter, not an economy by itself. A working Vault setup requires:

1. Vault;
2. a Vault-compatible economy plugin;
3. `VAULT` in `economyTypes`;
4. a full server restart after installing the plugins.

## Physical item currency

`ITEM` uses exact Bukkit item similarity and rewrites recognized denominations to make change. Its configuration and inventory rules are documented separately:

[Configure item currency](item-currency.md)

## Currency labels

ZaminShop assigns built-in suffixes such as ` points`, ` tokens`, ` gems`, ` exp`, and ` exp levels`. Vault uses the formatting exposed by its economy provider. Item currency uses:

```yaml
item-currency:
  display-name: Coins
```

## Reload requirement

Use a full restart after installing, removing, or replacing an economy plugin. Configuration-only changes can be reloaded, but a restart is safer when changing the set or order of `economyTypes`, because plugin service registration is performed during startup.

## Common mistakes

### Using the old `GRINGOTTS` value

`GRINGOTTS` is not present in the current `EconomyType` enum and is not a supported `economyTypes` value.

### Naming a provider that is not installed

The type is only usable when its API loads. Read the startup error and verify the dependency's exact plugin version.

### Using decimals with integer providers

Use whole-number prices for providers backed by integer or long APIs.

### Assuming list order is cosmetic

The first available economy is the default. Reordering the list changes shops that do not define their own economy.
