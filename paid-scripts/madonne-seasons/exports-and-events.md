# Exports & Events

Madonne Seasons exposes client-side exports and NetEvents to allow other resources to integrate with its weather and time data.

***

## 📤 GetZonePredictions _(client-side)_

Returns the weather prediction list for a given GTA V zone code.

```lua
local predictions = exports['MS_Madonne_Seasons']:GetZonePredictions(zone)
```

| Parameter | Type     | Description                                               |
| --------- | -------- | --------------------------------------------------------- |
| `zone`    | `string` | A GTA V zone code (e.g. `"DOWNT"`, `"SANDY"`, `"PALETO"`) |

**Returns:** A table of upcoming weather types in order, indexed from `1` to N (where N = number of weather slots for the day).

### Example

```lua
local playerCoords = GetEntityCoords(PlayerPedId())
local zone = GetNameOfZone(playerCoords.x, playerCoords.y, playerCoords.z)
local predictions = exports['MS_Madonne_Seasons']:GetZonePredictions(zone)

for i, weather in ipairs(predictions) do
    print("Slot " .. i .. ": " .. weather)
end
```

***

## ☀️ GetSunTimes _(client-side)_

Returns the current sunrise and sunset hours, which vary dynamically with the season.

```lua
local sunTimes = exports['MS_Madonne_Seasons']:GetSunTimes()
-- Returns: { sunrise = 6.5, sunset = 20.3 }
```

**Returns:** A table with two keys:

| Key       | Type     | Description                       |
| --------- | -------- | --------------------------------- |
| `sunrise` | `number` | Sunrise hour (e.g. `6.5` = 6h30)  |
| `sunset`  | `number` | Sunset hour (e.g. `20.3` = 20h18) |

### Example

```lua
local sunTimes = exports['MS_Madonne_Seasons']:GetSunTimes()
print("Sunrise at " .. sunTimes.sunrise .. "h")
print("Sunset at " .. sunTimes.sunset .. "h")
```

***

## 📡 NetEvents

### MadonneSeasons:SyncWeathers _(client)_

Fired when weather data is synced to the client (on spawn and on each weather change).

```lua
RegisterNetEvent("MadonneSeasons:SyncWeathers")
AddEventHandler("MadonneSeasons:SyncWeathers", function(data)
    -- data = { ["Los Santos"] = "CLEAR", ["Grand Senora Desert"] = "EXTRASUNNY", ... }
end)
```

***

### MadonneSeasons:SyncPredictions _(client)_

Fired alongside `SyncWeathers`, providing the full prediction table and sun times.

```lua
RegisterNetEvent("MadonneSeasons:SyncPredictions")
AddEventHandler("MadonneSeasons:SyncPredictions", function(predictions, sunrise, sunset)
    -- predictions = { ["Los Santos"] = { "CLEAR", "CLOUDS", "RAIN" }, ... }
    -- sunrise = 6.5, sunset = 20.3
end)
```

***

### MadonneSeasons:SyncTime _(client)_

Fired when time data is synced to the client.

```lua
RegisterNetEvent("MadonneSeasons:SyncTime")
AddEventHandler("MadonneSeasons:SyncTime", function(offset, base, daySpeed, nightSpeed, freeze)
    -- offset     = time offset in minutes
    -- base       = base time counter
    -- daySpeed   = ticks per minute during daytime
    -- nightSpeed = ticks per minute during nighttime
    -- freeze     = boolean, whether time is frozen
end)
```

