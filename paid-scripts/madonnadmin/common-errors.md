# Common Errors

## 🔴 You lack the required entitlement to use MS\_MadonnAdmin

This message indicates that your server does not have the necessary entitlement to start the resource. This is related to FiveM's **Escrow** protection system.

Check the following points one by one:

* ✅ The **CFX Portal key** listed in your `server.cfg` does not contain any typing error
* ✅ The CFX Portal key belongs to the **FiveM account that was used to purchase or claim** the resource
* ✅ The resource has been **successfully claimed** on the [CFX Portal](https://portal.cfx.re/)
* ✅ The CFX Portal key linked to your server **belongs to you**, and not to your hosting provider

> ⚠️ Some hosting providers include a shared CFX Portal key as part of their offers. A key that does not belong to you will block the use of **any Escrow-protected resource**, without exception. Always use your own personal key.

***

## 🔴 Error 0xA01 — Failed to initialize Madonn'Admin

```
[ERROR - #0xA01] An error has occured during the loading of MadonnAdmin. Please check your Server Token in the config.lua
```

**Cause:** The Madonn'Admin platform could not be reached, or the Server Token is invalid.

**Fix:**

* Verify that `Server_Token` in `config/cfg_main.lua` matches exactly the token shown in your community settings on `madonnadmin.com`
* Make sure your FiveM server has outbound internet access to `madonnadmin.com`
* If the platform is temporarily unavailable, the resource will retry automatically every 5 seconds

***

## 🔴 Error 0xA02 — Community not found or subscription inactive

```
[ERROR - #0xA02] An error has occured during the loading of MadonnAdmin. Please check your Server Token in the config.lua
```

**Cause:** The Server Token is recognized but the associated community cannot be loaded. This usually means the subscription is inactive or the community has been deleted.

**Fix:**

* Check that your subscription is active on `madonnadmin.com`
* Verify that the server is correctly configured in your community dashboard with the right IP address
* If your IP has changed, update it in the Madonn'Admin dashboard

***

## 🔴 Error 0xC01 — Player blocked from connecting

```
[ERROR - #0xC01] Player X is not verified through Madonn'Admin and will not be connected
```

**Cause:** Madonn'Admin is offline or unreachable, and `Failure_Override` is set to `false` in `config/cfg_main.lua`, so players are blocked from joining.

**Fix:** Set `Failure_Override = true` to allow players to connect even when Madonn'Admin is temporarily unavailable:

```lua
Failure_Override = true,
```

> 💡 When `Failure_Override` is `true`, players will see a brief warning message but will still be able to connect. Bans and permission checks will be suspended until the connection is restored.

***

## 🔴 Error 0xC02 — No response from Madonn'Admin when loading permissions

```
[ERROR - #0xC02] No response received from Madonn'Admin
```

**Cause:** The platform did not respond when loading a player's permissions after they connected.

**Fix:** This is usually a temporary network issue. It resolves itself automatically on the next connection attempt. If it happens persistently, check that your server has stable outbound internet access.

***

## 🔴 The admin menu does not open

**Cause 1:** The player does not have a staff rank assigned in Madonn'Admin.

**Fix:** Go to **Team Staffs → Manage Staffs** in the dashboard, select the correct server, and assign a role to the player.



**Cause 2:** The player has a rank assigned but has not connected since the assignment.

**Fix:** Have the player disconnect and reconnect to the server so their permissions are reloaded.



**Cause 3:** The key binding is conflicting with another resource.

**Fix:** Check the FiveM key bindings in **Settings → Key Bindings → FiveM** and look for the **"Open Admin Menu"** entry. Reset it to the configured key (`F10` by default).

***

## 🔴 Staff member has no permissions after being added

**Cause:** The player was added to the community but has not yet been assigned a role, or the role has no permissions enabled.

**Fix:**

* Go to **Team Staffs → Manage Staffs**, select the server, and assign the correct role to the player
* In **Roles**, verify that the role has the necessary permission toggles enabled (teleportations, spectate, god mode, etc.)
* Have the player reconnect to reload their permissions

***

## 🔴 Screenshots are not working

**Cause 1:** `screenshot-basic` is not installed or not started before `MS_MadonnAdmin`.

**Fix:** Install `screenshot-basic` and make sure it is ensured before `MS_MadonnAdmin` in your `server.cfg`:

```cfg
ensure screenshot-basic
ensure MS_MadonnAdmin
```



**Cause 2:** The Discord webhook in `config/module/cfg_screenshots.lua` is invalid or missing.

**Fix:** Replace the webhook URL with a valid one from your Discord server:

```lua
SCREENSHOTS = {
    ScreenshotBasicName = "screenshot-basic",
    DiscordWebhookToSaveScreenshots = "https://discord.com/api/webhooks/...",
}
```

***

## 🔴 Logs are not appearing in Discord

**Cause:** The Discord webhook URLs in `config/module/cfg_logs.lua` are set to `false` or are invalid.

**Fix:** Set valid webhook URLs for the log types you want to receive:

```lua
LOGS = {
    DiscordWebhook = {
        Connections = "https://discord.com/api/webhooks/...",
        Chat        = "https://discord.com/api/webhooks/...",
        Shots       = "https://discord.com/api/webhooks/...",
        -- etc.
    }
}
```

Set any entry to `false` to disable that log type's webhook.

***

## 🔴 Anti-cheat is not running _(Silver & Gold only)_

**Cause 1:** `ModuleAnticheat` is set to `false` in `config/cfg_main.lua`.

**Fix:** Set it to `true`:

```lua
ModuleAnticheat = true,
```



**Cause 2:** Your subscription tier is **Bronze**. The anti-cheat module requires **Silver or Gold**.

**Fix:** Upgrade your subscription at `madonnadmin.com`.

***

## 🔴 Sanction returns "Error 0xS14" or "Error 0xS18"

```
[ERROR - #0xS14] An error occured while applying sanction to X
```

**Cause:** The Madonn'Admin API returned an error when applying the sanction. This can happen if the targeted player's profile is not yet fully synchronized.

**Fix:**

* Make sure the target player has connected at least once and their profile exists on `madonnadmin.com`
* If the error persists, contact support with the full error message

***

## 🔴 Ban screen not showing to a banned player

**Cause:** The `Failure_Override` option allowed the player through before the ban check completed, or the player's identifiers changed.

**Fix:**

* Check that the player's ban is correctly registered on `madonnadmin.com` under their profile
* Verify that the player is connecting with the same identifiers (Steam, FiveM, etc.) that were used when the ban was applied

***

## 💬 Still having issues?

If you are still experiencing problems after following the steps above, feel free to reach out to us:

* 💬 **Discord:** [discord.gg/madonne](https://discord.gg/madonne)
* 🌐 **Website:** [madonnestudio.com](https://madonnestudio.com/)
* 📧 **Email:** [contact@madonnestudio.com](mailto:contact@madonnestudio.com)

