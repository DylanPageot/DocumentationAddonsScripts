# Exports & Events

Madonn'Admin exposes client-side and server-side exports, as well as a server-side HTTP API and custom log events for integration with other resources.

***

## 🖥️ Client-side Exports

### GetStaffRank

Returns the staff rank ID of the local player.

```lua
local rank = exports['MS_MadonnAdmin']:GetStaffRank()
-- Returns: number
-- -1 = Super Admin
--  0 = Not a staff member
--  1+ = Staff rank (lower number = higher authority)
```

#### Example

```lua
local rank = exports['MS_MadonnAdmin']:GetStaffRank()
if rank ~= 0 and rank ~= nil then
    print("This player is a staff member (rank " .. rank .. ")")
end
```

> This export is used by other MadonneStudio resources (e.g. MS\_Delete\_Gun with `MADONNADMIN = "auto"`) to detect whether the local player has staff access.

***

### IsPlayerTrusted

Returns whether the local player is considered trusted by the Madonn'Admin trust system.

```lua
local trusted = exports['MS_MadonnAdmin']:IsPlayerTrusted()
-- Returns: boolean
```

A player is considered **untrusted** if they have any of the following flags active:

* `flag_last_chance`
* `flag_sanction_lover`
* `flag_untrusted_plus`
* `flag_untrusted`

#### Example

```lua
local trusted = exports['MS_MadonnAdmin']:IsPlayerTrusted()
if not trusted then
    -- Apply restrictions for untrusted players
end
```

***

## 🌐 Server-side Exports

### GetStaffLevelServerSide

Returns the staff rank ID of a given player by their server ID.

```lua
local rank = exports['MS_MadonnAdmin']:GetStaffLevelServerSide(source)
-- Returns: number (same scale as GetStaffRank)
-- Returns 0 if the player is not a staff member or not found
```

#### Example

```lua
AddEventHandler("playerConnecting", function(name, setReason, deferrals)
    local rank = exports['MS_MadonnAdmin']:GetStaffLevelServerSide(source)
    if rank ~= 0 then
        print(name .. " is connecting as a staff member (rank " .. rank .. ")")
    end
end)
```

***

### GetStaffStatus

Returns whether a given player is currently in **active moderation mode** (i.e. they have activated their staff mode in-game).

```lua
local active = exports['MS_MadonnAdmin']:GetStaffStatus(source)
-- Returns: boolean
```

#### Example

```lua
-- Check if a staff member is actively moderating before assigning them a task
local isActive = exports['MS_MadonnAdmin']:GetStaffStatus(source)
if isActive then
    print("Staff member is currently in active moderation mode")
end
```

***

## 📡 Custom Log Event

Madonn'Admin exposes a custom log event that allows any resource to push entries into the Madonn'Admin log system, including Discord webhook delivery and automatic screenshots.

```lua
TriggerEvent('MadonnAdmin:SimpleLog', type, playerA, detail, playerB, text, colorEmbed, screenshot, webhookAddress)
```

| Parameter        | Type              | Description                                                                                                     |
| ---------------- | ----------------- | --------------------------------------------------------------------------------------------------------------- |
| `type`           | `number`          | Log type. Use `8` for custom logs                                                                               |
| `playerA`        | `number`          | Server ID of the primary player                                                                                 |
| `detail`         | `string`          | Detail text of the log                                                                                          |
| `playerB`        | `number` \| `nil` | Server ID of a second player (e.g. the attacker), or `nil`                                                      |
| `text`           | `string` \| `nil` | Custom action label to display in the embed                                                                     |
| `colorEmbed`     | `number`          | Discord embed color in hex (e.g. `0xFF0000`)                                                                    |
| `screenshot`     | `boolean`         | If `true`, automatically captures a screenshot of `playerB` (or `playerA`) and attaches it to the Discord embed |
| `webhookAddress` | `string`          | Discord webhook URL to send the log to                                                                          |

#### Example

```lua
-- Log a custom event with a screenshot
TriggerEvent(
    'MadonnAdmin:SimpleLog',
    8,                          -- type 8 = custom log
    source,                     -- playerA
    "Used a forbidden item",    -- detail
    nil,                        -- no playerB
    "Custom Action",            -- action label
    0x662d91,                   -- embed color (purple)
    true,                       -- take screenshot
    "https://discord.com/api/webhooks/your-webhook-here"
)
```

***

## 🔔 Custom Notification Handler

When `NotificationSystem` is set to `"custom"` in `config/cfg_main.lua`, edit `client/custom/cl_functions.lua` to implement your own notification:

```lua
function CustomNotify(text)
    -- Your custom notification code here
    -- Example with okokNotify:
    exports['okokNotify']:Alert("MadonneStudio", text, 5000, 'info', true)
end
```

***

## 📋 Custom Log Handler

To add your own persistent log logic, edit the provided custom log files:

**Client-side** — `client/custom/cl_logs.lua`:

```lua
if LOGS.LogsEnabled.Other then
    CreateThread(function()
        -- Your custom client-side log code here
    end)
end
```

**Server-side** — `server/custom/sv_logs.lua`:

```lua
if LOGS.LogsEnabled.Other then
    CreateThread(function()
        -- Your custom server-side log code here
        -- Use TriggerEvent('MadonnAdmin:SimpleLog', 8, ...) to push to Discord
    end)
end
```
