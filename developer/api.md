# Developer API

This page is for plugin developers who want to open shops or inspect loaded shop data from their own code.

## What the public API is for

Use the public API when you want to:

- open the main shop for a player
- open a specific shop page
- inspect loaded shop categories
- inspect public shop item views

Use Bukkit events if you need to react to transactions or post-load lifecycle moments.

## Entry point

```java
import com.zamin.zaminshop.api.ZaminShop;
import com.zamin.zaminshop.api.ZaminShopAPI;

ZaminShopAPI api = ZaminShop.getApi();
```

## Open the main shop

```java
api.openShopDirectory(player);
```

## Open a specific shop

```java
api.openShop(player, "default:blocks", 1);
```

If your server only uses one pack, you can still normalize your own integrations around the scoped shop id format so future multi-pack changes do not break your code.

## Read loaded shops

```java
api.getShopManager().getShops();
api.getShopManager().getShop("default:blocks");
```

Public shop category views expose:

- id
- display name
- public item collection

Public item views expose:

- item id
- display item stack
- buy price
- sell price

## What the API does not expose

The public API is intentionally small.

It is not meant to give direct control over:

- transaction internals
- menu session internals
- inventory listener internals
- persistence internals

If you need to integrate with player purchases or sales, use the Bukkit event layer and keep money or item mutations inside ZaminShop's own transaction flow.

## Stability note

The public API package is:

```text
com.zamin.zaminshop.api
```

Build against that package only. Do not depend on internal runtime packages unless you are intentionally maintaining a private integration that you are willing to update across plugin changes.
