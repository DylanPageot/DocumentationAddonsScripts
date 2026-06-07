---
cover: ../../.gitbook/assets/Voyage Photo Général Linkedin Bannière (11).png
coverY: 0
---

# Installation

## 📋 Requirements

* A **FiveM server** running on artifact `2699` or above
* _(Optional)_ `MS_Madonne_Notify` or `okokNotify` for enhanced notifications

***

## ⬇️ Step 1 — Download the resource

Download the latest version of **MS\_Madonne\_Seatbelt** from the [CFX Portal](https://portal.cfx.re/), the official Cfx.re platform for downloading your purchased resources.

> 💡 You must be logged in with the account used to purchase the resource.

***

## 📁 Step 2 — Add to your server

Copy the `MS_Madonne_Seatbelt` folder into your server's **resources directory**.

```
your-server/
└── resources/
    └── MS_Madonne_Seatbelt/
        ├── client/
        ├── custom/
        ├── ui/
        ├── config.lua
        ├── server.lua
        └── fxmanifest.lua
```

***

## 📝 Step 3 — Add to server.cfg

Add the following line to your `server.cfg`, **after** any optional notification resource:

```cfg
ensure MS_Madonne_Notify   # optional, if using it for notifications
ensure MS_Madonne_Seatbelt
```

> ⚠️ If you use `NotificationsType = "MS_Madonne_Notify"` or `"okokNotify"`, make sure those resources are started **before** MS\_Madonne\_Seatbelt.

***

## ⚙️ Step 4 — Configure the resource

Open `config.lua` and configure the resource to match your server setup.

Refer to the [⚙️ Configuration](configuration.md) page for a full breakdown of every option.

***

## 🔄 Step 5 — Restart your server

Restart your server or run the following command in the console:

```
ensure
start MS_Madonne_Seatbelt
```

Madonne Seatbelt is now ready to use! ✅

Players can fasten their seatbelt by pressing **`K`** (default) while inside a vehicle.
