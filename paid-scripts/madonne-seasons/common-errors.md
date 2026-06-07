# Common Errors

## 🔴 You lack the required entitlement to use MS\_Madonne\_Seasons

This message indicates that your server does not have the necessary entitlement to start the resource. This is related to FiveM's **Escrow** protection system.

Check the following points one by one:

* ✅ The **CFX Portal key** listed in your `server.cfg` does not contain any typing error
* ✅ The CFX Portal key belongs to the **FiveM account that was used to purchase or claim** the resource
* ✅ The resource has been **successfully claimed** on the [CFX Portal](https://portal.cfx.re/)
* ✅ The CFX Portal key linked to your server **belongs to you**, and not to your hosting provider

> ⚠️ Some hosting providers include a shared CFX Portal key as part of their offers. A key that does not belong to you will block the use of **any Escrow-protected resource**, without exception. Always use your own personal key.

***

## 🔴 Weather is the same for all players / not changing

**Cause 1:** `DYNAMIC_WEATHER` is set to `false` in `config.lua`.

**Fix:** Set it to `true`, or toggle it in-game with `/dynamicweather`.



**Cause 2:** `WEATHER_DELAY` is set to a very high value.

**Fix:** Lower `WEATHER_DELAY` (in minutes) to make weather change more frequently.



**Cause 3:** A player used `/dynamicweather` to disable automatic weather changes.

**Fix:** Use `/dynamicweather` again in-game to re-enable it, or restrict access to the command via the permission system.

***

## 🔴 All players are in the same zone / per-zone weather isn't working

**Cause:** Zone codes in `WEATHER_ZONES` don't match the actual GTA V zone codes for those areas.

**Fix:** Verify zone codes using the `GetNameOfZone` native. You can test it in-game by printing the zone name in a script and checking which code is returned at your current position.

***

## 🔴 The `/forcast` command plays no audio

**Cause 1:** `FORCAST_ENABLED` is set to `false`.

**Fix:** Set `FORCAST_ENABLED = true` in `config.lua`.



**Cause 2 (OpenAI):** The `openai_key` convar is missing or incorrect in `server.cfg`.

**Fix:** Add or correct the following line in your `server.cfg`:

```cfg
set openai_key "sk-your-openai-key-here"
```



**Cause 3 (OpenAI):** Your OpenAI account has no credits.

**Fix:** Add credits to your OpenAI account at [platform.openai.com](https://platform.openai.com/).



**Cause 4 (pre-recorded):** The `.ogg` file for the predicted weather type is missing in the selected language folder.

**Fix:** Make sure all weather `.ogg` files exist under `ui/forcasts/YOUR_LANGUAGE/`. The required files are named after each weather type: `CLEAR.ogg`, `RAIN.ogg`, `THUNDER.ogg`, etc.

***

## 🔴 Time is not synced between players

**Cause:** The `playerSpawned` event is not firing, preventing the sync request from being sent.

**Fix:** Make sure no other resource is blocking or replacing the `playerSpawned` event. You can also try increasing the timeout in `cl_time.lua` if your server takes longer to spawn players.

***

## 🔴 Admin commands return "You do not have permission"

**Cause:** The permission system is not configured correctly for your setup.

**Fix:** Check your `PERMISSION_SYSTEM` setting and verify accordingly:

* **ACE:** Confirm `add_ace` entries are in `server.cfg` and the player is in the correct group
* **Steam:** Confirm the player's Steam hex ID is listed in `ADMIN_USERS`
* **MadonnAdmin:** Confirm `MS_MadonnAdmin` is running and the player has a staff rank
* **Custom:** Verify your `IsAllowedToAccessStaffCommandFromCustomMethod` function returns `true` for the player

***

## 🔴 Server console shows ERROR 0x01A or 0x01B

These are configuration parsing errors:

| Code    | Cause                           | Fix                                                          |
| ------- | ------------------------------- | ------------------------------------------------------------ |
| `0x01A` | `YEAR_LENGTH` format is invalid | Use `"Nd"`, `"Nw"`, or `"Nmo"` format (e.g. `"2w"`, `"1mo"`) |
| `0x01B` | `DAY_LENGTH` format is invalid  | Use `"Nm"` or `"Nh"` format (e.g. `"48m"`, `"1h"`)           |

***

## 💬 Still having issues?

* 💬 **Discord:** [discord.gg/madonne](https://discord.gg/madonne)
* 🌐 **Website:** [madonnestudio.com](https://madonnestudio.com/)
* 📧 **Email:** [contact@madonnestudio.com](mailto:contact@madonnestudio.com)
