# Common Errors

## 🔴 Players are not being ejected from vehicles

**Cause 1:** The vehicle is in the `DisableSeatbeltsForThisVehicles` or `DisableSeatbeltsForThisVehcilesClasses` exclusion list.

**Fix:** Remove the vehicle model or class from the exclusion list in `config.lua`.



**Cause 2:** `DiffTrigger` is set too high, making the ejection threshold too insensitive.

**Fix:** Lower the `DiffTrigger` value (e.g. from `0.325` to `0.2`) to make ejection trigger more easily.



**Cause 3:** `MinSpeed` is set too high, so ejection never triggers at normal speeds.

**Fix:** Lower the `MinSpeed` value. The default is `13.9` (approximately 50 km/h). Set it lower if needed.



**Cause 4:** The player is in a whitelisted seat defined in `DisallowEjectionFromSeats`.

**Fix:** Check the `DisallowEjectionFromSeats` table in `config.lua` and adjust the vehicle/seat entries as needed.

***

## 🔴 The seatbelt warning icon is not showing

**Cause:** `ShowBlinker` is set to `false`.

**Fix:** Set `ShowBlinker` to `true` in `config.lua`.

***

## 🔴 The alarm is not playing

**Cause 1:** `AlarmEnabled` is set to `false`.

**Fix:** Set `AlarmEnabled` to `true`.



**Cause 2:** `AlarmOnlySpeed` is `true` and the vehicle speed is below `AlarmSpeed`.

**Fix:** Either lower `AlarmSpeed` or set `AlarmOnlySpeed` to `false` to always play the alarm when unbuckled.

***

## 🔴 Notifications are not showing

**Cause:** The configured `NotificationsType` resource is not running on your server.

**Fix:** Either:

* Set `NotificationsType` to `"auto"` to let the resource detect the best available system automatically
* Set it to `"default"` to use the native GTA V notification system
* If using `"custom"`, make sure your handlers are correctly defined in `custom/notifs.lua`

***

## 🔴 The resource loads but the seatbelt key does nothing

**Cause:** The key binding may have been remapped or is conflicting with another resource.

**Fix:** Check the FiveM key bindings in your game settings under `Settings > Key Bindings > FiveM` and look for the **"(Un)fasten seatbelt"** entry. Reset it to the default key if needed.

***

## 🔴 You lack the required entitlement to use MS\_Madonne\_Seatbelt

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
