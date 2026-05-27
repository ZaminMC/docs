# Limited Items

The source supports sell-side item limits through item fields and global sell limit services.

## Per-item sell caps

Recognized item keys:

```yaml
maximum:
  items:
    player:
      can:
        sell: 100
  money:
    by:
      selling:
        player:
          can:
            make: 5000
```

The loader recognizes these paths as:

```text
maximum.items.player.can.sell
maximum.money.by.selling.player.can.make
```

## Global sell limits

Use `sell-limits` in `config.yml` for daily/weekly money and item caps.

## Practical use

Limited items are useful for:

- preventing farm abuse
- limiting rare-event economy damage
- controlling high-value sell items
- creating rotating market caps
