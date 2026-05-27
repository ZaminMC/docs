# Transactions

Use this file for economy bugs, dupe bugs, rollback safety, or sell/buy behavior.

## Authority
- `ShopTransactionService` is the only allowed place for money/item movement.
- Commands, listeners, menus, and future search/favorite/recent flows must delegate into it.

## Current protections
- per-player transaction lock
- normalized price and balance checks
- explicit economy response validation
- rollback on failed item add or failed deposit path
- transaction state tracking and audit logging
- risk guard block checks
- sell limit enforcement
- suspicious sell blocking

## Primary files
- `src/main/java/com/zamin/zaminshop/service/transaction/ShopTransactionService.java`
- `src/main/java/com/zamin/zaminshop/service/transaction/TransactionContext.java`
- `src/main/java/com/zamin/zaminshop/service/transaction/TransactionLockService.java`
- `src/main/java/com/zamin/zaminshop/service/currency/CurrencyService.java`
- `src/main/java/com/zamin/zaminshop/service/limit/SellLimitService.java`
- `src/main/java/com/zamin/zaminshop/service/suspicious/SuspiciousTransactionService.java`
- `src/main/java/com/zamin/zaminshop/service/risk/RiskGuardService.java`
