# Configuration



<details>

<summary><em><strong>Content of the configuration file by default</strong></em></summary>

```lua
CONFIG = {
    DEBUG = false,

    Delay_Before_Init = 1000, -- ms
    Delay_Before_Opening_Menu = 200, -- ms
    
    Enable_Command_To_Debug_Shipping = true,
    Command_To_Debug_Shipping = "debug", -- Without '/'
    Enable_Command_To_Open = true,
    Command_To_Open = "vehicle", -- Without '/'
    Enable_Keybind_To_Open = true,
    Keybind_To_Open = 'F7', -- Default : F7
    Player_Must_Be_In_Area_To_Open = true,
    Set_A_Marker_In_Area = true,
    Set_A_NPC_In_Area = false,
    Ship_Vehicle_If_Zero_Slot_Available = true, -- if false, spawn will be impossible and notification will be sent
    ParkingSlotDectionRange = 200, -- Don't do a huge value, may cause lags

    Areas = {
	[1] = {
		x = -802.311, y = 175.056, z = 72.8446, h = 0.0,
		radius = 5.0,
		marker_type = 36, -- https://docs.fivem.net/docs/game-references/markers/
		marker_color = {r = 255, g = 255, b = 255, a = 255},
		marker_rotation = true, -- true or false
		NPC_Model = "s_m_y_cop_01",
		departments = {"LSPD","LSSD"}, -- Change {} to false to show all departments
	},
	[2] = {
		x = -802.311, y = 170.056, z = 72.8446, h = 0.0,
		radius = 5.0,
		marker_type = 36, -- https://docs.fivem.net/docs/game-references/markers/
		marker_color = {r = 255, g = 255, b = 255, a = 255},
		marker_rotation = false, -- true or false
		NPC_Model = "s_m_y_cop_01",
		departments = {}, -- Change {} to false to show all departments
	},
    },
    
    EjectDriverIfCantDrive = true,
    
    Add_Blip_To_Vehicle = true,
    Blip_Sprite = 56,
    Blip_Colour = 57,
    
    Mechano_Ped = {
        {
            vehicle_type = 1,
            ped = "s_m_y_cop_01",
        },
        {
            vehicle_type = 2,
            ped = "s_m_y_fireman_01",
        },
        {
            vehicle_type = 3,
            ped = "s_m_m_paramedic_01",
        },
        {
            vehicle_type = 4,
            ped = "s_m_y_armymech_01",
        },
        {
            vehicle_type = "default",
            ped = "mp_m_waremech_01",
        },

    },

    Cars_Limit_By_Player = true,
    Default_Cars_Limit = 3,
    Permissions_Codes_For_Limits = {
        {
            name = "VIP OR",
            limit = 6
        },
        {
            name = "VIP ARGENT",
            limit = 5
        },
        {
            name = "VIP BRONZE",
            limit = 4
        }
    },

    Notifications_Type = "notification",
    Notifications_Chat_Color = {255,255,255}
}

TRANSLATIONS = {
    Vehicle_Already_Coming = "Un véhicule est déjà en route. Merci de patienter qu'il arrive.",
    Shipping_In_Progress = "Livraison en cours de votre véhicule...",
    Vehicle_On_Nearest_Slot = "Votre véhicule est prêt. Il vous attend sur la place de parking la plus proche !",
    Vehicle_Arrived = "Votre véhicule est arrivé !",
    CantDrive = "Vous n'avez pas accès à ce véhicule.",
    OpenDashboard = "Press ~INPUT_SELECT_CHARACTER_TREVOR~ to access the Car Spawner",
    OpenKeySettings = "Open Car Spawner",
    NotPossibleToOpenDashboardFromHere = "Il n'est pas possible d'ouvrir la tablette d'aparition de véhicules depuis cet endroit.",
    OpenCommandDescription = "Ouvrir la tablette d'apparition de véhicules",
    DebugCommandDescription = "Débugger la livraison des véhicules, lorsqu'elle reste bloqué en \"en route\"",
    NoParkingSlotAvailable = "Aucun emplacement de parking disponible. Véhicule non livré.",
    Shipping_Debugged = "La livraison de véhicule a été débuggée !"
}
```

</details>

<details>

<summary><em><strong>Main Madonne CarSpawner configuration</strong></em></summary>

Delay before the script is initialized, in order to receive all the required information before allowing access to the menu.

```lua
Delay_Before_Init = 1000, -- ms
Delay_Before_Opening_Menu = 200, -- ms
```

Configure the different ways to open the vehicle spawn menu.

```lua
Enable_Command_To_Debug_Shipping = true,
Command_To_Debug_Shipping = "debug", -- Without '/'
Enable_Command_To_Open = true,
Command_To_Open = "vehicle", -- Without '/'
Enable_Keybind_To_Open = true,
Keybind_To_Open = 'F7', -- Default : F7
```

Select if you want that your players must be in a specific area to open the menu. You will can edit this areas later in the file.

```lua
Player_Must_Be_In_Area_To_Open = true,
Set_A_Marker_In_Area = true,
Set_A_NPC_In_Area = false,
```

With this options, you can select if you want to ship the vehicle by an NPC when zero slot available was found in the detection range selected above.

```lua
Ship_Vehicle_If_Zero_Slot_Available = true, -- if false, spawn will be impossible and notification will be sent
ParkingSlotDectionRange = 200, -- Don't do a huge value, may cause lags
```

