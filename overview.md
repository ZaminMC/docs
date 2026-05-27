# Total Overview

ZaminShop has four big layers:

## 1. Commands

Players mostly use `/shop` and `/sell`.

Admins use `/zaminshop` for reloads, validation, risk guard, language management, modifiers, item checks, and inventory sanitation.

## 2. Shops

Shop definitions live in `shops/*.yml`.

Each shop file controls:

- display name
- rows/size
- economy
- buy/sell GUI toggles
- per-shop messages
- permission/world restrictions
- item list

## 3. GUIs

Built-in menu files live in `guis/*.yml`.

The default menus include:

- shop directory
- amount selector
- bulk buy
- bulk sell
- favorites
- recent
- search
- sell GUI
- shared GUI settings

## 4. Safety Systems

ZaminShop is not only a menu renderer. It has backend safety layers:

- transaction-safety
- transaction-audit
- currency-safety
- risk-guard
- sell-limits
- suspicious-transactions
- GUI-owned item sanitation

These systems exist to reduce dupes, broken economies, bad YAML, and leaked GUI items.
