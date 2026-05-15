# Exports & Events

Madonne Seatbelt exposes two **client-side exports** for integration with other resources, allowing you to read or control the seatbelt state programmatically.

***

## 📤 GetSeatbeltStatus

Returns the current seatbelt status of the local player.

```lua
local isBuckled = exports['MS_Madonne_Seatbelt']:GetSeatbeltStatus()
-- Returns: true (buckled) or false (unbuckled)
```

### Example use case

```lua
-- Prevent a player from exiting a vehicle if unbuckled
if not exports['MS_Madonne_Seatbelt']:GetSeatbeltStatus() then
    TriggerEvent('chat:addMessage', { args = { "You must fasten your seatbelt before exiting!" } })
end
```

***

## 📥 SetSeatbeltStatus

Forces the seatbelt state of the local player to a specific value.

```lua
exports['MS_Madonne_Seatbelt']:SetSeatbeltStatus(status)
```

| Parameter | Type      | Description                                       |
| --------- | --------- | ------------------------------------------------- |
| `status`  | `boolean` | `true` to force buckle, `false` to force unbuckle |

### Example use case

```lua
-- Force buckle the player when entering a specific vehicle
exports['MS_Madonne_Seatbelt']:SetSeatbeltStatus(true)

-- Force unbuckle on player death
exports['MS_Madonne_Seatbelt']:SetSeatbeltStatus(false)
```

> ⚠️ `SetSeatbeltStatus` only updates the internal state. It does not trigger the buckle/unbuckle sounds, notifications, or custom hooks. If you need those, trigger the seatbelt toggle manually through player input or use `FastenedSeatbelt()` / `UnfastenedSeatbelt()` in `custom/main.lua`.

***

## 🪝 Custom Hook Functions

Two functions in `custom/main.lua` are called automatically by the resource when the player toggles their seatbelt. You can add any logic inside them:

```lua
function FastenedSeatbelt()
    -- Called every time the player buckles up
    -- Example: sync state to server, trigger animations, update HUD...
end

function UnfastenedSeatbelt()
    -- Called every time the player unbuckles
end
```

***

## 📡 Custom Notification Events

When `NotificationsType` is set to `"custom"`, the following client-side events are triggered:

```lua
-- Triggered when the player fastens the seatbelt
RegisterNetEvent("MS_MS_Seatbelt_Fastened_Notification")

-- Triggered when the player unfastens the seatbelt
RegisterNetEvent("MS_MS_Seatbelt_Unfastened_Notification")
```

These are already set up in `custom/notifs.lua` for you to fill in.
