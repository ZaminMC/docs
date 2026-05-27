# Architecture

ZaminShop focuses on clean separation between:

- GUI rendering
- Transactions
- Search indexing
- Configuration loading
- Compatibility layers

---

# Core Principles

## Atomic Transactions
Balance updates and item grants should remain synchronized.

## Performance
Avoid unnecessary inventory rebuilds.

## Compatibility
Support older and newer Minecraft versions.

## Extensibility
Design APIs for future integrations.
