---
cover: ../../.gitbook/assets/Voyage Photo Général Linkedin Bannière (15).png
coverY: 0
---

# Configuration

The configuration file (named config.lua) allows you to modify all the different parameters taken into account within our script. In case of problems with the scripts, first check that you have correctly edited this document

<details>

<summary><em><strong>Content of the configuration file by default</strong></em></summary>

```lua
----------------------------------------------------------------------------------------------------
--                           Madonne Studio © 2023 - All rights reserved                          --
--                                                                                                --
--                                    "MADONNE SEASONS - v.1.0.0"                                 --
--                                                                                                --
--               For any issue with this ressource, please contact us on Discord :                --
--                                                                                                --
--                                  https://discord.gg/nmBAJrFhQB                                 --
--                                                                                                --
--                                    https://madonnestudio.com                                   --
--                                    contact@madonnestudio.com                                   --
--                                                                                                --
----------------------------------------------------------------------------------------------------

CONFIG_MADONNE_SEASONS = {

    -- Select type of permission system used
    PERMISSION_SYSTEM = "none",
    -- Can be : ace | steam | custom | none
    -- If custom is selected, you can edit the file permission.lua to 

    -- if "steam" is selected above, list allowed steam users here :
    ADMIN_USERS = {
        "steam:1100001000056ba",
    },

    -- Change names of differents seasons
    SEASONS_NAMES = {
        SPRING = "Spring",
        SUMMER = "Summer",
        AUTUMN = "Autumn",
        WINTER = "Winter",
    },

    -- Set the length IRL f a cycle of four seasons IG ( = 1 Year )
    YEAR_LENGTH = "2w", -- Examples of values accepted : '3d' for 3 Days, '1w' for 1 Week, '1mo' for 1 Month
    -- WARNING : Must be in days, weeks or months.

    -- Set the length IRL of an entire day IG
    DAY_LENGTH = "48m", -- Examples of values accepted : '20m' for 20 Minutes, '1h' for 1 Hour'
    -- WARNING : Must b1cae in minutes or hours
    -- DEFAULT = 48m

    -- Activate or desactivate automatic weather changes
    DYNAMIC_WEATHER = true,

    -- Enable / Disable ability to access to weather forcast
    FORCAST_ENABLED = true,
    FORCAST_LANGUAGE = "FR", -- Name of the folder to separate every languages
    -- WARNING : If you add a new language, you must edit fxmanifest.lua to add the ability to our script to reach your files. You can ask for support if you need it
    FORCAST_VOLUME = 0.5,
    

    -- Change the time between each possible weather change (in minutes)
    WEATHER_DELAY = 10,

    -- Change weather probability for each (total for each season should be 100)
    WEATHER_PROBABILITY = {
        { -- 1 : SPRING
            0, -- BLIZZARD
            10, -- CLEAR
            10, -- CLEARING
            10, -- CLOUDS
            15, -- EXTRASUNNY
            5, -- FOGGY
            10, -- NEUTRAL
            10, -- OVERCAST
            18, -- RAIN
            10, -- SMOG
            0, -- SNOW
            0, -- SNOWLIGHT
            2, -- THUNDER
            0, -- XMAS
        },
    
        { -- 2 : SUMMER
            0, -- BLIZZARD
            25, -- CLEAR
            10, -- CLEARING
            10, -- CLOUDS
            30, -- EXTRASUNNY
            0, -- FOGGY
            10, -- NEUTRAL
            5, -- OVERCAST
            8, -- RAIN
            0, -- SMOG
            0, -- SNOW
            0, -- SNOWLIGHT
            2, -- THUNDER
            0, -- XMAS
        },

        { -- 3 : AUTUMN
            0, -- BLIZZARD
            10, -- CLEAR
            10, -- CLEARING
            10, -- CLOUDS
            15, -- EXTRASUNNY
            3, -- FOGGY
            10, -- NEUTRAL
            10, --OVERCAST
            20, --RAIN
            2, -- SMOG
            0, -- SNOW
            0, -- SNOWLIGHT
            5, -- THUNDER
            0, -- XMAS
        },

        { -- 4 : WINTER
            5, -- BLIZZARD
            5, -- CLEAR
            5,-- CLEARING
            10,-- CLOUDS
            5, -- EXTRASUNNY
            5, -- FOGGY
            5, -- NEUTRAL
            15, --OVERCAST
            15, --RAIN
            5, -- SMOG
            10, -- SNOW
            10, -- SNOWLIGHT
            0, -- THUNDER
            5, -- XMAS
        },
    } 
}

-- Change differents commands names
COMMANDS = {
    DynamicWeather = "dynamicweather",
    FreezeTime = "freezetime",
    Forcast = "forcast",
    ChangeWeather = "changeweather",
    ChangeTime = "changetime",
    NextWeather = "nextweather",
    Season = "season",
}

HELPCMD = {
    DynamicWeather = "Enable or disable changes in weather.",
    FreezeTime = "Enable or disable the progression of time.",
    Forcast = "Get a weather report for tommorow.",
    ChangeWeather = "Modify the weather for a custom one (EXTRASUNNY, CLOUDS, RAIN, THUNDER, SNOW, ...)",
    ChangeTime = "Change the current time to a custom time (in HH:MM format).",
    NextWeather = "Go to the next weather.",
    Season = "Get the current season.",
}

-- Change any text to your own language
TEXT = {
    Enabled = "ENABLED !",
    Disabled = "DISABLED !",
    Freeze = "FROZEN !",
    Unfreeze = "UNFROZEN !",
    NoPermission = "You do not have permission to do that !",
    DynamicWeather = "Dynamic Weather is now ",
    FreezeTime = "The time is now ",
    WeatherChangedTo = "Weather is successfully changed to : ",
    TimeChangedTo = "Time is successfully changed to : ",
    WeatherChangedError = "Weather can't be changed. Please check args in your command.",
    TimeChangedError = "Time can't be changed. Please check args and respect this : HH:MM.",
    Season = "We are actually in ",
}
```

