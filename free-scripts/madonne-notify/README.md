---
cover: ../../.gitbook/assets/Voyage Photo Général Linkedin Bannière (1) (1).png
coverY: 0
---

# 📢 Madonne Notify

_Madonne Notify_ is a lightweight notification system designed specifically for FiveM servers. Whether you're building a roleplay, freeroam, or custom game mode server, Madonne Notify provides a sleek and modern way to send real-time in-game notifications to your players.

**Key Features:**

* 🔔 Clean and modern UI notifications
* ⚙️ Easy-to-use client and server-side exports
* 🚀 Lightweight and optimized for performance
* 🧩 Compatible with any framework (ESX, QBCore, standalone)



## **How does the script work ?**

Madonne Notify uses a simple and efficient client-server architecture to send in-game notifications directly to players. You can trigger notifications from either the server or the client using the provided `Notify` function.

#### 📦 Server-Side Usage

To send a notification from the server to a specific player:

```lua
-- Parameters: targetPlayer, type, title, message, duration, sound
exports['madonne_notify']:Notify(targetPlayer, "success", "Mission Complete", "You earned $500!", 5000, true)
```

#### 💻 Client-Side Usage

To display a notification locally on the client:

```lua
-- Parameters: type, title, message, duration, sound
exports['madonne_notify']:Notify("error", "Access Denied", "You do not have permission to do this.", 4000, true)
```

**🎨 Notification Types & Styles**

Each notification type applies a distinct style based on its category:

| Type                                | Style Preview                |
| ----------------------------------- | ---------------------------- |
| `warning`                           | Orange border and background |
| `info`, `progress`, `announce`      | Blue border and background   |
| `success`, `achievement`            | Green border and background  |
| `msg`, `system`, `radio`, `vehicle` | Gray border, neutral style   |

#### 🔊 Optional Sound

By setting `sound = true`, a frontend UI sound (`COLLECTED` from `HUD_AWARDS`) plays when the notification appears, adding feedback for critical or rewarding messages.
