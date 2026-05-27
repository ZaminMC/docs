# Developer API

Public API root:

```text
com.zamin.zaminshop.api
```

Static access point:

```java
import com.zamin.zaminshop.api.ZaminShop;
import com.zamin.zaminshop.api.ZaminShopAPI;

ZaminShopAPI api = ZaminShop.getApi();
api.openShopDirectory(player);
api.openShop(player, "blocks", 1);
```

API files from source:

## `DefaultShopCategory.java`

```java
package com.zamin.zaminshop.api;

import java.util.Collection;
import java.util.stream.Collectors;
import com.zamin.zaminshop.feature.shop.Shop;

final class DefaultShopCategory implements ShopCategory {
    private final Shop shop;

    DefaultShopCategory(Shop shop) {
        this.shop = shop;
    }

    @Override
    public String getId() {
        return this.shop.getId();
    }

    @Override
    public String getDisplayName() {
        return this.shop.getName();
    }

    @Override
    public Collection<ShopItem> getItems() {
        return this.shop.getShopItems().stream()
            .map(DefaultShopItem::new)
            .collect(Collectors.toList());
    }
}
```

## `DefaultShopItem.java`

```java
package com.zamin.zaminshop.api;

final class DefaultShopItem implements ShopItem {
    private final com.zamin.zaminshop.feature.shop.item.ShopItem item;

    DefaultShopItem(com.zamin.zaminshop.feature.shop.item.ShopItem item) {
        this.item = item;
    }

    @Override
    public String getId() {
        return this.item.getId();
    }

    @Override
    public org.bukkit.inventory.ItemStack getItemStack() {
        return this.item.getItem();
    }

    @Override
    public double getBuyPrice() {
        return this.item.getBuyPrice();
    }

    @Override
    public double getSellPrice() {
        return this.item.getSellPrice();
    }
}
```

## `DefaultZaminShopAPI.java`

```java
package com.zamin.zaminshop.api;

import java.util.Collection;
import java.util.Collections;
import java.util.Optional;
import java.util.stream.Collectors;
import com.zamin.zaminshop.bootstrap.ZaminShopRuntime;
import com.zamin.zaminshop.feature.shop.Shop;
import org.bukkit.entity.Player;

final class DefaultZaminShopAPI implements ZaminShopAPI {
    private final ShopManager shopManager = new DefaultShopManager();

    @Override
    public ShopManager getShopManager() {
        return this.shopManager;
    }

    @Override
    public void openShopDirectory(Player player) {
        ZaminShopRuntime.openShopDirectory(player);
    }

    @Override
    public void openShop(Player player, String shopId, int page) {
        ZaminShopRuntime.openShop(player, shopId, page);
    }

    private static final class DefaultShopManager implements ShopManager {
        @Override
        public Collection<ShopCategory> getShops() {
            if (ZaminShopRuntime.getPlugin() == null || !ZaminShopRuntime.getPlugin().getShopManager().areShopsLoaded()) {
                return Collections.emptyList();
            }

            return ZaminShopRuntime.getPlugin().getShopManager().getShops().stream()
                .map(DefaultShopCategory::new)
                .collect(Collectors.toList());
        }

        @Override
        public Optional<ShopCategory> getShop(String id) {
            Shop shop = ZaminShopRuntime.getShop(id);
            return shop == null ? Optional.empty() : Optional.of(new DefaultShopCategory(shop));
        }

        @Override
        public void openShopDirectory(Player player) {
            ZaminShopRuntime.openShopDirectory(player);
        }

        @Override
        public void openShop(Player player, String id, int page) {
            ZaminShopRuntime.openShop(player, id, page);
        }
    }
}
```

## `ShopCategory.java`

```java
package com.zamin.zaminshop.api;

import java.util.Collection;

/**
 * Public read-only shop category view.
 */
public interface ShopCategory {
    String getId();

    String getDisplayName();

    Collection<ShopItem> getItems();
}
```

## `ShopItem.java`

```java
package com.zamin.zaminshop.api;

import org.bukkit.inventory.ItemStack;

/**
 * Public read-only shop item view.
 */
public interface ShopItem {
    String getId();

    ItemStack getItemStack();

    double getBuyPrice();

    double getSellPrice();
}
```

## `ShopManager.java`

```java
package com.zamin.zaminshop.api;

import java.util.Collection;
import java.util.Optional;
import org.bukkit.entity.Player;

/**
 * Public shop access facade.
 */
public interface ShopManager {
    Collection<ShopCategory> getShops();

    Optional<ShopCategory> getShop(String id);

    void openShopDirectory(Player player);

    void openShop(Player player, String id, int page);
}
```

## `ZaminShop.java`

```java
package com.zamin.zaminshop.api;

/**
 * Static access helper for the new ZaminShop API facade.
 */
public final class ZaminShop {
    private static final ZaminShopAPI API = new DefaultZaminShopAPI();

    private ZaminShop() {
    }

    public static ZaminShopAPI getApi() {
        return API;
    }
}
```

## `ZaminShopAPI.java`

```java
package com.zamin.zaminshop.api;

import org.bukkit.entity.Player;

/**
 * Stable public entry point for addon developers.
 */
public interface ZaminShopAPI {
    ShopManager getShopManager();

    void openShopDirectory(Player player);

    void openShop(Player player, String shopId, int page);
}
```
