# Installation

## 📋 Requirements

* A **FiveM server** running on artifact `2699` or above
* _(Optional)_ `MS_Madonne_Notify` for enhanced notifications
* _(Optional)_ `es_extended` if using `Framework = "esx"`

***

## ⬇️ Step 1 — Download the resource

Download the latest version of **MS\_Madonne\_CarSpawner** from the [CFX Portal](https://portal.cfx.re/), the official Cfx.re platform for downloading your purchased resources.

> 💡 You must be logged in with the FiveM account used to purchase the resource.

***

## 📁 Step 2 — Add to your server

Copy the `MS_Madonne_CarSpawner` folder into your server's **resources directory**.

```
your-server/
└── resources/
    └── MS_Madonne_CarSpawner/
        ├── cfg/
        │   ├── config.lua
        │   ├── categories.lua
        │   ├── vehicles.lua
        │   └── parkings.lua
        ├── framework/
        │   └── esx.lua
        ├── ui/
        ├── client.lua
        ├── permissions.lua
        └── fxmanifest.lua
```

> ⚠️ The folder name must remain exactly `MS_Madonne_CarSpawner`. Renaming it will break the resource.

***

## 📝 Step 3 — Add to server.cfg

Add the following line to your `server.cfg`:

```cfg
ensure MS_Madonne_Notify   # optional, if using it for notifications
ensure MS_Madonne_CarSpawner
```

> ⚠️ If you use `MS_Madonne_Notify`, make sure it is started **before** `MS_Madonne_CarSpawner`.

***

## ⚙️ Step 4 — Configure the resource

Open the files inside the `cfg/` folder and configure them to match your server setup.

Refer to the [⚙️ Configuration](configuration.md) page for a full breakdown of every option.

***

## 🔄 Step 5 — Restart your server

Restart your server or run the following command in the console:

<pre><code><strong>refresh
</strong><strong>ensure MS_Madonne_CarSpawner
</strong></code></pre>

Madonne Car Spawner is now ready to use! ✅

Players can open the vehicle menu by pressing **`F7`** (default), using the **`/vehicle`** command, or by walking into a configured spawn area.
