# GUI System

Use this file for click handling, menu routing, session bugs, or inventory exploit checks.

## Rules
- GUI items are visuals, not authority.
- Slot actions are registered server-side on the menu session.
- Unsafe click types and drag actions are rejected in `PlayerListener`.
- Old sessions must fail after reload through snapshot version checks.

## Primary files
- `src/main/java/com/zamin/zaminshop/bootstrap/listener/PlayerListener.java`
- `src/main/java/com/zamin/zaminshop/gui/menu/MenuSession.java`
- `src/main/java/com/zamin/zaminshop/gui/menu/ShopMenuSession.java`
- `src/main/java/com/zamin/zaminshop/gui/menu/AmountSelectorMenu.java`
- `src/main/java/com/zamin/zaminshop/gui/menu/BulkAmountSelectorMenu.java`
- `src/main/java/com/zamin/zaminshop/feature/shop/ShopDirectoryMenu.java`
