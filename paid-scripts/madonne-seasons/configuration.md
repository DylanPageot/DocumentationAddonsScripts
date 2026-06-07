---
cover: ../../.gitbook/assets/Voyage Photo Général Linkedin Bannière (15).png
coverY: 0
---

# Configuration

All configuration is done in `config.lua`, which is not escrowed and can be freely edited.

***

## 🔐 Permission System

```lua
PERMISSION_SYSTEM = "none",
```

| Value           | Description                                                              |
| --------------- | ------------------------------------------------------------------------ |
| `"none"`        | All players can use admin commands. Recommended only for testing.        |
| `"ace"`         | Uses FiveM's ACE permission system with configurable permission nodes    |
| `"steam"`       | Restricts access to a list of Steam identifiers defined in `ADMIN_USERS` |
| `"madonnadmin"` | Uses MadonnAdmin staff rank detection                                    |
| `"custom"`      | Uses your own logic defined in `server/custom/sv_permission.lua`         |

**ACE permission nodes** (when `PERMISSION_SYSTEM = "ace"`):

```lua
ACE_PERMISSION = {
    ["DynamicWeather"] = "madonne.dynweather",
    ["ChangeWeather"]  = "madonne.changeweather",
    ["NextWeather"]    = "madonne.nextweather",
    ["FreezeTime"]     = "madonne.freezetime",
    ["ChangeTime"]     = "madonne.changetime",
},
```

Grant them in your `server.cfg`:

```cfg
add_ace group.admin madonne.dynweather allow
add_ace group.admin madonne.changeweather allow
add_ace group.admin madonne.nextweather allow
add_ace group.admin madonne.freezetime allow
add_ace group.admin madonne.changetime allow
```

**Steam whitelist** (when `PERMISSION_SYSTEM = "steam"`):

```lua
ADMIN_USERS = {
    ["steam:1100001000056ba"] = true,
},
```

***

## 🔔 Notification System

```lua
NOTIFICATION_SYSTEM = "default",
```

| Value       | Description                                                      |
| ----------- | ---------------------------------------------------------------- |
| `"default"` | Uses the native GTA V notification                               |
| `"chat"`    | Sends notifications as a chat message                            |
| `"madonne"` | Uses MS\_Madonne\_Notify                                         |
| `"custom"`  | Uses your custom handler in `server/custom/sv_notifications.lua` |

***

## 🗓️ Seasons

```lua
SEASONS_NAMES = {
    SPRING = "Spring",
    SUMMER = "Summer",
    AUTUMN = "Autumn",
    WINTER = "Winter",
},
```

Customize the display names of each season. These names are used in the `/season` command response and in AI-generated forecasts.

***

## ⏱️ Time & Season Length

| Option        | Example values          | Description                                                                                        |
| ------------- | ----------------------- | -------------------------------------------------------------------------------------------------- |
| `YEAR_LENGTH` | `"2w"`, `"1mo"`, `"3d"` | Real-time duration of a full four-season cycle. Accepts days (`d`), weeks (`w`), or months (`mo`). |
| `DAY_LENGTH`  | `"48m"`, `"1h"`         | Real-time duration of a full in-game day. Accepts minutes (`m`) or hours (`h`). Default: `"48m"`.  |

> 💡 A `YEAR_LENGTH` of `"2w"` means one full year (all four seasons) passes in 2 real-world weeks.

***

## 🌤️ Dynamic Weather

```lua
DYNAMIC_WEATHER = true,
WEATHER_DELAY = 10,
```

| Option            | Type      | Description                                                                                      |
| ----------------- | --------- | ------------------------------------------------------------------------------------------------ |
| `DYNAMIC_WEATHER` | `boolean` | Enable or disable automatic weather changes. Can also be toggled in-game with `/dynamicweather`. |
| `WEATHER_DELAY`   | `number`  | Time in **minutes** between each automatic weather change.                                       |

***

## 📻 Forecast System

