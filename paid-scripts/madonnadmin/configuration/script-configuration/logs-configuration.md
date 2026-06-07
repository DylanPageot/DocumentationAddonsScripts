# Logs Configuration

The logs configuration is located at `config/module/cfg_logs.lua`. It controls which activity types are logged, where they are sent (Discord webhooks), and various display options.

***

## ✅ Enabled Log Types

```lua
LogsEnabled = {
    Disconnections = true,
    Chat           = true,
    Explosions     = true,
    Shots          = true,
    Injuries       = true,
    Death          = true,
    Other          = true,
}
```

Each entry can be independently enabled or disabled. Setting a type to `false` completely disables its logging — no data is stored and no webhook is sent.

| Type             | Description                                                               |
| ---------------- | ------------------------------------------------------------------------- |
| `Disconnections` | Player connections and disconnections                                     |
| `Chat`           | All chat messages sent on the server                                      |
| `Explosions`     | Explosions caused by players                                              |
| `Shots`          | Weapon shots fired by players, grouped per session                        |
| `Injuries`       | Damage dealt to players                                                   |
| `Death`          | Player deaths, including the cause and the killer if applicable           |
| `Other`          | Custom logs triggered via `TriggerEvent('MadonnAdmin:SimpleLog', 8, ...)` |

***

## 📨 Discord Webhooks

Each log type has its own Discord webhook. Set a valid webhook URL to enable Discord delivery for that type, or set it to `false` to disable it:

```lua
DiscordWebhook = {
    Disconnections = "https://discord.com/api/webhooks/...",
    Chat           = "https://discord.com/api/webhooks/...",
    Shots          = "https://discord.com/api/webhooks/...",
    Injuries       = "https://discord.com/api/webhooks/...",
    Death          = "https://discord.com/api/webhooks/...",
    Explosions     = "https://discord.com/api/webhooks/...",
    Connections    = "https://discord.com/api/webhooks/...",
    ChangeName     = "https://discord.com/api/webhooks/...",
}
```

> 💡 You can use **Discord forum threads** by appending `?thread_id=YOUR_THREAD_ID` to the webhook URL. This allows you to send each log type to a dedicated thread inside a single forum channel.

***

## 🔫 Ignored Weapons

Weapons in this list are excluded from the shots log entirely:

```lua
IgnoredWeapons = {
    [GetHashKey("WEAPON_FIREEXTINGUISHER")] = true,
    [GetHashKey("WEAPON_PETROLCAN")]        = true,
}
```

Add any weapon model hash you want to exclude from shot tracking. Useful for tools that are technically "weapons" but are not relevant for moderation.

***

## 🖥️ In-Game Log Display

```lua
MaxLogsShowedInGame = 100,
```

Maximum number of log entries displayed in the **Logs** tab of the in-game admin panel. Increasing this value may impact performance when opening the logs page with a large history.

***

## 🏷️ Discord Embed Options

```lua
AddDiscordIdToDiscordLogs = true,
```

If `true`, the Discord ID of each player involved in a log entry is included in the webhook embed. This allows Discord moderators to directly ping or identify players from the logs.

***

## 🔧 Custom Logs

You can push custom log entries to both the in-game panel and Discord from any resource using the `MadonnAdmin:SimpleLog` event:

```lua
-- From server-side:
TriggerEvent(
    'MadonnAdmin:SimpleLog',
    8,                    -- type 8 = custom / "Other"
    playerServerId,       -- playerA
    "Used forbidden item",-- detail
    nil,                  -- playerB (optional)
    "Custom Action",      -- action label
    0x662d91,             -- embed color
    true,                 -- take screenshot
    "https://discord.com/api/webhooks/your-webhook"
)
```

To add persistent custom log threads, edit `server/custom/sv_logs.lua`:

```lua
if LOGS.LogsEnabled.Other then
    CreateThread(function()
        -- Your custom server-side log logic here
    end)
end
```
