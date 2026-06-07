# Configuration

## General settings

Set delays before initialization and before the menu opens, to ensure all data is received in time.

```lua
Delay_Before_Init = 1000, -- ms
Delay_Before_Opening_Menu = 200, -- ms
```

Select the framework your server uses. Set to `"esx"` to enable job-based permissions — the ESX job name is then used as `permissionCode` in your categories and vehicles.

```lua
Framework = "standalone", -- "standalone" or "esx"
```

Configure the available ways to open the vehicle menu.

```lua
Enable_Command_To_Debug_Shipping = true,
Command_To_Debug_Shipping = "debug", -- Without '/'
Enable_Command_To_Open = true,
Command_To_Open = "vehicle", -- Without '/'
Enable_Keybind_To_Open = true,
Keybind_To_Open = 'F7',
```

> 💡 The debug command lets staff manually unstick a vehicle delivery blocked in the "en route" state.

Select whether players must stand inside a defined zone to open the menu. Markers and NPC attendants can be added per area.

```lua
Player_Must_Be_In_Area_To_Open = true,
Set_A_Marker_In_Area = true,
Set_A_NPC_In_Area = false,
```

Configure how the script behaves when no parking slot is found within detection range.

```lua
Ship_Vehicle_If_Zero_Slot_Available = true, -- if false, spawn is cancelled and a notification is sent
ParkingSlotDectionRange = 200,
```

> ⚠️ Avoid setting `ParkingSlotDectionRange` to very large values — it may cause performance issues on busy servers.

***

## Areas

Define each spawn area with its world coordinates, detection radius, marker appearance, optional NPC model, and department restrictions.

```lua
Areas = {
    [1] = {
        x = -802.311, y = 175.056, z = 72.8446, h = 0.0,
        radius = 5.0,
        marker_type = 36, -- https://docs.fivem.net/docs/game-references/markers/
        marker_color = {r = 255, g = 255, b = 255, a = 255},
        marker_rotation = true,
        NPC_Model = "s_m_y_cop_01",
        departments = {"LSPD","LSSD"}, -- set to {} or false to allow all departments
    },
},
```

