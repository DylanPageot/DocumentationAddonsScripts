# Main Configuration File

The main configuration file is located at `config/cfg_main.lua`. It controls the core behavior of Madonn'Admin, including the server token, notification system, active modules, and general settings.

***

## 🔑 Authentication

```lua
Server_Token = "",
```

| Option         | Type     | Description                                                                                    |
| -------------- | -------- | ---------------------------------------------------------------------------------------------- |
| `Server_Token` | `string` | Your unique server token, found in your community settings on `madonnadmin.com`. **Required.** |

***

## 🐛 Debug & Display

| Option                | Type      | Description                                                  |
| --------------------- | --------- | ------------------------------------------------------------ |
| `Debug`               | `boolean` | Enable or disable debug messages in the server console       |
| `Discord_Invite_Link` | `string`  | Your Discord invite link, shown to players in the ban screen |

***

## 🕐 Date & Time

| Option          | Type     | Description                                                                 |
| --------------- | -------- | --------------------------------------------------------------------------- |
| `DateFormatSQL` | `string` | Date format used for log timestamps. Default: `"%d/%m/%Y %T"`               |
| `Timezone`      | `string` | Timezone offset for logs (e.g. `"+1"` = UTC+1, `"0"` = UTC, `"-5"` = UTC-5) |

***

## 🔌 Connection Handling

| Option                     | Type      | Description                                                                                                           |
| -------------------------- | --------- | --------------------------------------------------------------------------------------------------------------------- |
| `Failure_Override`         | `boolean` | If `true`, players can still connect even when Madonn'Admin is temporarily unreachable. If `false`, they are blocked. |
| `AprilFoolBan`             | `boolean` | Enables the April Fool's fake ban joke on April 1st                                                                   |
| `CantConnectText`          | `string`  | Message shown to players when Madonn'Admin is down and `Failure_Override` is `false`                                  |
| `CantConnectToMadonnAdmin` | `string`  | Message shown briefly when the platform is unreachable but `Failure_Override` is `true`                               |
| `CheckingProfile`          | `string`  | Message shown in the loading screen while a player's profile is being verified                                        |

***

## 🎮 In-Game Interface

| Option                         | Type     | Description                                                                     |
| ------------------------------ | -------- | ------------------------------------------------------------------------------- |
| `OpenAdminMenu`                | `string` | Key binding to open the admin menu. Default: `"F10"`                            |
| `StaffActiveNoticeSize`        | `string` | Font size of the active staff notice displayed on screen. Default: `"20px"`     |
| `MinPlayersForHighDensityArea` | `number` | Minimum number of players in a zone for it to be flagged as a high density zone |

***

## 🔔 Notification System

| Option                         | Values                                                                       | Description                                                                           |
| ------------------------------ | ---------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `NotificationSystem`           | `"default"` \| `"chat"` \| `"okokNotify"` \| `"MadonneNotify"` \| `"custom"` | Controls how notifications are displayed to staff members                             |
| `NotificationChatColorMessage` | `{r, g, b}`                                                                  | Text color for chat-based notifications. Only used when `NotificationSystem = "chat"` |
| `NotifyAllPlayersForSanctions` | `boolean`                                                                    | If `true`, all players receive a server-wide chat message when a sanction is applied  |

> 💡 If using `"custom"`, implement your notification handler in `client/custom/cl_functions.lua` inside the `CustomNotify(text)` function.

***

## 💬 Staff Chat & Broadcasts

| Option                            | Type        | Description                                                                                          |
| --------------------------------- | ----------- | ---------------------------------------------------------------------------------------------------- |
| `StaffMessagePrefix`              | `string`    | Prefix shown in chat for staff messages. Default: `"STAFF CHAT"`                                     |
| `ShowStaffMessageAsSplashMessage` | `boolean`   | If `true`, private staff messages sent to a player appear as a full-screen GTA V splash message      |
| `ShowAuthorName`                  | `boolean`   | If `true`, the author's name is shown in the splash message when a staff sends a message to a player |
| `StaffMessageColor`               | `{r, g, b}` | Text color of staff chat messages                                                                    |
| `BroadcastMessageColor`           | `{r, g, b}` | Text color of broadcast messages                                                                     |

***

## 🧩 Modules

| Option              | Type      | Description                                                              |
| ------------------- | --------- | ------------------------------------------------------------------------ |
| `ModuleAnticheat`   | `boolean` | Enable the anti-cheat module. **Requires Silver or Gold subscription.**  |
| `ModuleLogs`        | `boolean` | Enable the activity log module (shots, deaths, chat, connections…)       |
| `ModuleScreenshots` | `boolean` | Enable the automatic screenshot system. **Requires `screenshot-basic`.** |

***

## ⏱️ Ban Durations

The `BanDurations` table defines the letter codes used when applying bans via command or the in-game panel:

```lua
BanDurations = {
    Community = "c",  -- Community-wide ban
    Permanent = "p",  -- Permanent ban
    Year      = "y",
    Month     = "mo",
    Week      = "w",
    Day       = "d",
    Hour      = "h",
    Minute    = "m",
}
```

**Examples of valid durations:**

* `"30m"` → 30 minutes
* `"2h"` → 2 hours
* `"7d"` → 7 days
* `"2w"` → 2 weeks
* `"1mo"` → 1 month
* `"p"` → permanent
* `"c"` → community ban

***

## 🔄 Restart Announcement

Automatically send countdown messages in chat before scheduled server restarts:

```lua
RestartAnnouncement = {
    Enabled = true,
    Hours = {
        "22:00",
        "04:00",
        "10:00",
        "16:00",
    },
    XMinutesBefore = { 30, 10, 5, 2, 1 }
}
```

| Option           | Type      | Description                                                    |
| ---------------- | --------- | -------------------------------------------------------------- |
| `Enabled`        | `boolean` | Enable or disable the restart announcement system              |
| `Hours`          | `table`   | List of scheduled restart times in `"HH:MM"` format            |
| `XMinutesBefore` | `table`   | List of how many minutes before each restart to send a warning |
