# Configuration

<details>

<summary><em><strong>Content of the configuration file by default</strong></em></summary>

```lua
CONFIG = {
    Delay_Before_Init = 1000, -- ms
    
    Enable_Command_To_Open = true,
    Command_To_Open = "eup", -- Without '/'

    Enable_Keybind_To_Open = true,
    Keybind_To_Open = 'F7', -- Default : F7

    Player_Must_Be_In_Area_To_Open = true,
    Set_A_Marker_In_Area = true,
    Set_A_NPC_In_Area = false,

    Areas = {
	[1] = {
		x = -802.311, y = 175.056, z = 72.8446, h = 0.0,
		radius = 5.0,
		marker_type = 21, -- https://docs.fivem.net/docs/game-references/markers/
		marker_color = {r = 255, g = 255, b = 255, a = 255},
		marker_rotation = true, -- true or false
		NPC_Model = "s_m_y_cop_01",
		departments = {"LSPD"}, -- Change {} to false to show all departments
	},
	[2] = {
		x = -802.311, y = 170.056, z = 72.8446, h = 0.0,
		radius = 5.0,
		marker_type = 21, -- https://docs.fivem.net/docs/game-references/markers/
		marker_color = {r = 255, g = 255, b = 255, a = 255},
		marker_rotation = false, -- true or false
		NPC_Model = "s_m_y_cop_01",
		departments = false, -- Change {} to false to show all departments
	},
    },
    
    Notifications_Type = "notification",
    Notifications_Chat_Color = {255,255,255}
}

TRANSLATIONS = {
	OpenCommandDescription = "Open EUP Menu",
	OpenKeySettings = "Open Car Spawner",
	OpenDashboard = "Press ~INPUT_SELECT_CHARACTER_TREVOR~ to access the Car Spawner",
	NotPossibleToOpenDashboardFromHere = "It's not possible to open the EUP menu from here.",
	NeedToBeAMPPed = "You need to be a MP ped to use the EUP menu.",
}
```

</details>

<details>

<summary><em><strong>Main Madonne EUP Menu configuration</strong></em></summary>

Delay before the script is initialized, in order to receive all the required information before allowing access to the menu.

```lua
Delay_Before_Init = 1000, -- ms
```

Configure the different ways to open the EUP menu.

<pre class="language-lua"><code class="lang-lua"><strong>Enable_Command_To_Open = true,
</strong>Command_To_Open = "eup", -- Without '/'

Enable_Keybind_To_Open = true,
Keybind_To_Open = 'F7', -- Default : F7
</code></pre>

Select if you want that your players must be in a specific area to open the menu. You will can edit this areas later in the file.

```lua
Player_Must_Be_In_Area_To_Open = true,
Set_A_Marker_In_Area = true,
Set_A_NPC_In_Area = false,
```

Edit here all differents areas : coords, detection radius, markers, npcs and departments.

```lua
Areas = {
	[1] = {
		x = -802.311, y = 175.056, z = 72.8446, h = 0.0,
		radius = 5.0,
		marker_type = 21, -- https://docs.fivem.net/docs/game-references/markers/
		marker_color = {r = 255, g = 255, b = 255, a = 255},
		marker_rotation = true, -- true or false
		NPC_Model = "s_m_y_cop_01",
		departments = {"LSPD"}, -- Change {} to false to show all departments
	},
	[2] = {
		x = -802.311, y = 170.056, z = 72.8446, h = 0.0,
		radius = 5.0,
		marker_type = 21, -- https://docs.fivem.net/docs/game-references/markers/
		marker_color = {r = 255, g = 255, b = 255, a = 255},
		marker_rotation = false, -- true or false
		NPC_Model = "s_m_y_cop_01",
		departments = false, -- Change {} to false to show all departments
	},
},
```

Change the notification types between "notification", "other" or "chat".

```lua
Notifications_Type = "notification",
Notifications_Chat_Color = {255,255,255}
```

Edit the various phrases used in notification messages.

```lua
TRANSLATIONS = {
	OpenCommandDescription = "Open EUP Menu",
	OpenKeySettings = "Open Car Spawner",
	OpenDashboard = "Press ~INPUT_SELECT_CHARACTER_TREVOR~ to access the Car Spawner",
	NotPossibleToOpenDashboardFromHere = "It's not possible to open the EUP menu from here.",
	NeedToBeAMPPed = "You need to be a MP ped to use the EUP menu.",
}
```

</details>

<details>

<summary>File : categories.lua</summary>

This file allows you to add new categories to the menu. For each of them, you must add: a name, a logo, if access is restricted and if so, what permission code it is restricted to.

```lua
{
        name = "LSPD",
        logo = "",
	whitelist = false,
        permissionCode = ""
    },
```

</details>

<details>

<summary>File : outfits.lua</summary>

Edit here the list of different clothing presents you want. For each part, this is composed of the number of the clothing, followed by the corresponding texture. The numbers can be taken using "Player Appearence" from the vMenu.

```lua
{
	category = "LSPD",
	name = "Classe A",
	image = "",
	gender = "M",
	whitelist = false,
        permissionCode = "",
	----------------------------
	mask = "1:1",
	upperskin = "7:1",
	pants = "36:1",
	parachute = "33:2",
	shoes = "62:1",
	accessories = "237:1",
	undercoat = "225:1",
	armor = "201:1",
	decal = "1:1",
	top = "201:9",
	hat = "1:1",
	glasses = "1:1",
	ear = "1:1",
	watch = "1:1",
},
```

</details>
