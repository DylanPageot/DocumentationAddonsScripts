# Script Configuration

All configuration files for Madonn'Admin are located in the `config/` folder. None of these files are escrowed — they can be freely edited to match your server's needs.

***

## 📁 File Structure

```
MS_MadonnAdmin/
└── config/
    ├── cfg_main.lua          ← Main configuration
    └── module/
        ├── cfg_anticheat.lua
        ├── cfg_blips.lua
        ├── cfg_brigitteai.lua
        ├── cfg_button.lua
        ├── cfg_commands.lua
        ├── cfg_logs.lua
        ├── cfg_reports.lua
        ├── cfg_sanctions.lua
        └── cfg_screenshots.lua
```

***

## 📄 Configuration Files

### ⚙️ [Main Configuration File](main-configuration-file.md)

The core of the resource. Contains the **Server Token**, notification system, active modules, staff chat settings, ban duration codes, timezone, and the restart announcement system.

**Start here** — most of the initial setup is done in this file.

***

### 🛡️ [Anticheat Configuration](anticheat-configuration.md)

Configures the built-in anti-cheat module _(Silver & Gold only)_. Each detection system is independent and can be individually enabled, tuned, and assigned its own ban duration.

Covers: Anti Props, Anti Explosions, Anti Vehicle Spam, Anti Trigger Event, Anti Noclip, Anti Invisible, Anti Freecam, Anti Sound, Anti Clear Tasks.

***

### 🗺️ [Blips Configuration](blips-configuration.md)

Controls everything related to player visibility on the map and nametags above players for active staff members. Includes player blip sprites, trust level color coding, active staff and submarine mode display, dead player blips, and high density zone detection.

***

### 🔧 [Buttons Configuration](buttons-configuration.md)

Defines the **custom quick action buttons** shown on player profiles and in the report panel. Each button runs a Lua function on the targeted player's client. Buttons can also register their own in-game commands.

***

### 💬 [Commands Configuration](commands-configuration.md)

Enable, disable, and rename every staff command: admin chat, note, commend, warn, kick, ban, goto, bring, return, and spectate. Also controls whether commands can be used on higher-ranked staff, and whether multi-ID syntax is supported.

***

### 📋 [Logs Configuration](logs-configuration.md)

Controls which activity types are tracked (connections, chat, shots, injuries, deaths, explosions) and where they are sent via **Discord webhooks**. Supports per-type webhook URLs, Discord thread routing, and custom log entries from external resources.

***

### 🚨 [Reports Configuration](reports-configuration.md)

Configures the in-game player report system: the command name, up to 10 quick report presets, automatic screenshot on submission, and notification triggers for players and staff.

***

### ⚖️ [Sanctions Configuration](sanctions-configuration.md)

Configures how sanctions are presented to players — full-screen splash messages for warns and commends, and whether the ban author's name is shown on the ban screen.

***

## 🪝 Custom Files

In addition to the standard config files, Madonn'Admin provides dedicated files for custom logic that won't be overwritten on updates:

| File                             | Description                                  |
| -------------------------------- | -------------------------------------------- |
| `client/custom/cl_functions.lua` | Custom notification handler (`CustomNotify`) |
| `client/custom/cl_logs.lua`      | Custom client-side log logic                 |
| `client/custom/cl_events.lua`    | Custom client-side event handlers            |
| `server/custom/sv_logs.lua`      | Custom server-side log logic                 |

***

## ⚠️ Important Notes

* **Never share your `Server_Token`** publicly. It is the unique key that links your server to your Madonn'Admin account.
* Changes to config files require a **resource restart** to take effect: `restart MS_MadonnAdmin`
* The anti-cheat module (`cfg_anticheat.lua`) will only run on **Silver and Gold** subscriptions regardless of the `ModuleAnticheat` setting on Bronze.
* The screenshot system (`cfg_screenshots.lua`) requires `screenshot-basic` to be installed and started before `MS_MadonnAdmin`.

