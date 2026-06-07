# Installation

## 📋 Requirements

* A **FiveM server** running on artifact `2699` or above
* An **EUP** pack installed on your server (ped components and props must exist server-side)

***

## ⬇️ Step 1 — Download the resource

Download the latest version of **MS\_Madonne\_EUPMenu** from the [CFX Portal](https://portal.cfx.re/), the official Cfx.re platform for downloading your purchased resources.

> 💡 You must be logged in with the FiveM account used to purchase the resource.

***

## 📁 Step 2 — Add to your server

Copy the `MS_Madonne_EUPMenu` folder into your server's **resources directory**.

```
your-server/
└── resources/
    └── MS_Madonne_EUPMenu/
        ├── client/
        │   ├── core/
        │   └── custom/
        │       └── notifications.lua
        ├── server/
        │   ├── core/
        │   └── custom/
        │       └── permissions.lua
        ├── config/
        │   ├── config.lua
        │   ├── categories.lua
        │   └── outfits.lua
        ├── ui/
        └── fxmanifest.lua
```

> ⚠️ The folder name must remain exactly `MS_Madonne_EUPMenu`. Renaming it will break the resource.

***

## 📝 Step 3 — Add to server.cfg

Add the following line to your `server.cfg`:

<pre class="language-cfg"><code class="lang-cfg"><strong>ensure MS_Madonne_EUPMenu
</strong></code></pre>

***

## ⚙️ Step 4 — Configure the resource

Open the files inside the `config/` folder and configure them to match your server setup.

Refer to the [⚙️ Configuration](configuration.md) page for a full breakdown of every option.

***

## 🔄 Step 5 — Restart your server

Restart your server or run the following command in the console:

```
refresh
ensure MS_Madonne_EUPMenu
```

Madonne EUP Menu is now ready to use! ✅

Players can open the outfit menu by pressing **`F7`** (default), using the **`/eup`** command, or by walking into a configured spawn area.

> ⚠️ Players must be using an **MP freemode ped** (`mp_m_freemode_01` or `mp_f_freemode_01`) to access the menu. The resource will display a notification if the player's ped is not compatible.
