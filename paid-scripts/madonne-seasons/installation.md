---
cover: ../../.gitbook/assets/Voyage Photo Général Linkedin Bannière (16).png
coverY: 0
---

# Installation

## 📋 Requirements

* A **FiveM server** running on artifact `2699` or above
* _(Optional)_ `MS_Madonne_Notify` for enhanced notifications
* _(Optional)_ An **OpenAI API key** if using AI-powered forecast generation
* _(Optional)_ `lb-phone` if using the LB Phone weather app integration

***

## ⬇️ Step 1 — Download the resource

Download the latest version of **MS\_Madonne\_Seasons** from the [CFX Portal](https://portal.cfx.re/), the official Cfx.re platform for downloading your purchased resources.

> 💡 You must be logged in with the account used to purchase the resource.

***

## 📁 Step 2 — Add to your server

Copy the `MS_Madonne_Seasons` folder into your server's **resources directory**.

```
your-server/
└── resources/
    └── MS_Madonne_Seasons/
        ├── client/
        ├── server/
        │   └── custom/
        ├── ui/
        ├── config.lua
        └── fxmanifest.lua
```

***

## 📝 Step 3 — Add to server.cfg

Add the following line to your `server.cfg`:

```cfg
ensure MS_Madonne_Seasons
```

If you plan to use **AI-powered forecasts**, also add your OpenAI API key:

```cfg
set openai_key "sk-your-openai-api-key-here"
```

> ⚠️ Make sure `MS_Madonne_Seasons` is started **after** any notification resource it depends on (`MS_Madonne_Notify`, etc.).

***

## ⚙️ Step 4 — Configure the resource

Open `config.lua` and configure the resource to match your server setup.

Refer to the [⚙️ Configuration](configuration.md) page for a full breakdown of every option.

***

## 🔄 Step 5 — Restart your server

Restart your server or run the following command in the console:

```
restart MS_Madonne_Seasons
```

Madonne Seasons is now active! ✅

***

## 📱 Step 6 — LB Phone integration _(optional)_

If you use **lb-phone** and want the weather app to reflect Madonne Seasons data, refer to the [📱 Compatibility](compatibility.md) page for the two files to edit.
