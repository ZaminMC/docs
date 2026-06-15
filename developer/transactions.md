# Transaction Flow and Safety Rules

This page is for developers and server owners who need to understand how ZaminShop protects buy and sell operations.

## Why this exists

Shop plugins fail when they let too many systems move money and items independently.

ZaminShop keeps transaction logic centralized so it can enforce:

- lock protection
- cooldown checks
- balance validation
- sell-limit checks
- suspicious transaction checks
- rollback on failure

## What the transaction system owns

The transaction layer is responsible for:

- validating whether a buy or sell may happen
- checking permission and risk state
- talking to the active economy provider
- adding or removing items
- aborting or rolling back when a downstream step fails

## Safety rules for integrations

If you build against ZaminShop:

- do not withdraw money yourself and then call a menu action
- do not add bought items directly from a listener
- do not remove sold items directly from a menu handler

If you bypass the transaction boundary, you also bypass the plugin's safety model.

## Protections currently in play

- per-player transaction lock
- click cooldown
- normalized price checks
- economy response validation
- rollback on failed inventory add or failed sell deposit
- provider-specific currency resolution
- Overwatcher blocking
- Runtime Shield purchase fingerprints and resale checks
- sell-limit enforcement
- suspicious transaction monitoring

## Practical admin takeaway

If a player reports:

- duplicated items
- missing sale money
- blocked purchases
- blocked sell-all actions

check:

1. `config.yml -> transaction-safety`
2. `currency.yml -> safety`
3. `overwatcher.yml`
4. `config.yml -> sell-limits`
5. `config.yml -> suspicious-transactions`

Then reload, read the automatic validation report, and use `/zaminshop overwatcher list`.
