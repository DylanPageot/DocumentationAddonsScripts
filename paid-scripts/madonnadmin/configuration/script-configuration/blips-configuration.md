# Blips Configuration

The blips configuration is located at `config/module/cfg_blips.lua`. It controls everything related to player visibility on the map and nametags above players — both for active staff members and for regular players.

***

## 👁️ General

| Option                           | Type      | Description                                                                             |
| -------------------------------- | --------- | --------------------------------------------------------------------------------------- |
| `ShowPlayerBlipsForActiveStaffs` | `boolean` | If `true`, active staff members see a map blip for every player visible to them         |
| `DistanceToShowBlipsAndNames`    | `number`  | Maximum distance (in units) at which blips and nametags are displayed. Default: `100.0` |

***

## 🚗 Blip Sprites per Vehicle Class

When a player is in a vehicle, their blip sprite changes based on the vehicle class. You can customize each sprite ID:

```lua
BlipSpritesForVehicleClasses = {
    ['0']  = 225, -- Compacts
    ['1']  = 225, -- Sedans
    ['8']  = 226, -- Motorcycles
    ['14'] = 427, -- Boats
    ['15'] = 43,  -- Helicopters
    ['16'] = 307, -- Planes
    -- ...
}
BlipSpritePlayerOnFoot = 1
```

> 📖 A full list of blip sprite IDs is available at [docs.fivem.net](https://docs.fivem.net/docs/game-references/blips/).

***

## 🔵 Submarine Mode (Undercover Staff)

The Submarine mode allows staff members to be hidden from other staff while appearing as regular players. When a staff member activates Submarine mode, their nametag displays differently.

```lua
SubMarine = {
    Abbreviation = "SB",           -- Prefix shown in the nametag for staff in same or lower rank
    Color = 150,                   -- Nametag color for same/lower rank staff
    ShowActuallyTalking = true,    -- Show voice indicator
    ShowHealth = true,             -- Show health bar in nametag

    AbbreviationHigherRanks = "SB",       -- Prefix shown to higher-ranked staff
    ColorHigherRanks = 150,               -- Nametag color shown to higher-ranked staff
    ShowActuallyTalkingHigherRanks = true,
    ShowHealthHigherRanks = false,
}
```

***

## 🟢 Active Staff Display

Controls how active (non-submarine) staff members are displayed to other staff and to regular players.

```lua
ActiveStaff = {
    Color = 176,                    -- Nametag color for active staff (seen by other staff)
    ShowActuallyTalking = true,
    ShowHealth = true,

    ShowNameForPlayers = true,              -- Show "ACTIVE STAFF - Name" nametag to regular players
    ShowActuallyTalkingForPlayers = true,
    ShowHealthForPlayers = false,
    ColorForPlayers = 1                     -- Nametag color shown to regular players
}
```

***

## 👤 Player Nametags

Controls how regular players are displayed to active staff members.

```lua
PlayerBlips = {
    ShowActuallyTalking = true,
    ShowActuallyDriving = true,   -- Show a driver prefix in the nametag when the player is driving
    DriverPrefix = "C",           -- Prefix shown when the player is the driver of a vehicle
    ShowHealth = true,

    TrustLevelInNames = {
        Enabled = true,
        Default   = 1,    -- Color for neutral players
        Trusted   = 18,   -- Color for trusted players (flag_trusted, flag_trusted_plus)
        Untrusted = 6,    -- Color for untrusted players (flag_untrusted, flag_caution, flag_cheater)
    },
}
```

> 💡 Players flagged as `flag_caution` or `flag_cheater` will also have `!!` prepended to their nametag to warn active staff at a glance.

***

## 💀 Dead Player Blips

When a player dies, a blip is automatically placed on the map for active staff members.

```lua
DeadPlayersBlips = {
    Enabled = true,
    BlipSprite = 310,
    BlipCategory = 10,
    DisplayOnMinimapOnlyAtShortRange = true,
    DelayBeforeRemovingBlip = 5,   -- Minutes before the blip is automatically removed
}
```

***

## 🏘️ High Density Zones

Automatically detects and highlights areas on the map where a high concentration of players is gathered, helping staff prioritize their attention.

```lua
HighDensityZones = {
    Enabled = true,
    Radius = 150.0,
    BlipSprite = 9,
    BlipAlpha = 100,
    BlipRotation = 50,
    DisplayOnMinimapOnlyAtShortRange = true,

    HighDensity = {
        Density = 30,   -- % of total online players in zone to trigger this level
        Color = 59,
    },
    MediumDensity = {
        Density = 20,
        Color = 47,
    },
    LowDensity = {
        Density = 10,
        Color = 60,
    }
}
```

| Option                | Type      | Description                                                   |
| --------------------- | --------- | ------------------------------------------------------------- |
| `Enabled`             | `boolean` | Enable or disable high density zone detection                 |
| `Radius`              | `number`  | Radius (in units) of each density zone blip                   |
| `BlipSprite`          | `number`  | Blip sprite ID used for density zones                         |
| `BlipAlpha`           | `number`  | Transparency of the blip (`0`–`255`)                          |
| `HighDensity.Density` | `number`  | Minimum % of online players in the zone to trigger this level |
| `HighDensity.Color`   | `number`  | Blip color for this density level                             |

> 💡 A zone is only shown if it also meets the `MinPlayersForHighDensityArea` threshold set in `cfg_main.lua`.
