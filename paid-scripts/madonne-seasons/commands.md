# Commands

All command names can be customized in the `COMMANDS` table in `config.lua`.

***

## 🌤️ Weather Commands

### /changeweather `<weather>`

Forces the weather to a specific type in the player's current zone.

```
/changeweather RAIN
/changeweather EXTRASUNNY
/changeweather THUNDER
```

**Available weather types:**

| Type         | Available                                                                      |
| ------------ | ------------------------------------------------------------------------------ |
| `BLIZZARD`   | ✅                                                                              |
| `CLEAR`      | ✅                                                                              |
| `CLEARING`   | ✅                                                                              |
| `CLOUDS`     | ✅                                                                              |
| `EXTRASUNNY` | ✅                                                                              |
| `FOGGY`      | ✅                                                                              |
| `NEUTRAL`    | ✅                                                                              |
| `OVERCAST`   | ✅                                                                              |
| `RAIN`       | ✅                                                                              |
| `SMOG`       | ✅                                                                              |
| `THUNDER`    | ✅                                                                              |
| `SNOW`       | ❌ _(disabled by default — edit `WeatherUsableInCommands` in config to enable)_ |
| `SNOWLIGHT`  | ❌                                                                              |
| `XMAS`       | ❌                                                                              |

> 🔐 Requires the `ChangeWeather` permission.

***

### /nextweather

Forces an immediate transition to the next weather in the current prediction cycle, skipping the current `WEATHER_DELAY` timer.

> 🔐 Requires the `NextWeather` permission.

***

### /dynamicweather

Toggles automatic weather changes on or off. When disabled, weather remains static until manually changed.

> 🔐 Requires the `DynamicWeather` permission.

***

## ⏱️ Time Commands

### /freezetime

Toggles time progression. When frozen, the in-game clock stops advancing.

> 🔐 Requires the `FreezeTime` permission.

***

### /changetime `<HH:MM>`

Sets the in-game time to a specific hour and minute.

```
/changetime 08:30
/changetime 22:00
```

> 🔐 Requires the `ChangeTime` permission.

***

## 📋 Information Commands

### /season

Displays the current in-game season (Spring, Summer, Autumn, or Winter) as configured in `SEASONS_NAMES`.

> 🔓 Available to all players.

***

### /forcast

Requests a weather forecast for the player's current zone. The forecast covers the next 24 hours and is delivered as an **audio broadcast**.

* If `FORCAST_OPENAI` is enabled, a unique AI-generated voice bulletin is produced in the configured language.
* If disabled, a pre-recorded `.ogg` file is played based on the predicted weather type.

> 🔓 Available to all players. Requires `FORCAST_ENABLED = true` in config.

***

## 🔐 Permission Reference

| Command           | Permission key    |
| ----------------- | ----------------- |
| `/dynamicweather` | `DynamicWeather`  |
| `/changeweather`  | `ChangeWeather`   |
| `/nextweather`    | `NextWeather`     |
| `/freezetime`     | `FreezeTime`      |
| `/changetime`     | `ChangeTime`      |
| `/season`         | _(none — public)_ |
| `/forcast`        | _(none — public)_ |
