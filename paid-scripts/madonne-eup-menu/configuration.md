# Configuration

## Default configuration file (config.lua)

### General settings

Set a delay before the script initializes, to ensure all data is received before allowing players to open the menu.

```lua
Delay_Before_Init = 1000, -- ms
```

Configure the available ways to open the outfit menu.

```lua
Enable_Command_To_Open = true,
Command_To_Open = "eup", -- Without '/'
Enable_Keybind_To_Open = true,
Keybind_To_Open = 'F7',
```

Select whether players must stand inside a defined zone to open the menu. Markers and NPC attendants can be added per area.

```lua
Player_Must_Be_In_Area_To_Open = true,
Set_A_Marker_In_Area = true,
Set_A_NPC_In_Area = false,
```

***

### Areas

Define each spawn area with its world coordinates, detection radius, marker appearance, optional NPC model, and department restrictions.

```lua
Areas = {
    [1] = {
        x = -802.311, y = 175.056, z = 72.8446, h = 0.0,
        radius = 5.0,
        marker_type = 21, -- https://docs.fivem.net/docs/game-references/markers/
        marker_color = {r = 255, g = 255, b = 255, a = 255},
        marker_rotation = true,
        NPC_Model = "s_m_y_cop_01",
        departments = {"LSPD"}, -- set to {} or false to show all departments
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

### Notifications

Accepted values: `"notification"` (default FiveM notification), `"chat"` (chat message), or `"other"` (fires the `MS_EUPMenu_Notification` client event for a custom handler).

```lua
Notifications_Type = "notification",
Notifications_Chat_Color = {255, 255, 255},
```

To use a custom notification script, edit `client/custom/notifications.lua`:

```lua
RegisterNetEvent("MS_EUPMenu_Notification")
AddEventHandler("MS_EUPMenu_Notification", function(text)
    -- Example with okokNotify:
    exports['okokNotify']:Alert("MadonneStudio", text, 5000, 'info', true)
end)
```

***

### Translations

All in-game messages are editable in the `TRANSLATIONS` table at the bottom of `config.lua`.

```lua
TRANSLATIONS = {
    OpenCommandDescription             = "Open EUP Menu",
    OpenKeySettings                    = "Open EUP Menu",
    OpenDashboard                      = "Press ~INPUT_SELECT_CHARACTER_TREVOR~ to access the EUP Menu",
    NotPossibleToOpenDashboardFromHere = "It's not possible to open the EUP menu from here.",
    NeedToBeAMPPed                     = "You need to be a MP ped to use the EUP menu.",
}
```

***

## File : categories.lua

Define each outfit category visible in the menu. The variable must be named `OUTFITS_CATEGORIES`.

```lua
OUTFITS_CATEGORIES = {
    {
        name = "LSPD",
        logo = "https://cdn.discordapp.com/attachments/.../logo.png",
        whitelist = false,
        permissionCode = "",
    },
}
```

| Parameter        | Description                                                                             |
| ---------------- | --------------------------------------------------------------------------------------- |
| `name`           | Category name shown in the interface — must match the `category` field in `outfits.lua` |
| `logo`           | URL of the category logo image                                                          |
| `whitelist`      | `true` to restrict access to players with the permission code                           |
| `permissionCode` | Required permission code. Can be a `string`                                             |

***

## File : outfits.lua

Add each outfit to the menu. The variable must be named `OUTFITS`.

Each outfit defines every ped component and prop using the format `"drawableId:textureId"` (both 1-indexed).

```lua
OUTFITS = {
    {
        category = "LSPD",
        name = "Classe A",
        image = "https://cdn.discordapp.com/.../photo.jpg",
        gender = "M", -- "M" or "F"
        whitelist = false,
        permissionCode = "",
        ----------------------------
        mask       = "1:1",
        upperskin  = "7:1",
        pants      = "36:1",
        parachute  = "33:2",
        shoes      = "62:1",
        accessories = "237:1",
        undercoat  = "225:1",
        armor      = "201:1",
        decal      = "1:1",
        top        = "201:9",
        hat        = "1:1",
        glasses    = "1:1",
        ear        = "1:1",
        watch      = "1:1",
    },
}
```

| Parameter        | Description                                                                |
| ---------------- | -------------------------------------------------------------------------- |
| `category`       | Must exactly match a `name` value in `categories.lua`                      |
| `name`           | Display name shown in the interface                                        |
| `image`          | URL of the outfit preview image                                            |
| `gender`         | `"M"` for MP male ped, `"F"` for MP female ped                             |
| `whitelist`      | `true` to restrict to a permission code                                    |
| `permissionCode` | Required permission code                                                   |
| `mask` … `watch` | Ped component or prop value in `"drawableId:textureId"` format (1-indexed) |

**Component reference:**

| Field         | Ped component slot          |
| ------------- | --------------------------- |
| `mask`        | Component 1                 |
| `upperskin`   | Component 3                 |
| `pants`       | Component 4                 |
| `parachute`   | Component 5 (bag/parachute) |
| `shoes`       | Component 6                 |
| `accessories` | Component 7                 |
| `undercoat`   | Component 8                 |
| `armor`       | Component 9                 |
| `decal`       | Component 10                |
| `top`         | Component 11                |
| `hat`         | Prop 0                      |
| `glasses`     | Prop 1                      |
| `ear`         | Prop 2                      |
| `watch`       | Prop 6                      |

> 💡 Set a component to `"1:1"` to apply drawable index 0 / texture 0 (the first available). For props, `"1:1"` will **clear** the prop slot entirely.

***

## File : permissions.lua

This server-side file handles permission assignment. By default it grants the `STAFF` permission to players with the `madonne.staffoutfit` ace permission.

```lua
RegisterNetEvent("MS_EM_CheckPermissions")
AddEventHandler("MS_EM_CheckPermissions", function()
    local src = source
    if IsPlayerAceAllowed(source, "madonne.staffoutfit") then
        TriggerClientEvent("MS_CS_AddPermissionCode", src, "STAFF")
    else
        -- Add your own permission logic here
        -- TriggerClientEvent("MS_CS_AddPermissionCode", src, "YOUR_CODE")
    end
end)
```

> 💡 You can call `TriggerClientEvent("MS_CS_AddPermissionCode", src, "...")` multiple times to assign several permission codes to a player at once.
