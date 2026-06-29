# Currencies

Currencies are configured in `currency.yml`.

Shop packs choose which registered providers they expose.

## Default Provider

```yaml
default-provider: vault
```

## Provider Example

```yaml
providers:
  vault:
    type: VAULT
    enabled: true
    display-name: Vault
    icon:
      material: EMERALD
    prefix: "$"
    suffix: ""
```

## Provider Types

Confirmed economy types in code:

| Type | Used for |
| ---- | -------- |
| `VAULT` | Vault economy. |
| `INTERNAL` | ZaminShop internal SQL-backed provider. |
| `PLAYER_POINTS` | PlayerPoints. |
| `ITEM` | Item-backed currency. |
| `EXP` | Player experience points. |
| `EXP_LEVELS` | Player experience levels. |
| `EXCELLENT_ECONOMY` | ExcellentEconomy. |
| `COINS_ENGINE` | CoinsEngine. |
| `GEMS_ECONOMY` | GemsEconomy. |
| `MYSQL_TOKENS` | MySQL-Tokens. |
| `TOKEN_ENCHANT` | TokenEnchant. |
| `TOKEN_MANAGER` | TokenManager. |
| `VOTING_PLUGIN` | VotingPlugin. |
| `CUSTOM` | API-registered custom provider. |

## Item Currency

```yaml
providers:
  item:
    type: ITEM
    enabled: false
    display-name: Coins
    icon:
      material: EMERALD
    prefix: ""
    suffix: " Coins"
    decimal-places: 0
    denominations:
      emerald:
        value: 1
        item:
          material: EMERALD
      emerald-block:
        value: 9
        item:
          material: EMERALD_BLOCK
```

## Pack Currencies

In a shop pack `main.yml`:

```yaml
currencies:
  - vault
  - playerpoints
  - item
```

## Item Currency Provider

Use the provider ID on a shop item:

```yaml
diamond:
  type: SHOP_ITEM
  material: DIAMOND
  slot: 13
  buy-price: 250
  sell-price: 50
  currency-provider: vault
```

## Currency Selection

```yaml
currency-selection:
  enabled: true
  open-before-amount-selector: true
  remember-last-provider: true
  menu:
    title: "&8Choose Currency"
    rows: 3
    open-sound: UI_BUTTON_CLICK
    slots:
      - 11
      - 13
      - 15
```

When enabled, players can choose from the providers available to the shop pack or item.
