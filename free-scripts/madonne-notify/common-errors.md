# Common Errors

## 🔴 Notifications are not showing up

**Cause 1:** `MS_Madonne_Notify` is not started on your server.

**Fix:** Make sure the resource is added to your `server.cfg` and started before any resource that depends on it:

```cfg
ensure MS_Madonne_Notify
```



**Cause 2:** The resource started but the NUI page failed to load.

**Fix:** Check your server console for any errors related to `MS_Madonne_Notify`. Make sure the `ui/` folder is present and intact in the resource directory.

***

## 🔴 Export call throws an error

**Cause:** The resource name in the export call doesn't match the actual folder name.

**Fix:** Make sure you are using the exact resource name. The correct call is:

```lua
exports['MS_Madonne_Notify']:Notify(...)
```

Double-check that the folder is named `MS_Madonne_Notify` (case-sensitive on Linux servers).

***

## 🔴 Server-side export doesn't send the notification to the player

**Cause:** The `target` parameter is incorrect or the player is no longer connected.

**Fix:** Make sure you are passing a valid active server ID. Use `source` inside a server event handler, or verify the player is still online before triggering.

```lua
-- Correct server-side usage
exports['MS_Madonne_Notify']:Notify(source, "info", "Title", "Message", 5000, false)
```

***

## 🔴 The notification appears but no sound plays

**Cause:** The `sound` parameter is set to `false` or omitted.

**Fix:** Pass `true` as the last parameter:

```lua
exports['MS_Madonne_Notify']:Notify("success", "Title", "Message", 5000, true)
```

***

## 🔴 You lack the required entitlement to use MS\_Madonne\_Notify

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
