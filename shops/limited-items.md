# Limited Items

Not every item should be freely sellable forever.

This page covers the ways ZaminShop can limit item-driven economy output.

## Why limited items exist

Limits are useful when:

- one farmable item can dominate your economy
- one rare item should stay rare even if players automate production
- you want one category to be generous but another to be tightly controlled

## Per-item sell caps

ZaminShop supports sell-side limits directly on shop items through recognized limit paths such as:

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

These limit how much a player can sell or earn through that item path.

## Global sell limits

If the problem is server-wide rather than item-specific, use:

```yaml
sell-limits:
```

inside `config.yml`.

Global limits are usually better when your server has many farmable items and you want one consistent policy.

## When to use per-item vs global limits

Use per-item limits when:

- one or two items are the problem
- you want more precise tuning

Use global limits when:

- the whole sell economy needs hard caps
- you want simpler rules for staff and players
