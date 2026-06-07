# Common Errors

## ❌ The resource does not start / is not found

**Error message:** `Couldn't start resource MS_Madonne_EUPMenu` or similar.

**Possible causes:**

* The resource folder is not named exactly `MS_Madonne_EUPMenu`
* The `ensure MS_Madonne_EUPMenu` line is missing from your `server.cfg`
* The resource was placed in a sub-folder not scanned by FiveM

**Fix:** Verify the folder name matches exactly, check your `server.cfg`, then restart your server.

***

## ❌ CFX Portal entitlement error — resource refuses to start

**Error message:** `Couldn't load resource MS_Madonne_EUPMenu` or `Escrow: invalid entitlement`.

This error means the FiveM account linked to your server's license key does not have access to this resource.

Please verify the following:

* The CFX key in your `server.cfg` contains no typo
* The key belongs to the FiveM account used to purchase the resource
* The resource has been successfully purchased on our store
* The key belongs to you and not to your hosting provider

> ⚠️ Hosts offering shared CFX keys in their packages prevent the use of any resource protected by FiveM's Escrow system, without exception.

***

## ❌ "You need to be a MP ped" notification appears

The menu refuses to open because the player is not using a freemode ped.

**Fix:** The resource only works with `mp_m_freemode_01` (MP male) and `mp_f_freemode_01` (MP female). Make sure your players spawn with one of these ped models. Custom ped models are not supported.

***

## ❌ Menu opens but no outfits are displayed

**Possible causes:**

* `outfits.lua` is empty or contains a syntax error
* The `category` field in an outfit entry does not match any `name` in `categories.lua`
* The `gender` field does not match the player's current ped model
* The `departments` restriction in the area config is set to a list that doesn't include the player's department

**Fix:** Check that category names match exactly between `outfits.lua` and `categories.lua`. Verify the `gender` field (`"M"` or `"F"`) matches the ped the player is using.

***

## ❌ Outfit is equipped incorrectly / wrong component applied

**Possible causes:**

* A component value uses the wrong format — the expected format is `"drawableId:textureId"` with both values **1-indexed** (so `"1:1"` = drawable 0, texture 0)
* A drawable or texture index doesn't exist in your EUP pack

**Fix:** Double-check all component values in `outfits.lua`. Remember that `"1:1"` corresponds to index 0 in-game. For props (`hat`, `glasses`, `ear`, `watch`), setting `"1:1"` clears the prop slot.

***

## ❌ Menu cannot be opened from the configured area

**Possible causes:**

* `Player_Must_Be_In_Area_To_Open = true` but the area coordinates or radius are not set correctly
* The `departments` table in the area config doesn't include the player's department name

**Fix:** Verify the `x`, `y`, `z` coordinates and `radius` in your `Areas` config. Make sure the department names in `departments` exactly match those in `categories.lua`.

***

## ❌ Notifications are not displayed

**Possible causes:**

* `Notifications_Type` is set to an unrecognized value — valid values are `"notification"`, `"chat"`, and `"other"`
* When using `"other"`, the event handler in `client/custom/notifications.lua` is not properly set up

**Fix:** Set `Notifications_Type = "notification"` to use native FiveM notifications, or configure your custom handler in `client/custom/notifications.lua`.

***

### 💬 Need further help?

Join our support server on Discord: [discord.gg/madonne](https://discord.gg/madonne)