Edit here all differents areas : coords, detection radius, markers, npcs and departments.

```lua
Areas = {
	[1] = {
		x = -802.311, y = 175.056, z = 72.8446, h = 0.0,
		radius = 5.0,
		marker_type = 36, -- https://docs.fivem.net/docs/game-references/markers/
		marker_color = {r = 255, g = 255, b = 255, a = 255},
		marker_rotation = true, -- true or false
		NPC_Model = "s_m_y_cop_01",
		departments = {"LSPD","LSSD"}, -- Change {} to false to show all departments
	},
	[2] = {
		x = -802.311, y = 170.056, z = 72.8446, h = 0.0,
		radius = 5.0,
		marker_type = 36, -- https://docs.fivem.net/docs/game-references/markers/
		marker_color = {r = 255, g = 255, b = 255, a = 255},
		marker_rotation = false, -- true or false
		NPC_Model = "s_m_y_cop_01",
		departments = {}, -- Change {} to false to show all departments
	},
},
```

Configure if the driver must be kicked out of the vehicle if he is not whitelisted.

```lua
EjectDriverIfCantDrive = true,
```

Configure the display of vehicle blips on the map.

```lua
Add_Blip_To_Vehicle = true,
Blip_Sprite = 56,
Blip_Colour = 57,
```

If a vehicle needs to be brought by an NPC, you can configure the NPC for each type of vehicle here.

```lua
Mechano_Ped = {
    {
        vehicle_type = 1,
        ped = "s_m_y_cop_01",
    },
    {
        vehicle_type = 2,
        ped = "s_m_y_fireman_01",
    },
    {
        vehicle_type = 3,
        ped = "s_m_m_paramedic_01",
    },
    {
        vehicle_type = 4,
        ped = "s_m_y_armymech_01",
    },
    {
        vehicle_type = "default",
        ped = "mp_m_waremech_01",
    },
},
```

Configure here the maximum number of vehicles that a player can spawn at the same time.

```lua
Cars_Limit_By_Player = true,
Default_Cars_Limit = 3,
Permissions_Codes_For_Limits = {
    {
        name = "VIP OR",
        limit = 6
    },
    {
        name = "VIP ARGENT",
        limit = 5
    },
    {
        name = "VIP BRONZE",
        limit = 4
    }
},
```

Change the notification types between "notification" or "chat".

```lua
Notifications_Type = "notification",
Notifications_Chat_Color = {255,255,255}
```

Edit the various phrases used in notification messages.

```lua
TRANSLATIONS = {
    Vehicle_Already_Coming = "Un véhicule est déjà en route. Merci de patienter qu'il arrive.",
    Shipping_In_Progress = "Livraison en cours de votre véhicule...",
    Vehicle_On_Nearest_Slot = "Votre véhicule est prêt. Il vous attend sur la place de parking la plus proche !",
    Vehicle_Arrived = "Votre véhicule est arrivé !",
    CantDrive = "Vous n'avez pas accès à ce véhicule.",
    OpenDashboard = "Press ~INPUT_SELECT_CHARACTER_TREVOR~ to access the Car Spawner",
    OpenKeySettings = "Open Car Spawner",
    NotPossibleToOpenDashboardFromHere = "Il n'est pas possible d'ouvrir la tablette d'aparition de véhicules depuis cet endroit.",
    OpenCommandDescription = "Ouvrir la tablette d'apparition de véhicules",
    DebugCommandDescription = "Débugger la livraison des véhicules, lorsqu'elle reste bloqué en \"en route\"",
    NoParkingSlotAvailable = "Aucun emplacement de parking disponible. Véhicule non livré.",
    Shipping_Debugged = "La livraison de véhicule a été débuggée !"
}
```

</details>

<details>

<summary>File : categories.lua</summary>

This file allows you to add new categories to the menu. For each of them, you must add: a name, a logo, if access is restricted and if so, what permission code it is restricted to.

```lua
{
    name = "LSPD",
    logo = "https://cdn.discordapp.com/attachments/974693738309881928/1122647747070267523/latest.png",
    whitelist = false,
    permissionCode = ""
},
```

</details>

<details>

<summary>File : parkings.lua</summary>

This file contains all the parking spaces that have been recorded. You can change them to your liking.

```lua
-- Vehicle type, X, Y, Z
{0,1110.62,-1506.04,34.03,268.66},
```

</details>

<details>

<summary>File : vehicles.lua</summary>

Add here all the different vehicles you want to appear in the menu. For each vehicle, please specify: its type (civilian = 0, police = 1, fire department = 2, EMS = 3, military = 4), its category, its name, its model, if you wish to appear inside this one or not, its livery, a photo, if access is restricted and the extras which are to be activated or desactivated.

The ids of differents colors can be found [here](https://wiki.rage.mp/index.php?title=Vehicle\_Colors).

```lua
{
    type = 1,
    category = "LSPD",
    name = "2011 Ford CVPI - Rotatif",
    model = "mst11vic",
    spawnIn = false,
    livery = 0,
    photo = "https://media.discordapp.net/attachments/810976379716763688/1017814804733366332/20220908154339_1.jpg?width=810&height=811",
    whitelist = false,
    permissionCode = "",
    extraToEnable = {1,4},
    extraToDisable = {2,3,5,6,7},
    primaryColor = 0,
    secondaryColor = 0,
},
```

</details>
