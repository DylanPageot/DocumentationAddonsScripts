# Usage & API

Madonne Notify exposes a simple API usable from any resource via **exports** (client-side or server-side).

***

## 🖥️ Client-side Export

Trigger a notification directly from a client-side script:

```lua
exports['MS_Madonne_Notify']:Notify(type, title, message, duration, sound)
```

### Parameters

| Parameter  | Type      | Description                                                      |
| ---------- | --------- | ---------------------------------------------------------------- |
| `type`     | `string`  | Notification type (see types below)                              |
| `title`    | `string`  | Title displayed in bold. Pass `""` to hide.                      |
| `message`  | `string`  | Subtitle message. Pass `""` to hide.                             |
| `duration` | `number`  | Display duration in **milliseconds** (e.g. `5000` for 5 seconds) |
| `sound`    | `boolean` | `true` to play a UI sound when the notification appears          |

### Example

```lua
exports['MS_Madonne_Notify']:Notify("success", "Seatbelt", "Seatbelt fastened!", 4000, true)
exports['MS_Madonne_Notify']:Notify("error", "Alert", "You are not allowed to do this.", 5000, false)
exports['MS_Madonne_Notify']:Notify("info", "", "Server restart in 10 minutes.", 6000, true)
```

***

## 🌐 Server-side Export

Trigger a notification from a server-side script, targeting a specific player by their server ID:

```lua
exports['MS_Madonne_Notify']:Notify(target, type, title, message, duration, sound)
```

### Parameters

| Parameter  | Type      | Description                                         |
| ---------- | --------- | --------------------------------------------------- |
| `target`   | `number`  | Player server ID (`-1` to broadcast to all players) |
| `type`     | `string`  | Notification type (see types below)                 |
| `title`    | `string`  | Title displayed in bold. Pass `""` to hide.         |
| `message`  | `string`  | Subtitle message. Pass `""` to hide.                |
| `duration` | `number`  | Display duration in **milliseconds**                |
| `sound`    | `boolean` | `true` to play a UI sound                           |

### Example

```lua
-- Send to a specific player
exports['MS_Madonne_Notify']:Notify(source, "warning", "Warning", "Your behavior has been noted.", 5000, true)

-- Broadcast to all players
exports['MS_Madonne_Notify']:Notify(-1, "announce", "Server", "An event is starting!", 8000, true)
```

***

## 📡 NetEvent (Client-side)

Notifications can also be triggered via a NetEvent, useful for more dynamic or event-driven systems:

```lua
TriggerEvent('MST_Notify:Notify', type, title, message, duration, sound)
```

Or from the server:

```lua
TriggerClientEvent('MST_Notify:Notify', source, type, title, message, duration, sound)
```

***

## 🎨 Notification Types

Each type comes with a dedicated color and icon:

| Type          | Color    | Icon           | Use case                  |
| ------------- | -------- | -------------- | ------------------------- |
| `info`        | Purple   | ℹ️ Information | General information       |
| `announce`    | Purple   | 📢 Megaphone   | Server announcements      |
| `progress`    | Purple   | ⏳ Hourglass    | Ongoing actions           |
| `success`     | Green    | ✅ Check        | Successful actions        |
| `achievement` | Green    | 🏆 Trophy      | Unlocked achievements     |
| `error`       | Dark Red | ⚠️ Warning     | Errors or blocked actions |
| `warning`     | Orange   | 🔔 Alert       | Warnings                  |
| `msg`         | White    | 💬 Message     | Chat or messages          |
| `radio`       | White    | 📻 Broadcast   | Radio communications      |
| `system`      | White    | ⚙️ Settings    | System events             |
| `vehicle`     | White    | 🚗 Car         | Vehicle-related events    |

***

> 💡 **Tip:** You can omit the title or message by passing an empty string `""`. The notification will adapt its layout accordingly and only show the content you provide.
