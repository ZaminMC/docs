# Installation

## Install

1. Stop your server.
2. Put the ZaminShop jar in your `plugins` folder.
3. Install any optional plugins you want to use, such as Vault, PlaceholderAPI, HeadDatabase, Oraxen, ItemsAdder, or PlayerPoints.
4. Start the server.
5. Check the console for startup warnings.
6. Open `plugins/ZaminShop/` and review the generated files.

## First Boot

ZaminShop creates its default files on startup.

The important files are:

```text
plugins/ZaminShop/
├── config.yml
├── currency.yml
├── gui-settings.yml
├── lang/
├── menus/
├── shops/
└── webhooks/
```

The bundled starter shop is stored under:

```text
plugins/ZaminShop/shops/packs/survival_shop/
```

## Economy Setup

The default currency provider is `vault`.

If you use Vault, install Vault and a Vault-compatible economy plugin before starting the server.

If you want PlayerPoints or item currencies, enable them in `currency.yml`.

## Reloads

Use `/zaminshop reload` for normal config, menu, and shop changes.

Restart the server after:

* adding or removing integration plugins
* changing database settings
* replacing the ZaminShop jar
* large shop structure changes that affect commands