| Parameter          | Description                                                                                          |
| ------------------ | ---------------------------------------------------------------------------------------------------- |
| `x`, `y`, `z`, `h` | World coordinates and heading of the area center                                                     |
| `radius`           | Detection radius in units to trigger menu access                                                     |
| `marker_type`      | Marker type ID — see [FiveM markers reference](https://docs.fivem.net/docs/game-references/markers/) |
| `marker_color`     | RGBA color of the marker                                                                             |
| `marker_rotation`  | Whether the marker rotates                                                                           |
| `NPC_Model`        | Ped model for the NPC attendant (`Set_A_NPC_In_Area` must be `true`)                                 |
| `departments`      | List of department names to restrict access; `{}` or `false` to allow all                            |

***

## Vehicle blips & ejection

Configure whether a minimap blip appears when a vehicle is delivered, and whether unauthorized drivers are ejected.

```lua
EjectDriverIfCantDrive = true,

Add_Blip_To_Vehicle = true,
Blip_Sprite = 56,
Blip_Colour = 57,
```

Blip sprite and colour IDs are available at [docs.fivem.net](https://docs.fivem.net/docs/game-references/blips/).

***

## NPC mechanic per vehicle type

When no nearby parking slot is found, an NPC drives the vehicle to the player. Configure the ped model used per vehicle type.

```lua
Mechano_Ped = {
    { vehicle_type = 1,         ped = "s_m_y_cop_01" },       -- Police
    { vehicle_type = 2,         ped = "s_m_y_fireman_01" },   -- Fire department
    { vehicle_type = 3,         ped = "s_m_m_paramedic_01" }, -- EMS
    { vehicle_type = 4,         ped = "s_m_y_armymech_01" },  -- Military
    { vehicle_type = "default", ped = "mp_m_waremech_01" },   -- Default / civilian
},
```

Vehicle type IDs are defined in `vehicles.lua`.

***

## Player vehicle limits

Limit how many vehicles a player can have spawned simultaneously. Permission tiers can raise the limit above the default.

```lua
Cars_Limit_By_Player = true,
Default_Cars_Limit = 3,
Permissions_Codes_For_Limits = {
    { name = "VIP OR",     limit = 6 },
    { name = "VIP ARGENT", limit = 5 },
    { name = "VIP BRONZE", limit = 4 },
},
```

> 💡 Permission codes must exactly match those assigned by your permission system.

***

## Notifications

Accepted values: `"notification"` (default FiveM notification), `"chat"` (chat message), or `"other"` (fires the `MS_CarSpawner_Notification` client event for a custom handler).

```lua
Notifications_Type = "notification",
Notifications_Chat_Color = {255, 255, 255},
```

***

## Badges

Badges display on locked vehicles in the interface. Each badge is associated with a permission code and shows a custom icon, color, and label. Icons use names from [Remix Icon](https://remixicon.com/).

```lua
Badges = {
    ["VIP OR"] = {
        label = "VIP OR",
        icon_badge = "verified-badge-fill", -- icon name from remixicon.com (without ri- prefix)
        color_badge = "#c7a635",
        display_if_locked = true,
    },
},
```

| Parameter             | Description                                                                                              |
| --------------------- | -------------------------------------------------------------------------------------------------------- |
| Key (e.g. `"VIP OR"`) | Must match the `permissionCode` set on the vehicle or category                                           |
| `label`               | Text displayed next to the icon                                                                          |
| `icon_badge`          | Remix Icon name, without the `ri-` prefix                                                                |
| `color_badge`         | Hex color of the badge                                                                                   |
| `display_if_locked`   | If `true`, the vehicle stays visible in the menu with a lock overlay when the player doesn't have access |

***

## Translations

All in-game messages are editable in the `TRANSLATIONS` table at the bottom of `config.lua`.

```lua
TRANSLATIONS = {
    Vehicle_Already_Coming             = "...",
    Shipping_In_Progress               = "...",
    Vehicle_On_Nearest_Slot            = "...",
    Vehicle_Arrived                    = "...",
    CantDrive                          = "...",
    OpenDashboard                      = "Press ~INPUT_SELECT_CHARACTER_TREVOR~ to access the Car Spawner",
    OpenKeySettings                    = "Open Car Spawner",
    NotPossibleToOpenDashboardFromHere = "...",
    OpenCommandDescription             = "...",
    DebugCommandDescription            = "...",
    NoParkingSlotAvailable             = "...",
    Shipping_Debugged                  = "...",
}
```

***

## File : categories.lua

Define each category visible in the spawn menu. The variable must be named `VEHICLES_CATEGORIES`.

```lua
VEHICLES_CATEGORIES = {
    {
        name = "LSPD",
        logo = "https://cdn.discordapp.com/attachments/.../logo.png",
        whitelist = false,
        permissionCode = "",
    },
}
```

| Parameter        | Description                                                                              |
| ---------------- | ---------------------------------------------------------------------------------------- |
| `name`           | Category name shown in the interface — must match the `category` field in `vehicles.lua` |
| `logo`           | URL of the category logo image                                                           |
| `whitelist`      | `true` to restrict access to players with the permission code                            |
| `permissionCode` | Required permission code. Can be a `string` or a table of strings                        |

> 💡 When using `Framework = "esx"`, set `permissionCode` to the ESX job name (e.g. `"police"`).

The default file includes 12 pre-configured categories: LSPD, LSPP, LSSD, BCSO, SAHP, SASP, FIB, USMS, NOOSE, SAMR, SAFR, USARMY.

***

## File : vehicles.lua

Add each vehicle to the menu. The variable must be named `VEHICLES`.

```lua
VEHICLES = {
    {
        type = 1,
        category = "LSPD",
        name = "2011 Ford CVPI - Rotatif",
        model = "mst11vic",
        spawnIn = false,
        livery = 0,
        photo = "https://cdn.discordapp.com/.../photo.jpg",
        whitelist = false,
        permissionCode = "",
        extraToEnable = {1, 4},
        extraToDisable = {2, 3, 5, 6, 7},
        primaryColor = 0,
        secondaryColor = 0,
    },
}
```

| Parameter        | Description                                                                                           |
| ---------------- | ----------------------------------------------------------------------------------------------------- |
| `type`           | Vehicle type: `0` civilian, `1` police, `2` fire department, `3` EMS, `4` military                    |
| `category`       | Must exactly match a `name` value in `categories.lua`                                                 |
| `name`           | Display name shown in the interface                                                                   |
| `model`          | In-game spawn name of the vehicle                                                                     |
| `spawnIn`        | `true` to teleport the player inside the vehicle on spawn                                             |
| `livery`         | Livery index (`0` = default)                                                                          |
| `photo`          | URL of the vehicle preview image                                                                      |
| `whitelist`      | `true` to restrict to a permission code                                                               |
| `permissionCode` | Required permission code. Can be a `string` or a table of strings                                     |
| `extraToEnable`  | List of extra IDs to enable on the vehicle                                                            |
| `extraToDisable` | List of extra IDs to disable on the vehicle                                                           |
| `primaryColor`   | Primary vehicle color ID — see [color reference](https://wiki.rage.mp/index.php?title=Vehicle_Colors) |
| `secondaryColor` | Secondary vehicle color ID                                                                            |

***

## File : parkings.lua

Contains all pre-listed parking slots used for vehicle delivery. The variable must be named `PARKING_SLOTS`.

```lua
PARKING_SLOTS = {
    -- vehicle_type, X, Y, Z, heading
    {0, 1110.62, -1506.04, 34.03, 268.66},
}
```

A `vehicle_type` of `0` makes the slot available for all types. Use a specific type ID to restrict a slot to one category.

> 💡 The default file includes **11,000+ parking slots** mapped across the entire GTA V map. Only edit this file if you want to add custom spots or restrict available locations.

***

## File : permissions.lua

This server-side file handles permission assignment. By default it grants the `STAFF` permission to players with the `madonne.vclstaff` ace permission.

```lua
RegisterNetEvent("MS_CS_CheckPermissions")
AddEventHandler("MS_CS_CheckPermissions", function()
    local src = source
    if IsPlayerAceAllowed(source, "madonne.vclstaff") then
        TriggerClientEvent("MS_CS_AddPermissionCode", src, "STAFF")
    else
        -- Add your own permission logic here
        -- TriggerClientEvent("MS_CS_AddPermissionCode", src, "YOUR_CODE")
    end
end)
```

> 💡 You can call `TriggerClientEvent("MS_CS_AddPermissionCode", src, "...")` multiple times to assign several permission codes to a player at once.
