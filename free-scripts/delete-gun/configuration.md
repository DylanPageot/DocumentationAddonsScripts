# Configuration

All configuration files are located in the `config/` and `customs/` folders. These files are **not escrowed** and can be freely edited.

***

## config/main.lua

This is the main configuration file for the resource.

```lua
CONFIG_DELETE_GUN = {
    FRAMEWORK = "none",
    INVENTORY = "ox",
    MADONNADMIN = "auto",
    INIT_DELAY = 1,
    PERMISSION_SYSTEM = "ace",
    ENABLE_MULTI_MODE = false,
    WEAPON_TO_USE = "WEAPON_RAYCARBINE",
    AUTOMATICALLY_GIVE_WEAPON = true,
    NOTIFICATION_TEXT = "Entity deleted !",
    NOTIFICATION_TITLE = "Delete Gun",
    NOTIFICATION_TYPE = "default",
    notifChatColor = {255, 255, 255},
}
```

***

### 🧩 Framework & Inventory

| Option      | Values              | Description                                                                                        |
| ----------- | ------------------- | -------------------------------------------------------------------------------------------------- |
| `FRAMEWORK` | `"esx"` \| `"none"` | Set to `"esx"` if your server uses ESX. Use `"none"` for standalone or other frameworks.           |
| `INVENTORY` | `"ox"` \| `"none"`  | Only relevant if `FRAMEWORK` is `"esx"`. Set to `"ox"` if using ox\_inventory, `"none"` otherwise. |

***

### 🔐 Permissions

| Option              | Values                            | Description                                                                                                                                                |
| ------------------- | --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `MADONNADMIN`       | `"auto"` \| `"true"` \| `"false"` | Controls whether MadonnAdmin is used for permissions. `"auto"` will automatically detect if MS\_MadonnAdmin is running on your server.                     |
| `PERMISSION_SYSTEM` | `"ace"` \| `"custom"`             | Defines the permission system to use. If MadonnAdmin is enabled, this value is ignored. Use `"custom"` to implement your own logic in `customs/perms.lua`. |

> 💡 When using ACE, the default permission node is `madonne.deletegun`. You can change this in `customs/perms.lua`.

***

### ⏱️ Initialization

| Option       | Values              | Description                                                                                                                                                           |
| ------------ | ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `INIT_DELAY` | Integer _(seconds)_ | Delay before the resource initializes and checks permissions on the client side. If MadonnAdmin is used, an additional 10-second delay is added on top of this value. |

***

### 🔫 Weapon

| Option                      | Values            | Description                                                                                                         |
| --------------------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------- |
| `WEAPON_TO_USE`             | Any weapon name   | The weapon model used as the Delete Gun. Default is `"WEAPON_RAYCARBINE"`. You can use any valid GTA V weapon name. |
| `AUTOMATICALLY_GIVE_WEAPON` | `true` \| `false` | If `true`, the weapon is automatically given to authorized players when they join.                                  |

***

### 🔔 Notifications

| Option               | Values                                           | Description                                                             |
| -------------------- | ------------------------------------------------ | ----------------------------------------------------------------------- |
| `NOTIFICATION_TEXT`  | String                                           | The message displayed to the player when an entity is deleted.          |
| `NOTIFICATION_TITLE` | String                                           | The title of the notification (used by supported notification systems). |
| `NOTIFICATION_TYPE`  | `"default"` \| `"chat"` \| `"auto"` \| `"other"` | Controls how notifications are displayed. See details below.            |
| `notifChatColor`     | `{R, G, B}`                                      | Text color when `NOTIFICATION_TYPE` is set to `"chat"`.                 |

#### **Notification types:**

| Value       | Behavior                                                                                                                                              |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| `"default"` | Uses the native GTA V notification system                                                                                                             |
| `"chat"`    | Sends the notification as a chat message                                                                                                              |
| `"auto"`    | Automatically detects a running notification resource — checks for **MS\_Madonne\_Notify** first, then **okokNotify**, then falls back to `"default"` |
| `"other"`   | Triggers the `MS_DeleteGun_Notification` event, allowing a fully custom notification in `customs/notifs.lua`                                          |

***

### 🧩 Multi-Mode

| Option              | Values            | Description                                                                                                            |
| ------------------- | ----------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `ENABLE_MULTI_MODE` | `true` \| `false` | Enables the multi-mode system, allowing the gun to have multiple behaviors. When enabled, refer to `config/modes.lua`. |

***

## config/modes.lua

This file is only used when `ENABLE_MULTI_MODE` is set to `true`.

```lua
DELETE_GUN_MODES = {
    ["CommandNameToChangeMode"] = "gunmode",
    ["CommandDescription"] = "Edit the mode of your tool gun",
    ["CommandNotify"] = "Gun mode changed to",

    ["1"] = {
        ModeName = "Delete Gun",
        AcePermissions = false,
        MadonnAdmin = {1,2,3,4,5},
        NotificationText = "Entity deleted !",

        ClientSide = function(entity)
            -- Your client-side code here
        end,

        ServerSide = function(entity)
            DeleteEntity(entity)
        end,
    }
}
```

| Option                    | Description                                                                  |
| ------------------------- | ---------------------------------------------------------------------------- |
| `CommandNameToChangeMode` | The command (without `/`) used to cycle through modes in-game                |
| `CommandDescription`      | Description shown in the chat suggestion                                     |
| `CommandNotify`           | Prefix of the notification displayed when the mode changes                   |
| `ModeName`                | Display name of the mode                                                     |
| `AcePermissions`          | ACE permission node required for this mode, or `false` to disable            |
| `MadonnAdmin`             | List of MadonnAdmin rank IDs allowed to use this mode, or `false` to disable |
| `NotificationText`        | Notification displayed when this mode is triggered                           |
| `ClientSide`              | Lua function executed **client-side** when the gun fires in this mode        |
| `ServerSide`              | Lua function executed **server-side** when the gun fires in this mode        |

> ➕ You can add as many modes as needed by duplicating the `["1"]` block and incrementing the key (`"2"`, `"3"`…).

***

## customs/notifs.lua

Used when `NOTIFICATION_TYPE` is set to `"other"`. Edit this file to define your own notification handler:

```lua
RegisterNetEvent("MS_DeleteGun_Notification")
AddEventHandler("MS_DeleteGun_Notification", function(msg)
    -- Your custom notification code here
    exports['okokNotify']:Alert("Delete Gun", msg, 5000, 'error', true)
end)
```

***

## customs/perms.lua

Used when `PERMISSION_SYSTEM` is set to `"custom"`. Edit the `GetPerms` function to implement your own permission logic:

```lua
function GetPerms(src)
    -- return true to grant access, false to deny
    return false
end
```
