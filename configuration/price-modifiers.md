# Price Modifiers

Price modifiers let you adjust prices for a specific player without rewriting the base shop files.

They are useful for:

- VIP discounts
- temporary boosts
- event pricing
- staff-applied punishments or recovery adjustments
- testing economy changes on a single player first

## Where they are controlled

Global behavior is controlled in `config.yml`:

```yaml
priceModifiersType: BOTH
displayPriceModifiersInPercents: true
```

Stored modifiers live in:

```text
plugins/ZaminShop/pricemodifiers.yml
```

## What the values mean

Modifier values are decimal multipliers.

| Value | Meaning |
|---:|---|
| `0.5` | 50% of the base price |
| `0.9` | 10% discount |
| `1.0` | normal price |
| `2.0` | double price |

## Types of modifier targets

ZaminShop supports modifiers for:

- one item
- one shop
- the player's global price context

And each modifier can target:

- buy price
- sell price
- both

## Commands

Add modifiers:

```text
/zaminshop addmodifier item <player> <shop> <item> <value> [buy|sell]
/zaminshop addmodifier shop <player> <shop> <value> [buy|sell]
/zaminshop addmodifier global <player> <value> [buy|sell]
```

Remove or reset modifiers:

```text
/zaminshop resetmodifier item <player> <shop> <item> [buy|sell]
/zaminshop resetmodifier shop <player> <shop> [buy|sell]
/zaminshop resetmodifier global <player> [buy|sell]
```

Check a player's active modifiers:

```text
/zaminshop checkmodifiers <player>
```

## When to use shop-level vs item-level modifiers

Use shop-level modifiers when:

- you want a whole category discounted
- you are running an event on one shop only

Use item-level modifiers when:

- one item needs special treatment
- you are correcting one problem item without touching the rest of the category

## Common mistakes

### Using modifiers as a replacement for fixing bad base prices

Modifiers are a tool, not a permanent excuse for broken base pricing.

If every player needs the same modifier forever, change the base shop price instead.

### Forgetting that sell modifiers affect economy extraction

Higher sell values can become more dangerous than lower buy values. Always re-check risk guard when heavy sell-side modifiers are in play.
