# Main Configuration File

<details>

<summary>Default configuration file</summary>

```lua
CONFIG = {
    -- Authentication Token : This value can be found in the community settings of Madonn'Admin
    Server_Token = "",
    Debug = true,
    Discord_Invite_Link = "https://discord.gg/",

    DateFormatSQL = "%d/%m/%Y %T",

    -- System Failure Override : If this option is set to true, all players will still be able to join even if MadonnAdmin is down.
    Failure_Override = true,
    CantConnectText = "The connection to the Madonn'Admin moderation system is currently impossible. Please try again later...",
    CantConnectToMadonnAdmin = "The connection to the Madonn'Admin moderation system is currently impossible. You will still be connected in a few seconds. Please wait...",
    CheckingProfile = "Your profile is being verified by our Madonn'Admin moderation system. Please wait...",

    -- Key to open the admin menu
    OpenAdminMenu = 'F10',
    StaffActiveNoticeSize = "20px", -- Size of the staff active notice

    MinPlayersForHighDensityArea = 5,

    NotificationSystem = "okok", -- Available options : default | okok | custom | chat
    NotificationChatColorMessage = {r = 255, g = 0, b = 0},
    NotifyAllPlayersForSanctions = true,

    StaffMessagePrefix = "MESSAGE STAFF",
    ShowAuthorName = true,
    StaffMessageColor = {r = 0, g = 27, b = 145},
    BroadcastMessageColor = {r = 0, g = 27, b = 145},

    -- Enable/Disable differents module of MadonnAdmin
    ModuleAnticheat = true,
    ModuleLogs = true,

    BanDurations = {
	Community = "c",
	Permanent = "p",
	Year = "y",
	Month = "mo",
	Week = "w",
	Day = "d",
	Hour = "h",
	Minute = "m",
    }
}
```

</details>

```lua
Server_Token = "",
```

Paste here your token, that you can find on Madonn'Admin Web, in the server settings.

```lua
Debug = true,
```

Enable our debug option only if you need some assistance about our script.

```lua
Discord_Invite_Link = "https://discord.gg/",
```

Set your Discord Intive Link here. It will appears when a banned player try to connect him on the server.

```lua
DateFormatSQL = "%d/%m/%Y %T",
```

This option allows you to change the way dates are recorded. Be careful, only change this option if you know what you are doing. It is best to get help from us, in a Discord ticket.

```lua
Failure_Override = true,
CantConnectText = "The connection to the Madonn'Admin moderation system is currently impossible. Please try again later...",
CantConnectToMadonnAdmin = "The connection to the Madonn'Admin moderation system is currently impossible. You will still be connected in a few seconds. Please wait...",
CheckingProfile = "Your profile is being verified by our Madonn'Admin moderation system. Please wait...",
```

These options allow you to change the messages that are displayed when a player logs in, while Madonn'Admin checks the player's data in our databases. If you set Failure\_Override to true, in the event that Madonn'Admin becomes inaccessible, this will not prevent the connection to the server.

```lua
OpenAdminMenu = 'F10',
StaffActiveNoticeSize = "20px",
```

Change the key used to open the moderation menu here. You can also decide the size of the text that indicates to staff that they are in moderation mode.

```lua
MinPlayersForHighDensityArea = 5,
```

Madonn'Admin has a high player concentration zone mode. If this is enabled, you can change the minimum number of players present in the same zone for this system to start if you wish. It is not recommended to set a value lower than 5.

```lua
NotificationSystem = "okok", -- Available options : default | okok | custom | chat
NotificationChatColorMessage = {r = 255, g = 0, b = 0},
NotifyAllPlayersForSanctions = true,
```

Some notifications may arrive in-game, especially when a sanction requested by a staff has been applied.

A system is already in place for okokNotify. The list can of course grow in the future. If you decide to use a custom system, you can modify the client/custom/cl\_functions.lua file according to your needs.

```lua
StaffMessagePrefix = "MESSAGE STAFF",
ShowAuthorName = true,
StaffMessageColor = {r = 0, g = 27, b = 145},
BroadcastMessageColor = {r = 0, g = 27, b = 145},
```

Since admins have their own in-game chat, by default via the /admin command, you can change the display of these here.

The ShowAuthorName allows you to indicate whether or not you want the name of the staff sending a private message to the player to be displayed with the message.

```lua
ModuleAnticheat = true,
ModuleLogs = true,
```

Enable or disable some MadonnAdmin modules. Note that AntiCheat is only accessible from the Silver version, and is still being implemented.

```lua
BanDurations = {
    Community = "c",
    Permanent = "p",
    Year = "y",
    Month = "mo",
    Week = "w",
    Day = "d",
    Hour = "h",
    Minute = "m",
}
```

These different ban duration options will complement the ban commands made in-game. Example: 2d for two days.
