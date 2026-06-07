# Common Errors

## ❌ The resource does not start / is not found

**Error message:** `Couldn't start resource MS_Madonne_CarSpawner` or similar.

**Possible causes:**

* The resource folder is not named exactly `MS_Madonne_CarSpawner`
* The `ensure MS_Madonne_CarSpawner` line is missing from your `server.cfg`
* The resource was placed in a sub-folder not scanned by FiveM

**Fix:** Verify the folder name matches exactly, check your `server.cfg`, then restart your server.

***

## ❌ CFX Portal entitlement error — resource refuses to start

**Error message:** `Couldn't load resource MS_Madonne_CarSpawner` or `Escrow: invalid entitlement`.

This error means the FiveM account linked to your server's license key does not have access to this resource.

Please verify the following:

* The CFX key in your `server.cfg` contains no typo
* The key belongs to the FiveM account used to purchase the resource
* The resource has been successfully purchased on our store
* The key belongs to you and not to your hosting provider

> ⚠️ Hosts offering shared CFX keys in their packages prevent the use of any resource protected by FiveM's Escrow system, without exception.

***

## ❌ Menu opens but no vehicles are displayed

**Possible causes:**

* `vehicles.lua` is empty or contains a syntax error
* The `category` field in a vehicle entry does not match any `name` in `categories.lua`
* The player's department doesn't match the restrictions set in the area's `departments` table

**Fix:** Check that category names match exactly between `vehicles.lua` and `categories.lua`. Enable `DEBUG = true` in `config.lua` to print loaded permission codes in the console.

***

## ❌ Vehicle delivery is stuck "en route"

The NPC was spawned but the vehicle never arrives and the status stays blocked.

**Fix:** Use the debug command (default `/debug`) to manually reset the delivery. If this happens frequently, check that:

* `ParkingSlotDectionRange` is not set too high
* No other resource is deleting NPC-driven vehicles before they arrive
* The NPC ped model defined in `Mechano_Ped` is valid and loadable

***

## ❌ Vehicle spawns far from the player / NPC delivery triggered unexpectedly

**Possible causes:**

* No parking slot was found within `ParkingSlotDectionRange`, so the NPC delivery fallback was triggered (expected behavior when `Ship_Vehicle_If_Zero_Slot_Available = true`)

**Fix:** If you want vehicles to always spawn nearby, add custom parking slots near your most-used areas in `parkings.lua`, or increase `ParkingSlotDectionRange` slightly.

***

## ❌ Players can access vehicles they should not

**Possible causes:**

* `whitelist = false` is set on a vehicle or category that should be restricted
* `permissionCode` does not exactly match the code returned by your permission system
* The `departments` table in the area config is set to `{}` instead of a specific list, allowing all departments

**Fix:** Review the `whitelist` and `permissionCode` values in `vehicles.lua` and `categories.lua`. Check `permissions.lua` to confirm the codes being assigned to players match what you expect.

***

## ❌ Notifications are not displayed

**Possible causes:**

* `Notifications_Type` is set to an unrecognized value — valid values are `"notification"`, `"chat"`, and `"other"`
* The `MS_Madonne_Notify` resource is not started before `MS_Madonne_CarSpawner` in `server.cfg`

**Fix:** Set `Notifications_Type = "notification"` to use native FiveM notifications, or ensure `MS_Madonne_Notify` is ensured first in your `server.cfg`.

***

## ❌ ESX jobs are not recognized as permission codes

**Possible causes:**

* `Framework` is still set to `"standalone"` in `config.lua`
* The `permissionCode` in categories or vehicles doesn't exactly match the ESX job name

**Fix:** Set `Framework = "esx"` in `config.lua`, then set `permissionCode` to the ESX job name (e.g. `"police"`). The ESX integration is handled automatically via `framework/esx.lua`.

***

## 💬 Need further help?

Join our support server on Discord: [discord.gg/madonne](https://discord.gg/madonne)
