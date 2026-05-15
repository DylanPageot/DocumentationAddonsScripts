---
cover: ../../.gitbook/assets/Voyage Photo Général Linkedin Bannière (17).png
coverY: 0
---

# Installation

## 📋 Requirements

* A **FiveM server** running on artifact `2699` or above
* No additional dependencies required

***

## ⬇️ Step 1 — Download the resource

Download the latest version of **MS\_Madonne\_Notify** from the [CFX Portal](https://portal.cfx.re/), the official Cfx.re platform for downloading your purchased or claimed resources.

> 💡 You must be logged in with the account used to claim the resource.

***

## 📁 Step 2 — Add to your server

Copy the `MS_Madonne_Notify` folder into your server's **resources directory**.

```
your-server/
└── resources/
    └── MS_Madonne_Notify/
        ├── ui/
        ├── client.lua
        ├── server.lua
        └── fxmanifest.lua
```

***

## 📝 Step 3 — Add to server.cfg

Add the following line to your `server.cfg`. This resource has no dependencies, so it can be started at any point:

```cfg
ensure MS_Madonne_Notify
```

> ⚠️ If other resources depend on MS\_Madonne\_Notify (e.g. MS\_Madonne\_Seatbelt with `NotificationsType = "MS_Madonne_Notify"`), make sure `MS_Madonne_Notify` is started **before** them.

***

## 🔄 Step 4 — Restart your server

Restart your server or run the following command in the console:

```
refresh
start MS_Madonne_Notify
```

Madonne Notify is now ready to use! ✅
