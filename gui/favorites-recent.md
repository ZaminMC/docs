# Favorites & Recent

## Favorites

Command:

```text
/shop favorites
```

Permission:

```text
zaminshop.player.favorite
```

Aliases:

```text
/shop fav
/shop favorite
```

Default messages:

```yaml
MSG.FAVORITES.EMPTY: "You do not have any favorite items yet."
MSG.FAVORITE.ADDED: "Added &c%item%&f to favorites."
MSG.FAVORITE.REMOVED: "Removed &c%item%&f from favorites."
```

## Recent

Command:

```text
/shop recent
```

Permission:

```text
zaminshop.player.recent
```

Aliases:

```text
/shop history
/shop transactions
```

Config:

```yaml
recent-menu:
  enabled: true
  max-records-per-player: 20
  show-bought: true
  show-sold: true
```
