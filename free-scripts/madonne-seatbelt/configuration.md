---
cover: ../../.gitbook/assets/Voyage Photo Général Linkedin Bannière (12).png
coverY: 8
---

# Configuration

The configuration file (named config.lua) allows you to modify all the different parameters taken into account within our script. In case of problems with the scripts, first check that you have correctly edited this document

<details>

<summary><em><strong>Content of the configuration file by default</strong></em></summary>

```lua
----------------------------------------------------------------------------------------------------
--                           Madonne Studio © 2023 - All rights reserved                          --
--                                                                                                --
--                                    "MADONNE SEATBELT - v.1.0.1"                                --
--                                                                                                --
--               For any issue with this ressource, please contact us on Discord :                --
--                                                                                                --
--                                  https://discord.gg/nmBAJrFhQB                                 --
--                                                                                                --
--                                    https://madonnestudio.com                                   --
--                                    contact@madonnestudio.com                                   --
--                                                                                                --
----------------------------------------------------------------------------------------------------

CONFIG_MADONNE_SEATBELT = {
    -- If you want to disable the seat belts for a particular vehicle, you can enter the model of that vehicle below
    DisableSeatbeltsForThisVehicles = {
        "harley","blazer","blazer2","blazer3","blazer4","blazer5","verus","airtug","caddy","caddy2","caddy3","forklift","mower","tractor","bmx","cruiser","fixter","scorcher","tribike","tribike2","tribike3","gator3"
    },

    -- If you want to disable seat belts for an entire class of vehicle, you can enter the class ID below. To find the list of all vehicle classes, you can go to this address : https://docs.fivem.net/natives/?_0x29439776AAA00A62 
    DisableSeatbeltsForThisVehcilesClasses = {
        8,13,14,15,16,21,22
    },

    -- Change the key associated with the seat belt (default: K). To obtain the code corresponding to the key of your choice, refer to the following site: https://docs.fivem.net/docs/game-references/controls/
    SeatbeltKey = 311,

    -- Activate / Deactivate the display of a warning light when the belt is not fastened.
    ShowBlinker = true,

    --
    ActivateSound = true,
    LoopSound = true,
    Volume = 0.8,

    -- Allows you to add and configure a sound effect simulating putting on your seat belt (or taking it off)
    EnableNotifications = true,
    NotificationsType = "default", -- Availables values : default | custom
    -- If NotificationsType is set to custom, you must to edit the notifs.lua file. You can ask us on Discord if you need any support about this.
    Strings = {
        seatbelt_on = 'Seatbelt : ~g~set',
        seatbelt_off = 'Seatbelt : ~r~removed',
    },

    -- Sensitivity of expulsion from the vehicle in the event of impact
    DiffTrigger = 0.255,
    MinSpeed = 13.9,

    -- Enables and configures the launch of a small alarm when the vehicle is moving at a certain speed without the seat belt on.
    AlarmOnlySpeed = true,
    AlarmSpeed = 20,
    AlarmVolume = 0.2
}
```

</details>

<details>

<summary><em>Main Madonne Seatbelt Configuration</em></summary>

If you want to disable the seatbelts for a particular vehicle, you can enter the model of that vehicle below.

```lua
DisableSeatbeltsForThisVehicles = {
        "harley","blazer","blazer2","blazer3","blazer4","blazer5","verus","airtug","caddy","caddy2","caddy3","forklift","mower","tractor","bmx","cruiser","fixter","scorcher","tribike","tribike2","tribike3","gator3"
    },
```



If you want to disable the seatbelts for an entire class of vehicles, you can enter the class ID below. To find the list of all vehicle classes, you can go to [this website](https://docs.fivem.net/natives/?\_0x29439776AAA00A62).&#x20;

```lua
DisableSeatbeltsForThisVehcilesClasses = {
        8,13,14,15,16,21,22
    },
```



Change the key associated with the seat belt (default : K). To botain the code corresponding to the key of your choice, refer to[ the following site](https://docs.fivem.net/docs/game-references/controls/).

```lua
SeatbeltKey = 311,
```



This parameter allows whether or not to display a visual warning when the seat belt is not fastened.

```lua
ShowBlinker = true,
```



The options below allow you to manager the sound effects when your players put on and take off their seatbelts.

```lua
    ActivateSound = true,
    LoopSound = true,
    Volume = 0.8,
```



Whether or not to show a notification above the map when the belt is fastened and unfastened. You can also choose to setup your custom notification system.

```lua
    EnableNotifications = true,
    NotificationsType = "default", -- Availables values : default | custom
	-- If NotificationsType is set to custom, you must to edit the notifs.lua file. You can ask us on Discord if you need any support about this.
    Strings = {
        seatbelt_on = 'Seatbelt : ~g~set',
        seatbelt_off = 'Seatbelt : ~r~removed',
    },
```



Modify via these two parameters, the sensitivity necessary to eject players who do not have seat belts attached, in the event of an accident.

```lua
    DiffTrigger = 0.255,
    MinSpeed = 13.9,
```



Allows you to activate and configure the presence of an audible alarm when the seat belt is not fastened and the vehicle is moving.

```lua
    AlarmOnlySpeed = true,
    AlarmSpeed = 20,
    AlarmVolume = 0.2
```

</details>
