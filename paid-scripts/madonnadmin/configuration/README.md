# Configuration

Before your staff members can open the admin panel in-game, Madonn'Admin requires a small amount of setup — both on the web platform and in the resource files. This section covers everything you need to configure to get your community running.

Configuration is split into two parts: the **Dashboard Configuration**, done entirely from the Madonn'Admin web platform, and the **Script Configuration**, done directly in the resource files on your FiveM server.

***

## 🖥️ Dashboard Configuration

The dashboard is where you define the structure of your community: your servers, your staff hierarchy, and how the platform behaves.

This is where you will:

* Set up your **community identity** — name, language, timezone, and trust score settings
* Add your **FiveM servers** and retrieve their unique tokens
* Create **staff roles** and configure their permissions
* Install the **Discord bot** to receive notifications directly in your Discord server

👉 [Dashboard Configuration](dashboard-configuration/)

***

## 📁 Script Configuration

The script configuration is done through the Lua files located in the `config/` folder of the resource. These files are not escrowed and can be freely edited.

This is where you will:

* Paste your **Server Token** and configure core behavior
* Enable or disable **modules** (anti-cheat, logs, screenshots)
* Define **staff commands**, **custom action buttons**, and **notification preferences**
* Configure the **anti-cheat** detection rules, sensitivity, and ban lengths
* Set up **Discord webhooks** for activity logs
* Customize the **report system** and its quick report presets

👉 [Script Configuration](script-configuration/)

***

> 💡 **Where to start?** If this is your first time setting up Madonn'Admin, begin with the [🚀 First Launch](../first-launch.md) guide, which walks you through the full setup process from account creation to your first server connection.