| Option                   | Type      | Description                                                                                                          |
| ------------------------ | --------- | -------------------------------------------------------------------------------------------------------------------- |
| `FORCAST_ENABLED`        | `boolean` | Enable the `/forcast` command and forecast system                                                                    |
| `FORCAST_OPENAI`         | `boolean` | Use OpenAI to generate a unique AI-voiced weather bulletin. Requires `openai_key` in `server.cfg`.                   |
| `FORCAST_OPENAI_ALL_MAP` | `boolean` | If `true`, the AI bulletin also covers all other zones of the map, not just the player's zone                        |
| `FORCAST_OPENAI_VOICE`   | `string`  | OpenAI TTS voice to use. Available: `alloy`, `fable`, `onyx`, `nova`. Preview at [openai.fm](https://www.openai.fm/) |
| `FORCAST_LANGUAGE`       | `string`  | Language folder to use for pre-recorded forecasts (e.g. `"FR"`, `"EN"`). Only used when `FORCAST_OPENAI` is `false`. |
| `FORCAST_VOLUME`         | `number`  | Playback volume of the forecast audio (`0.0` to `1.0`)                                                               |

> ⚠️ AI forecast generation costs approximately **$0.001 per forecast** via the OpenAI API. This is not a MadonneStudio cost — it is billed directly to your OpenAI account.

**Pre-recorded forecasts** are available for the following weather types, in both `FR` and `EN`:

`BLIZZARD` · `CLEAR` · `CLEARING` · `CLOUDS` · `EXTRASUNNY` · `FOGGY` · `NEUTRAL` · `OVERCAST` · `RAIN` · `SMOG` · `SNOW` · `SNOWLIGHT` · `THUNDER`

> 💡 You can add new language folders by placing `.ogg` files in `ui/forcasts/YOUR_LANGUAGE/` and registering them in `fxmanifest.lua`.

***

## 🌍 Weather Zones

The map is divided into named zones, each with its own set of weather probabilities for each season. Each zone is identified by a list of GTA V **zone codes** (`ZoneCodes`).

```lua
WEATHER_ZONES = {
    ["Los Santos"] = {
        ZoneCodes = { ["DOWNT"] = true, ["HAWICK"] = true, ... },
        SpringWeather = { ["CLEAR"] = 20, ["RAIN"] = 10, ... },
        SummerWeather = { ["CLEAR"] = 30, ["EXTRASUNNY"] = 30, ... },
        AutumnWeather = { ... },
        WinterWeather = { ... },
    },
    ...
    ["Default"] = { ... }
}
```

**Included zones out of the box:**

| Zone                  | Description                                           |
| --------------------- | ----------------------------------------------------- |
| `Los Santos`          | The entire city of Los Santos and its surroundings    |
| `Costal Beaches`      | Coastal and beach areas south of Los Santos           |
| `Los Santos Hills`    | Hilly areas around Vinewood and Tongva Valley         |
| `Grand Senora Desert` | The desert region around Sandy Shores                 |
| `Northern Moutains`   | Mount Gordo, Mount Chiliad, and surrounding highlands |
| `Zancudo`             | Fort Zancudo area and Lago Zancudo                    |
| `Paleto Bay`          | The northern coastal town and surrounding forests     |
| `Default`             | Fallback zone for any area not matched by the above   |

**Weather probabilities** are defined as weights — the higher the number, the more likely that weather type is to appear. They do not need to sum to 100.

***

## ☁️ Cloud Opacity

```lua
CLOUD_OPACITY = {
    ["CLEAR"]      = 0.0,
    ["RAIN"]       = 1.0,
    ["EXTRASUNNY"] = 0.5,
    ...
}
```

Controls the cloud layer opacity for each weather type. Values range from `0.0` (no clouds) to `1.0` (full cloud cover). These are applied automatically when weather changes.

***

## 💬 Commands & Text

All command names and notification texts can be customized in `config.lua`:

```lua
COMMANDS = {
    DynamicWeather = "dynamicweather",
    FreezeTime     = "freezetime",
    Forcast        = "forcast",
    ChangeWeather  = "changeweather",
    ChangeTime     = "changetime",
    NextWeather    = "nextweather",
    Season         = "season",
    ...
}

TEXT = {
    Enabled              = "ENABLED !",
    Disabled             = "DISABLED !",
    NoPermission         = "You do not have permission to do that !",
    WeatherChangedTo     = "Weather is successfully changed to : ",
    TimeChangedTo        = "Time is successfully changed to : ",
    Season               = "We are actually in ",
    WaitForForcast       = "You will receive your weather forcast in few seconds. Please wait...",
    ...
}
```

***

## 🔧 Custom Handlers

**Custom permissions** — `server/custom/sv_permission.lua`:

```lua
function IsAllowedToAccessStaffCommandFromCustomMethod(source)
    -- Return true to grant access, false to deny
end
```

**Custom notifications** — `server/custom/sv_notifications.lua`:

```lua
function CustomNotify(type, message, source)
    -- type can be: "error", "info", "success"
end
```
