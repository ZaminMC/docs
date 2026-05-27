# Price Modifiers

Default source file:

```yaml
# Price modifiers for ZaminShop categories and items.
priceModifiers: { }
```

Price modifiers are controlled by:

```yaml
priceModifiersType: BOTH
displayPriceModifiersInPercents: true
```

Command subcommands:

```text
/zaminshop addmodifier item <player> <shop> <item> <value> [buy|sell]
/zaminshop addmodifier shop <player> <shop> <value> [buy|sell]
/zaminshop addmodifier global <player> <value> [buy|sell]

/zaminshop resetmodifier item <player> <shop> <item> [buy|sell]
/zaminshop resetmodifier shop <player> <shop> [buy|sell]
/zaminshop resetmodifier global <player> [buy|sell]

/zaminshop checkmodifiers <player>
```

Modifier values are decimal multipliers:

| Value | Meaning |
|---:|---|
| `0.5` | half price |
| `0.9` | 10% discount |
| `1.0` | normal price |
| `2.0` | double price |
