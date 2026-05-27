# FAQ

## Why does `/zaminshop` sometimes not behave like `/shop`?

The command handler checks the actual command label. If the label is literally `shop`, it uses the player shop command flow. Otherwise it uses the admin/main command flow.

## What command should players use?

Use:

```text
/shop
```

## What command should admins use?

Use:

```text
/zaminshop
```

## How do I verify my setup?

Run:

```text
/zaminshop validate
/zaminshop risk list
```

## Why is my shop blocked?

Risk guard can block dangerous economy setups. Check:

```text
/zaminshop risk list
```

Then fix the shop or confirm the risk with:

```text
/zaminshop risk confirm <riskId>
```

## How do I open the sell GUI?

```text
/shop sell
```

The default permission is:

```text
zaminshop.sellgui
```

## Where do I edit menus?

```text
plugins/ZaminShop/guis/
```

## Where do I edit shops?

```text
plugins/ZaminShop/shops/
```

## Does ZaminShop support PlaceholderAPI?

Yes. Identifier:

```text
zaminshop
```

## Does `/sell` need a restart to disable?

Yes. `disableCommands.sell` requires a full server restart.
