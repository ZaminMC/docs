# Creating Shops

## Basic Example

```yaml
diamond:
  material: DIAMOND
  buy-price: 100
  sell-price: 50
```

---

# Modern Pricing

ZaminShop uses:

- `buy-price`
- `sell-price`

Negative prices are rejected.

---

# Display vs Transaction Amounts

```yaml
amount: 64
quantity: 1
```

- `amount` → GUI display amount
- `quantity` → actual transaction amount

---

# Tips

- Keep pricing balanced
- Use categories
- Avoid giant single-file shops
