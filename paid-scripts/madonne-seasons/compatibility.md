# Compatibility

## LB Phone — Weather App

Madonne Seasons is fully compatible with the **LB Phone** weather application. With the integration enabled, the phone's weather app will automatically reflect all data driven by Madonne Seasons in real time:

* 🌡️ **Temperature** — Coherent with the current weather type and season
* 🌦️ **Current weather** — Matches the weather currently active in the player's zone
* 📅 **Upcoming forecasts** — Displays the next weather predictions for the player's zone
* 🌧️ **Precipitation** — Updated based on the active weather
* 🌅 **Sunrise & sunset times** — Dynamically computed based on the current season and year progression

***

### 🛠️ How to Set Up the Integration

Two files need to be edited inside the **lb-phone** resource. Both are located in the apps folder of the LB Phone resource.

***

#### 📄 File 1 — `weather.lua`

**Location:** `lb-phone > client > apps > default > weather.lua`

This file handles the Lua-side logic that feeds weather data into the LB Phone app. Replace its content with the version provided below, which queries Madonne Seasons exports to retrieve the current weather, predictions, and sun times for the player's zone.

> ⚠️ The exact implementation may vary depending on your version of lb-phone. Refer to the existing file to understand how data is passed to the NUI layer, and adapt accordingly.

***

#### 📄 File 2 — `Weather-xxxx.js`

**Location:** `lb-phone > ui > dist > assets > Weather-xxxx.js`

> 💡 The `xxxx` part of the filename is a hash that changes with each LB Phone update. Look for the file starting with `Weather-` in the assets folder.

This file is the compiled JavaScript that handles the weather app's display logic. It needs to be updated to read the data provided by the modified `weather.lua`, including weather type mapping, temperature logic based on season, and precipitation values.

> ⚠️ **This file is minified.** Editing it requires care. We recommend using your browser's developer tools or a code formatter to make the content readable before editing.

The key parts to update are:

* The **weather type mapping** — so that GTA weather names (`EXTRASUNNY`, `RAIN`, etc.) correctly display the right icons and labels in the app UI
* The **temperature calculation** — to return values coherent with the current season and weather type (e.g. warmer in summer, colder in winter with snow)
* The **forecast rendering** — to display the `predictions` array from Madonne Seasons instead of the default LB Phone forecast data

***

### ⚠️ Important Notes

* These changes need to be **reapplied after each LB Phone update**, as the compiled JS file is regenerated.
* The `weather.lua` file may also be overwritten by updates to lb-phone. Keep a backup of your modified version.
* If you need help adapting the integration to your specific version of lb-phone, feel free to reach out on our Discord.

***

## 💬 Need Help?

* 💬 **Discord:** [discord.gg/madonne](https://discord.gg/madonne)
* 🌐 **Website:** [madonnestudio.com](https://madonnestudio.com/)
* 📧 **Email:** [contact@madonnestudio.com](mailto:contact@madonnestudio.com)

