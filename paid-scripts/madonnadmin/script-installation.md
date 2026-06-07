# Script Installation

## 📋 Requirements

* A **FiveM server** running on artifact `2699` or above
* An active **Madonn'Admin subscription** with a configured community and server token (see [🚀 First Launch](first-launch.md))
* _(Optional)_ `screenshot-basic` — required for the automatic screenshot system (reports and anti-cheat)
* _(Optional)_ `MS_Madonne_Notify` or `okokNotify` for enhanced notifications

***

## ⬇️ Step 1 — Download the resource

Download the latest version of **MS\_MadonnAdmin** from the [CFX Portal](https://portal.cfx.re/), the official Cfx.re platform for downloading your purchased resources.

> 💡 You must be logged in with the account used to purchase or claim the resource.

***

## 📁 Step 2 — Add to your server

Copy the `MS_MadonnAdmin` folder into your server's **resources directory**.

```
your-server/
└── resources/
    └── MS_MadonnAdmin/
        ├── client/
        ├── config/
        ├── server/
        ├── shared/
        ├── ui/
        └── fxmanifest.lua
```

***

## 🔑 Step 3 — Set your Server Token

Open `config/cfg_main.lua` and paste your **Server Token** from the Madonn'Admin dashboard:

```lua
CONFIG = {
    Server_Token = "your-server-token-here",
    ...
}
```

> ⚠️ This token is what authenticates your server with the Madonn'Admin platform. Without a valid token, the resource will refuse to start.

***

## 📝 Step 4 — Add to server.cfg

Add the following lines to your `server.cfg`. Make sure `oxmysql` and optionally `screenshot-basic` are started **before** `MS_MadonnAdmin`:

```cfg
ensure screenshot-basic   # optional, required for screenshots
ensure MS_Madonne_Notify  # optional, for enhanced notifications
ensure MS_MadonnAdmin
```

***

## ⚙️ Step 5 — Configure the resource

The main configuration file is `config/cfg_main.lua`. The most important options to set up at first launch are:

```lua
CONFIG = {
    Server_Token = "your-server-token-here",

    -- Key to open the admin menu in-game (default: F10)
    OpenAdminMenu = 'F10',

    -- Timezone offset for logs (e.g. 1 = UTC+1)
    Timezone = "+1",

    -- Notification system: "default" | "chat" | "okokNotify" | "MadonneNotify" | "custom"
    NotificationSystem = "default",

    -- Enable/disable modules
    ModuleAnticheat = true,   -- Silver & Gold only
    ModuleLogs = true,
    ModuleScreenshots = true, -- Requires screenshot-basic

    -- Restart announcement system
    RestartAnnouncement = {
        Enabled = true,
        Hours = { "22:00", "04:00", "10:00", "16:00" },
        XMinutesBefore = { 30, 10, 5, 2, 1 }
    }
}
```

Each module has its own config file under `config/module/`:

| File                  | Description                                                        |
| --------------------- | ------------------------------------------------------------------ |
| `cfg_anticheat.lua`   | Anti-cheat detection rules, ban lengths, whitelists                |
| `cfg_blips.lua`       | Player blips, nametags, high density zones, active staff display   |
| `cfg_brigitteai.lua`  | Birgitte AI settings (Gold only)                                   |
| `cfg_button.lua`      | Custom quick action buttons in the player profile and report panel |
| `cfg_commands.lua`    | Enable/disable and rename all in-game commands                     |
| `cfg_logs.lua`        | Discord webhooks per log type, ignored weapons                     |
| `cfg_reports.lua`     | Quick report presets, screenshot on report, notification options   |
| `cfg_sanctions.lua`   | Splash message on sanction, show ban author                        |
| `cfg_screenshots.lua` | screenshot-basic resource name, Discord webhook for screenshots    |

***

## 🔔 Step 6 — Configure the report command

In `config/module/cfg_reports.lua`, configure the quick reports available to players:

```lua
REPORTS_CONFIG = {
    ReportsEnabled = true,
    CreateReportCommand = "report",

    -- Up to 10 quick report types
    QuickReports = {
        "Bug",
        "Question",
        "Freekill",
        "NoFear",
        "NoPain",
        "Insults",
        "Cheater",
        "Spectate me",
        "New player"
    },
    TakeScreenshotWhenReportIsCreated = true,
}
```

***

## 🪝 Step 7 — Set up custom actions _(optional)_

The `config/module/cfg_button.lua` file lets you add custom quick action buttons that appear on each player's profile in the admin panel and in the report panel. Each button runs a Lua function on the targeted player's client:

```lua
BUTTONS = {
    [1] = {
        Title = "Heal",
        HaveAccess = true,           -- true = all staff, or {1,2,3} = specific rank IDs
        EnableCommandForThisButton = true,
        CommandName = "heal",
        CommandSuggestionText = "Heal a player",
        AddInReportMenu = true,
        Actions = function()
            SetEntityHealth(PlayerPed, 200)
        end
    },
    -- Add as many as needed
}
```

***

## 🔄 Step 8 — Restart your server

Restart your server or run the following in the console:

```
refresh
start MS_MadonnAdmin
```

If the Server Token is valid and your community is correctly configured, you should see the following in the console:

```
[SUCCESS] Madonn'Admin was successfully initialized. Thank you for using MadonneStudio ressources !
[SUCCESS] Retrieving community settings from the Madonn'Admin database : COMPLETED !
```

Madonn'Admin is now live! ✅

Staff members can open the admin panel in-game by pressing **`F10`** (default) and activating their moderation mode.
