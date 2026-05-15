---
cover: ../../.gitbook/assets/Voyage Photo Général Linkedin Bannière (12).png
coverY: 8
---

# Configuration

All configuration is done in `config.lua`, which is not escrowed and can be freely edited.

***

## 🚗 Vehicle Exclusions

```lua
DisableSeatbeltsForThisVehicles = {
    "harley","blazer","bmx","cruiser","gator3"
    -- add any vehicle model name here
},
```

List of **specific vehicle models** for which the seatbelt system is completely disabled. Useful for bicycles, ATVs, forklifts, and similar vehicles where a seatbelt makes no sense.

***

```lua
DisableSeatbeltsForThisVehcilesClasses = {
    8, 13, 14, 15, 16, 21, 22
},
```

List of **vehicle class IDs** for which the seatbelt system is disabled. This is the recommended way to exclude entire categories (motorcycles, boats, helicopters, planes…).

> 📖 Full class list: [FiveM Natives — GetVehicleClass](https://docs.fivem.net/natives/?_0x29439776AAA00A62)

***

## ⌨️ Key Binding & Controls

| Option                         | Type      | Description                                                           |
| ------------------------------ | --------- | --------------------------------------------------------------------- |
| `SeatbeltKey`                  | `string`  | Default key to toggle the seatbelt. Default: `"K"`                    |
| `KeymapText`                   | `string`  | Label shown in the FiveM key binding settings                         |
| `EnableWhenDead`               | `boolean` | If `true`, the seatbelt system remains active when the player is dead |
| `Cooldown`                     | `number`  | Minimum delay in **milliseconds** between two seatbelt toggles        |
| `LeaveVehicleWhenSeatbeltIsOn` | `boolean` | If `false`, the player cannot exit the vehicle while buckled          |

***

## 🖼️ Visual Warning

| Option                            | Type      | Description                                                                                              |
| --------------------------------- | --------- | -------------------------------------------------------------------------------------------------------- |
| `ShowBlinker`                     | `boolean` | Show the seatbelt warning icon when the player is unbuckled                                              |
| `SetBlinkerPermanent`             | `boolean` | If `true`, the icon stays visible permanently until the seatbelt is fastened. If `false`, it blinks      |
| `ShowBlinkerWhenVehicleIsStopped` | `boolean` | Show the warning even when the vehicle is stationary                                                     |
| `BlinkerMinSpeed`                 | `number`  | Minimum speed (km/h) to show the warning. Only applies when `ShowBlinkerWhenVehicleIsStopped` is `false` |

***

## 🔊 Sound

| Option          | Type      | Description                                                   |
| --------------- | --------- | ------------------------------------------------------------- |
| `ActivateSound` | `boolean` | Play buckle/unbuckle sound effects when toggling the seatbelt |
| `LoopSound`     | `boolean` | Enable the looping alarm when driving unbuckled               |
| `Volume`        | `number`  | Volume of buckle/unbuckle sounds (`0.0` to `1.0`)             |

***

## 🔔 Notifications

| Option                | Type      | Description                                                     |
| --------------------- | --------- | --------------------------------------------------------------- |
| `EnableNotifications` | `boolean` | Show a notification when the seatbelt is fastened or unfastened |
| `NotificationsType`   | `string`  | Notification system to use. See values below.                   |

### **Notification type values:**

| Value       | Behavior                                                                                                              |
| ----------- | --------------------------------------------------------------------------------------------------------------------- |
| `"default"` | Uses the native GTA V notification system                                                                             |
| `"auto"`    | Detects automatically — checks for **MS\_Madonne\_Notify** first, then **okokNotify**, then falls back to `"default"` |
| `"custom"`  | Uses your custom handler defined in `custom/notifs.lua`                                                               |

### **Notification strings:**

```lua
Strings = {
    notification_title = "Seatbelt System",
    seatbelt_on  = 'Seatbelt : ~g~set',
    seatbelt_off = 'Seatbelt : ~r~removed',
},
```

You can edit these strings to change the notification text and title.

***

## 💥 Ejection Physics

| Option                        | Type      | Description                                                                                 |
| ----------------------------- | --------- | ------------------------------------------------------------------------------------------- |
| `DiffTrigger`                 | `number`  | Speed difference threshold that triggers ejection. Lower = more sensitive. Default: `0.325` |
| `MinSpeed`                    | `number`  | Minimum vehicle speed (m/s) at which ejection can occur. Default: `13.9` (\~50 km/h)        |
| `VelocityMultiplicator`       | `number`  | Multiplier applied to the player's ejection velocity. Higher = further ejection             |
| `DisableEjectionWhenBreaking` | `boolean` | If `true`, ejection is disabled while the player is actively pressing the brake             |

***

## 🚨 Alarm

| Option           | Type      | Description                                                   |
| ---------------- | --------- | ------------------------------------------------------------- |
| `AlarmEnabled`   | `boolean` | Enable the seatbelt alarm system                              |
| `AlarmOnlySpeed` | `boolean` | Only trigger the alarm when the vehicle is above `AlarmSpeed` |
| `AlarmDuration`  | `number`  | Interval in **milliseconds** between each alarm sound loop    |
| `AlarmSpeed`     | `number`  | Minimum speed (km/h) to trigger the alarm                     |
| `AlarmVolume`    | `number`  | Volume of the alarm sound (`0.0` to `1.0`)                    |

***

## 💺 Per-Seat Ejection Whitelist

The `DisallowEjectionFromSeats` table lets you prevent ejection for specific **seats in specific vehicles**. This is useful for police vehicles where passengers should never be ejected.

```lua
DisallowEjectionFromSeats = {
    DisableAlarmInThisSituations = true,
    ["police"] = {-1, 1, 2},
    ["policeb"] = {-1},
}
```

| Option                         | Type      | Description                                                                    |
| ------------------------------ | --------- | ------------------------------------------------------------------------------ |
| `DisableAlarmInThisSituations` | `boolean` | If `true`, the alarm and blinker are also hidden for whitelisted seats         |
| `["model"]`                    | `table`   | Vehicle model name mapped to a list of seat indexes where ejection is disabled |

> 📖 Seat index reference: [FiveM Natives — GetPedInVehicleSeat](https://docs.fivem.net/natives/?_0x22AC59A870E6A669)
>
> `-1` = driver seat, `0` = front passenger, `1` = rear left, `2` = rear right, etc.

***

## 🪝 Custom Hooks — custom/main.lua

Two empty functions are available in `custom/main.lua` for you to add your own logic when the seatbelt state changes:

```lua
function FastenedSeatbelt()
    -- Called when the player fastens the seatbelt
end

function UnfastenedSeatbelt()
    -- Called when the player unfastens the seatbelt
end
```

***

## 🔔 Custom Notifications — custom/notifs.lua

Used when `NotificationsType` is set to `"custom"`. Edit the two event handlers to implement your own notification logic:

```lua
RegisterNetEvent("MS_MS_Seatbelt_Fastened_Notification")
AddEventHandler("MS_MS_Seatbelt_Fastened_Notification", function()
    -- Your notification for seatbelt fastened
end)

RegisterNetEvent("MS_MS_Seatbelt_Unfastened_Notification")
AddEventHandler("MS_MS_Seatbelt_Unfastened_Notification", function()
    -- Your notification for seatbelt unfastened
end)
```
