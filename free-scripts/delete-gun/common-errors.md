# Common Errors

## 🔴 The weapon is given but the gun doesn't delete anything

**Cause:** The player has the weapon but doesn't have the required permissions.

**Fix:** Make sure the permission system is correctly configured:

* **ACE:** Check that `add_ace group.yourgroup madonne.deletegun allow` is present in your `server.cfg` and that the player is in the correct group.
* **MadonnAdmin:** Ensure `MS_MadonnAdmin` is started **before** `MS_Delete_Gun` and that the player has a valid staff rank.
* **Custom:** Verify that your `GetPerms` function in `customs/perms.lua` returns `true` for the player.

***

## 🔴 The weapon is not automatically given on join

**Cause 1:** `AUTOMATICALLY_GIVE_WEAPON` is set to `false`.

**Fix:** Set it to `true` in `config/main.lua`.



**Cause 2:** The player doesn't have the required permissions, so the weapon is intentionally not given.

**Fix:** Grant the player the correct permission (see above).



**Cause 3 (ESX + ox\_inventory):** The `INVENTORY` option is not set correctly.

**Fix:** Make sure `FRAMEWORK` is set to `"esx"` and `INVENTORY` is set to `"ox"` if you are using ox\_inventory.

***

## 🔴 Notifications are not showing up

**Cause:** The `NOTIFICATION_TYPE` is set to a system that is not running on your server.

**Fix:** Either:

* Set `NOTIFICATION_TYPE` to `"auto"` to let the resource detect the available system automatically.
* Set it to `"default"` to use the native GTA V notification.
* If using `"other"`, make sure your custom handler is correctly defined in `customs/notifs.lua`.

***

## 🔴 Multi-mode command doesn't work

**Cause:** `ENABLE_MULTI_MODE` is set to `false`.

**Fix:** Set `ENABLE_MULTI_MODE` to `true` in `config/main.lua`, and make sure `config/modes.lua` is properly configured with at least one mode.

***

## 🔴 The resource loads but nothing happens (no weapon, no permissions)

**Cause:** The `INIT_DELAY` may be too short, causing the resource to check permissions before the player is fully loaded.

**Fix:** Increase the `INIT_DELAY` value in `config/main.lua` (e.g. set it to `3` or `5`).

> ⚠️ If you are using MadonnAdmin, an additional **10-second delay** is always applied on top of `INIT_DELAY`. This is normal behavior.

***

## 🔴 `MS_Delete_Gun` throws errors on start

**Cause:** A dependency resource is not started before `MS_Delete_Gun`.

**Fix:** Make sure your `server.cfg` starts resources in the correct order:

```cfg
ensure es_extended       # if using ESX
ensure ox_inventory      # if using ox_inventory
ensure MS_MadonnAdmin    # if using MadonnAdmin
ensure MS_Delete_Gun     # always last
```

***

## 🔴 You lack the required entitlement to use MS\_Delete\_Gun

This message indicates that your server does not have the necessary entitlement to start the resource. This is related to FiveM's **Escrow** protection system.

Check the following points one by one:

* ✅ The **CFX Portal key** listed in your `server.cfg` does not contain any typing error
* ✅ The CFX Portal key belongs to the **FiveM account that was used to purchase or claim** the resource
* ✅ The resource has been **successfully claimed** on the [CFX Portal](https://portal.cfx.re/)
* ✅ The CFX Portal key linked to your server **belongs to you**, and not to your hosting provider

> ⚠️ **Important warning about hosting provider keys**
>
> Some hosting providers include a shared CFX Portal key as part of their offers. We strongly advise against using such keys. A key that does not belong to you will block the use of **any resource protected by FiveM's Escrow system**, without exception — not just this one. Always use your own personal CFX Portal key.

***

## 💬 Still having issues?

If you are still experiencing problems after following the steps above, feel free to reach out to us:

* 💬 **Discord:** [discord.gg/madonne](https://discord.gg/madonne)
* 🌐 **Website:** [madonnestudio.com](https://madonnestudio.com/)
* 📧 **Email:** [contact@madonnestudio.com](mailto:contact@madonnestudio.com)
