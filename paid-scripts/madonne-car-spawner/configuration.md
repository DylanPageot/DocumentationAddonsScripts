# Configuration



<details>

<summary><em><strong>Content of the configuration file by default</strong></em></summary>

```lua
CONFIG = {
    Delay_Before_Init = 1000, -- ms
    
    Enable_Command_To_Open = true,
    Command_To_Open = "vehicle", -- Without '/'
    Enable_Keybind_To_Open = true,
    Keybind_To_Open = 168, -- Default : F7
    
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
    CantDrive = "Vous n'avez pas accès à ce véhicule."
}
```

</details>

<details>

<summary><em><strong>Main Madonne CarSpawner configuration</strong></em></summary>

Delay before the script is initialized, in order to receive all the required information before allowing access to the menu.

```lua
    Delay_Before_Init = 1000, -- ms
```

Configure the different ways to open the vehicle spawn menu.

```lua
    Enable_Command_To_Open = true,
    Command_To_Open = "vehicle", -- Without '/'
    Enable_Keybind_To_Open = true,
    Keybind_To_Open = 168, -- Default : F7
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
    CantDrive = "Vous n'avez pas accès à ce véhicule."
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
