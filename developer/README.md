# Developer Guide

This section explains the supported integration boundary and the runtime behavior developers need to preserve when extending ZaminShop.

Start with:

- [Developer API](api.md) for supported entry points and loaded shop access
- [How the Runtime Fits Together](architecture.md) for bootstrap, menu, pack, and transaction ownership
- [Transaction Flow and Safety Rules](transactions.md) before adding code that buys, sells, grants, or removes anything
- [Version Compatibility](version-compat.md) when working with Bukkit APIs, materials, metadata, or legacy server versions

Prefer the public API over internal classes. Internal menu and transaction components may change as compatibility fixes are added, while the public boundary is intended for external plugins.