</details>

<details>

<summary><em><strong>Main Madonne Seasons configuration</strong></em></summary>

This option allows you to select the type of permission system you want to use between _ace_, _steam_, _custom_ and _none_.

```lua
PERMISSION_SYSTEM = "none",
```

When _ace_ is selected, you must configure your system permissions to add these :

* madonne.dynweather : Enable or disable the dynamic weather
* madonne.changeweather : Change the current weather
* madonne.nextweather : Skip the current weather for the next one
* madonne.changetime : Change the current time
* madonne.freezetime : Enable or disable the time progression&#x20;

To set your custom permission system, just edit the permission.lua file. We can help you to configure that on our Discord.



If "steam" is selected bellow, you can select which user can access to all the commands.

```lua
ADMIN_USERS = {
        "steam:1100001000056ba",
},
```



Change name of differents seasons.

```lua
SEASONS_NAMES = {
        SPRING = "Spring",
        SUMMER = "Summer",
        AUTUMN = "Autumn",
        WINTER = "Winter",
},
```



Change the duration of a year (a four seasons cycle) and of a day in game.

```lua
YEAR_LENGTH = "2w",
DAY_LENGTH = "48m",
```



Enable or disable the dynamic weather.

```lua
DYNAMIC_WEATHER = true,
```



This prefixs correspond to the name that will be entered at the start of the notifications, related to this script, which will be displayed in the game.

```lua
FORCAST_ENABLED = true,
FORCAST_LANGUAGE = "FR", -- Name of the folder to separate every languages
FORCAST_VOLUME = 0.5,
```



Change the delay before the weather will change.

```lua
WEATHER_DELAY = 10,
```



Change all probabilities for each weather and each season.

```lua
WEATHER_PROBABILITY = {
        { -- 1 : SPRING
            0, -- BLIZZARD
            10, -- CLEAR
            10, -- CLEARING
            10, -- CLOUDS
            15, -- EXTRASUNNY
            5, -- FOGGY
            10, -- NEUTRAL
            10, -- OVERCAST
            18, -- RAIN
            10, -- SMOG
            0, -- SNOW
            0, -- SNOWLIGHT
            2, -- THUNDER
            0, -- XMAS
        },
    
        { -- 2 : SUMMER
            0, -- BLIZZARD
            25, -- CLEAR
            10, -- CLEARING
            10, -- CLOUDS
            30, -- EXTRASUNNY
            0, -- FOGGY
            10, -- NEUTRAL
            5, -- OVERCAST
            8, -- RAIN
            0, -- SMOG
            0, -- SNOW
            0, -- SNOWLIGHT
            2, -- THUNDER
            0, -- XMAS
        },

        { -- 3 : AUTUMN
            0, -- BLIZZARD
            10, -- CLEAR
            10, -- CLEARING
            10, -- CLOUDS
            15, -- EXTRASUNNY
            3, -- FOGGY
            10, -- NEUTRAL
            10, --OVERCAST
            20, --RAIN
            2, -- SMOG
            0, -- SNOW
            0, -- SNOWLIGHT
            5, -- THUNDER
            0, -- XMAS
        },

        { -- 4 : WINTER
            5, -- BLIZZARD
            5, -- CLEAR
            5,-- CLEARING
            10,-- CLOUDS
            5, -- EXTRASUNNY
            5, -- FOGGY
            5, -- NEUTRAL
            15, --OVERCAST
            15, --RAIN
            5, -- SMOG
            10, -- SNOW
            10, -- SNOWLIGHT
            0, -- THUNDER
            5, -- XMAS
        },
    }
```



All further lines give you the opportunity to edit (or translate) sentences sent by the script and commands.&#x20;

````lua
```lua
COMMANDS = {
    DynamicWeather = "dynamicweather",
    FreezeTime = "freezetime",
    Forcast = "forcast",
    ChangeWeather = "changeweather",
    ChangeTime = "changetime",
    NextWeather = "nextweather",
    Season = "season",
}

HELPCMD = {
    DynamicWeather = "Enable or disable changes in weather.",
    FreezeTime = "Enable or disable the progression of time.",
    Forcast = "Get a weather report for tommorow.",
    ChangeWeather = "Modify the weather for a custom one (EXTRASUNNY, CLOUDS, RAIN, THUNDER, SNOW, ...)",
    ChangeTime = "Change the current time to a custom time (in HH:MM format).",
    NextWeather = "Go to the next weather.",
    Season = "Get the current season.",
}

-- Change any text to your own language
TEXT = {
    Enabled = "ENABLED !",
    Disabled = "DISABLED !",
    Freeze = "FROZEN !",
    Unfreeze = "UNFROZEN !",
    NoPermission = "You do not have permission to do that !",
    DynamicWeather = "Dynamic Weather is now ",
    FreezeTime = "The time is now ",
    WeatherChangedTo = "Weather is successfully changed to : ",
    TimeChangedTo = "Time is successfully changed to : ",
    WeatherChangedError = "Weather can't be changed. Please check args in your command.",
    TimeChangedError = "Time can't be changed. Please check args and respect this : HH:MM.",
    Season = "We are actually in ",
}
```
````

</details>
