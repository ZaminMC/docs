# Favorites and Recent Menus

These two menus exist to reduce repeat navigation.

They are not just cosmetic extras. They are the fastest way for regular players to get back to the items they actually use most.

## Favorites

Command:

```text
/shop favorites
```

Aliases:

```text
/shop fav
/shop favorite
```

Permission:

```text
zaminshop.player.favorite
```

### What it is for

Favorites are best for:

- items a player buys often
- items a player sells often
- cross-category shortcuts

### How players add favorites

Use the current configured favorite click mapping in the shop flow. On the current defaults, that flow is built around dedicated click behavior instead of forcing players to open a separate editor.

## Recent

Command:

```text
/shop recent
```

Aliases:

```text
/shop history
/shop transactions
```

Permission:

```text
zaminshop.player.recent
```

### What it is for

Recent history is useful when a player wants to:

- re-buy something from a different category quickly
- find the last thing they sold
- revisit frequently used materials without searching again

### Global settings

```yaml
recent-menu:
  enabled: true
  max-records-per-player: 20
  show-bought: true
  show-sold: true
```

## Why these menus matter together

- favorites are intentional
- recent is automatic

That combination gives players both a curated shortcut list and a short-term memory of what they just did.

## Customization advice

Keep both menus fast to scan.

Good layouts usually include:

- item name
- shop name
- buy price
- sell price
- one usage hint line

Do not overload them with too much decorative text.
