---
cover: ../../.gitbook/assets/Voyage Photo Général Linkedin Bannière (10).png
coverY: 50.70484581497797
---

# Configuration

The configuration file (named config.lua) allows you to modify all the different parameters taken into account within our script. In case of problems with the scripts, first check that you have correctly edited this document

<details>

<summary><em><strong>Content of the configuration file by default</strong></em></summary>

```lua
CONFIG_WEARABLE_WEAPONS = {
    framework = "none", -- Accepted values : esx | none
    inventory = "none", -- Only if framework is not none. Accepted values : ox | none

    -- This option, if set to true, will force your players to retrieve the whitelist weapons from the trunk of a vehicle.
    heavyWeaponsFromCar = true, -- Accepted values : false | true
    UseNearestDoor = true, -- Only if HeavyWeaponsFromCar is TRUE. Accepted values : false | true
    PlayAnimation = true, -- Only if UserNearestDoor is TRUE. Accepted values : false | true

    -- This option allows you to list the different weapons that can be influenced by the script. Please follow the template below to add new weapons.
    weaponsAccepted = {
        -- Example : ["file_name"] = "WEAPON_ID",                                                                                 
        ["w_ar_carbinerifle"] = "WEAPON_CARBINERIFLE",                                                 
        ["w_ar_assaultrifle"] = "WEAPON_ASSAULTRIFLE",                                                         
        ["w_ar_bullpuprifle"] = "WEAPON_BULLPUPRIFLE",                                                              
        ["w_ar_advancedrifle"] = "WEAPON_ADVANCEDRIFLE",                                                            
                                                                                                                                                                                                        
        ["w_sb_assaultsmg"] = "WEAPON_ASSAULTSMG",                                                                  
        ["w_sb_smg"] = "WEAPON_SMG",                                                                                
        ["w_sb_smgmk2"] = "WEAPON_SMGMk2",                                                                          
        ["w_sb_gusenberg"] = "WEAPON_GUSENBERG",                                                                    
        ["w_mg_combatmg"] = "WEAPON_COMBATMG",       
        ["w_sb_microsmg"] = "WEAPON_MICROSMG",                          
                                                                                                                                                                                                                    
        ["w_sr_sniperrifle"] = "WEAPON_SNIPERRIFLE",                                                                
        ["w_sr_marksmanrifle"] = "WEAPON_MARKSMANRIFLE",                                                            
        ["w_sr_heavysniper"] = "WEAPON_HEAVYSNIPER",                                                                
                                                                                                                                                                                                                
        ["w_sg_assaultshotgun"] = "WEAPON_ASSAULTSHOTGUN",                                                          
        ["w_sg_bullpupshotgun"] = "WEAPON_BULLPUPSHOTGUN",                                                          
        ["w_sg_pumpshotgun"] = "WEAPON_PUMPSHOTGUN",		
        ["w_ar_musket"] = "WEAPON_MUSKET",                                                                          
        ["w_sg_heavyshotgun"] = "WEAPON_HEAVYSHOTGUN",

        ["w_ar_carbineriflemk2"] = "WEAPON_CARBINERIFLE_MK2",
        ["w_ar_specialcarbine"] = "WEAPON_SPECIALCARBINE"
    },

	-- back_bone : 11816 = back | 24816 = front | 51826 = side
	attachedBones = { -- 
		back_bone = { 11816 ,24816,     24816,    24816,    11816,    11816,    51826,	  24816},
		x = {		  -0.35 ,0.28,      -0.02,    -0.090,   -0.22,    -0.070,   0.15,     -0.05},
		y = {		  0.18  ,-0.15,     -0.05,    -0.15,    0.17,     0.16,     0.07,     -0.16},
		z = {		  -0.05 ,0.02,      0.05,     -0.080,   -0.020,   -0.030,   0.11,     -0.14},
		x_rotation = {360.0 ,0.0,       -4.0,     -180.0,   183.0,    -183.0,   -89.0,    0},
		y_rotation = {-40.0 ,165.0,     47.0,     -515.0,   -538.0,   -505.0,   -540.0,   -15},
		z_rotation = {1.0	,0.0,		-534.3,   -5.0,     0,        4.0,      2.0,      -7}
	},

    -- This option determines whether the weapon should be worn on the chest or on the back by default.
    default_position = 2, -- Accepted values : 1 (Chest) | 2 (Back)

    bags_can_contain_weapons = true,
    bags_eup = {41,45}

    -- Select whether or not the player can choose himself between placing his weapon on his back and placing his weapon on the chest. (Command to use : /weaponposition)
    playerCanChangePosition = true, -- Accepted values : false | true

    -- Here you can change the name of the command used to allow the player to choose the location of the weapon they will carry. (Default : weaponposition) (Used if playerCanChangePosition = true)
    commandUsedToChangePosition = "weaponposition", -- Accepted values : text (without the / )

	-- Here you can change all settings about Drop Command and the ability to your player to drop a weapon at ground
    enableDropCommand = true,
    commandUsedToDropWeapon = "drop",
    msg_suggDrop = "Drop the weapon you are currently holding",
    dropAnimDict = "random@domestic",
    dropAnimName = "pickup_low",

    -- This command will allow you to debug your players in case of problems with the script. This will reset the state of the weapon port.
    commandUsedToDebugWeaponWearing = "debugweapon", -- Accepted values : text (without the / )

    -- This prefix corresponds to the name that will be entered at the start of the notifications, related to this script, which will be displayed in the game.
    globalPrefix = "~r~[MyServer] ~c~", -- Accepted values : text
    globalPrefixBis = "MyServer", -- Accepted values : text

    -- Position of notifications.
    notifPos = "notification", -- Accepted values : notification | chat | other | none
    -- Notification : In bottom left corner, just on the map
    -- Chat : In the chat
    -- Other : Use a custom notifications system (see notif.lua)
    -- None : Desactivate notifications

    -- Change color of notification in case of notifPos = "chat"
    notifChatColor = {255,0,0}, -- Accepted values = RGB Color code = {R,G,B},

    -- Message indicating to the player that he must be in front of a vehicle to be able to equip himself with the weapon he has selected. (Used if heavyWeaponsFromCar = true)
    msg_needCar = "You must be in front of a vehicle to take out this weapon.", -- Accepted values : text

    -- Message indicating to the player that he must drop the weapon he has on him before he can get a new one out of the car. (Used if heavyWeaponsFromCar = true)
    msg_alreadyWeared = "You must put down your gun before picking up a new one.", -- Accepted values : text

    -- Message indicating to the player that his attached weapon was just deleted from his inventory.
    msg_weaponDeleted = "You no longer have the attached weapon in your inventory.", -- Accepted values : text

    -- One of these two notifications will be displayed when the player changes the position of their weapon. (Used if playerCanChangePosition = true)
    msg_emptyargs = "You must specify which position you want",
    msg_changingPosTo = "You will now carry your weapon on this position : ", -- Accepted values : text
    msg_dontexist = "Position don't exist, please check your command's args.",

    -- This sentence will be displayed when the command to change the position of the weapon is suggested. (Used if playerCanChangePosition = true)
    msg_suggChangePosition = "Allows you to change the position of the weapon (chest or back).", -- Accepted values : text

    -- This sentence will be displayed when the command to debug the weapon port is suggested.
    msg_suggDebug = "Command to use in case of problems with carrying a weapon. This will reset the latter to its default state.", -- Accepted values : text

}

CONFIG_HOLSTER = {
    weapon = { 
        'WEAPON_PISTOL',
        'WEAPON_COMBATPISTOL',
        'WEAPON_APPISTOL',
        'WEAPON_PISTOL50',
        'WEAPON_SNSPISTOL',
        'WEAPON_HEAVYPISTOL',
        'WEAPON_PISTOLXM3',
        'WEAPON_SNSPISTOL_MK2',
        'WEAPON_RAYPISTOL',
        'WEAPON_REVOLVER_MK2',
        'WEAPON_RAYPISTOL',
        'WEAPON_DOUBLEACTION',
        'WEAPON_VINTAGEPISTOL',
        'WEAPON_GADGETPISTOL',
        'WEAPON_FLAREGUN',
        'WEAPON_NAVYREVOLVER',
        'WEAPON_MARKSMANPISTOL',
        'WEAPON_REVOLVER',
        'WEAPON_PISTOL_MK2',
    },

    -- Which position of holster must be used by default : side | back | front | leg
    DefaultHolsterAnimation = "front",

    -- For each groups of components, as this examples, you must provide depanding of your EUP : ped, component, drawable.

    -- Components used as holster
    SideHolsterComponents = {
        --{"mp_m_freemode_01",{{7,{1,3,6,5,8,2,42,43,110,111,119,120}},{8,{16,18}}}}
    },

    -- Components used as holster
    BackHolsterComponents = {

    },

    -- Components used as holster
    FrontHolsterComponents = {

    },

    -- Components used as holster
    SideLegHolsterAnimation = {

    },

    -- This command will allow you to change the holster animation. You can also change all differents texts for this functionnality.
    commandUsedToChangeHolsterAnim = "changeHolsterAnim", -- Accepted values : text (without the / )
    msg_changingAnim = "Animation changed to : ",
    msg_suggChangeAnim = "Change your default animation when you try to get a pistol from your holster.",
    msg_AnimType = "Available animation type.",
    msg_error = "An error has occured. Please try again."
}

CONFIG_AIM = {
    WEAPONS = {
        'WEAPON_PISTOL',
        'WEAPON_COMBATPISTOL',
        'WEAPON_APPISTOL',
        'WEAPON_PISTOL50',
        'WEAPON_SNSPISTOL',
        'WEAPON_HEAVYPISTOL',
        'WEAPON_PISTOLXM3',
        'WEAPON_SNSPISTOL_MK2',
        'WEAPON_RAYPISTOL',
        'WEAPON_REVOLVER_MK2',
        'WEAPON_RAYPISTOL',
        'WEAPON_DOUBLEACTION',
        'WEAPON_VINTAGEPISTOL',
        'WEAPON_GADGETPISTOL',
        'WEAPON_FLAREGUN',
        'WEAPON_NAVYREVOLVER',
        'WEAPON_MARKSMANPISTOL',
        'WEAPON_REVOLVER',
        'WEAPON_PISTOL_MK2',
    },

    DefaultAnim = "Default", -- Default - GangsterAS - HillbillAS
    commandUsedToChangeAimAnim = "changeAimAnim",
    msg_changingAnim = "The aim animation has been changed to : ",
    msg_suggChangeAnim = "Change your default aiming animation.",
    msg_AnimType = "Available animation type."
}
```

</details>

<details>

<summary><em><strong>Main Wearable Weapons configuration</strong></em></summary>

Select here your framework and your inventory system.

```lua
framework = "none", -- Accepted values : esx | none
inventory = "none", -- Only if framework is not none. Accepted values : ox | none
```



This option, if set to true, will force your players to retrieve the whitelist weapons from the trunk of a vehicle. If UseNearestDoor is set to true, you will always use the nearest door of the vehicle to take your weapon.

```lua
heavyWeaponsFromCar = true,
UseNearestDoor = true, -- Only if HeavyWeaponsFromCar is TRUE. Accepted values : false | true
PlayAnimation = true, -- Only if UserNearestDoor is TRUE. Accepted values : false | true
```



This option allows you to list the different weapons that can be influenced by the script. The weapons present in this list must be taken out from a trunk of a vehicle.

```lua
weaponsAccepted = {
        -- Example : ["file_name"] = "WEAPON_ID",
        ["w_ar_carbinerifle"] = "WEAPON_CARBINERIFLE",
        ["w_ar_carbineriflemk2"] = "WEAPON_CARBINERIFLE_MK2",
        ["w_ar_assaultrifle"] = "WEAPON_ASSAULTRIFLE",
        ["w_ar_specialcarbine"] = "WEAPON_SPECIALCARBINE",
        ["w_ar_bullpuprifle"] = "WEAPON_BULLPUPRIFLE",
        ["w_ar_advancedrifle"] = "WEAPON_ADVANCEDRIFLE",

        ["w_sb_assaultsmg"] = "WEAPON_ASSAULTSMG",
        ["w_sb_smg"] = "WEAPON_SMG",
        ["w_sb_smgmk2"] = "WEAPON_SMGMk2",
        ["w_sb_gusenberg"] = "WEAPON_GUSENBERG",
        ["w_mg_combatmg"] = "WEAPON_COMBATMG",
        ["w_sb_microsmg"] = "WEAPON_MICROSMG",

        ["w_sr_sniperrifle"] = "WEAPON_SNIPERRIFLE",
        ["w_sr_marksmanrifle"] = "WEAPON_MARKSMANRIFLE",
        ["w_sr_heavysniper"] = "WEAPON_HEAVYSNIPER",

        ["w_sg_assaultshotgun"] = "WEAPON_ASSAULTSHOTGUN",
        ["w_sg_bullpupshotgun"] = "WEAPON_BULLPUPSHOTGUN",
        ["w_sg_pumpshotgun"] = "WEAPON_PUMPSHOTGUN",
        ["w_ar_musket"] = "WEAPON_MUSKET",
        ["w_sg_heavyshotgun"] = "WEAPON_HEAVYSHOTGUN",

        ["w_ar_carbineriflemk2"] = "WEAPON_CARBINERIFLE_MK2",
        ["w_ar_specialcarbine"] = "WEAPON_SPECIALCARBINE"
    },
```

This option determines all differents possibles positions to wear your weapon on your player. You can also determine wheter the weapon should be worn on the chest or on the back of the player by default.

```lua
attachedBones = { -- 
		back_bone = { 11816 ,24816,     24816,    24816,    11816,    11816,    51826,	  24816},
		x = {		  -0.35 ,0.28,      -0.02,    -0.090,   -0.22,    -0.070,   0.15,     -0.05},
		y = {		  0.18  ,-0.15,     -0.05,    -0.15,    0.17,     0.16,     0.07,     -0.16},
		z = {		  -0.05 ,0.02,      0.05,     -0.080,   -0.020,   -0.030,   0.11,     -0.14},
		x_rotation = {360.0 ,0.0,       -4.0,     -180.0,   183.0,    -183.0,   -89.0,    0},
		y_rotation = {-40.0 ,165.0,     47.0,     -515.0,   -538.0,   -505.0,   -540.0,   -15},
		z_rotation = {1.0	,0.0,		-534.3,   -5.0,     0,        4.0,      2.0,      -7}
},

default_position = 2,
```

Select if you want to let the possibility to your players to get weapons from bag, and if yes, in which bags

```
bags_can_contain_weapons = true,
bags_eup = {41,45}
```

Select whether or not the player can choose himself between placing his weapon on his back and placing his weapon on the chest. (Command by default : /weaponposition)

```lua
 playerCanChangePosition = true,
```



Here you can change the name of commands and enable (or disable) the weapon drop functionnality. The first one is used to allow the player to choose the location of the weapon they will carry. The second one will allow a player to be debugged in case of problems with the script. This will reset the state of the weapon port.

```lua
commandUsedToChangePosition = "weaponposition",
enableDropCommand = true,
commandUsedToDropWeapon = "drop",
msg_suggDrop = "Drop the weapon you are currently holding",
dropAnimDict = "random@domestic",
dropAnimName = "pickup_low",
commandUsedToDebugWeaponWearing = "debugweapon",
```



This prefixs correspond to the name that will be entered at the start of the notifications, related to this script, which will be displayed in the game.

```lua
globalPrefix = "~r~[MyServer] ~c~",
globalPrefixBis = "MyServer",
```



This is will allow you to move the position of notificatinos between : the classic GTA notification system, the chat, a custom notification system or simply desactivate notifications.

```lua
notifPos = "notification",
```

In the case where you want to show notifications in the chat, you can edit the chat color message (RGB code is used).

```lua
notifChatColor = {255,0,0},
```



All further lines give you the opportunity to edit (or translate) sentences sent by the script.&#x20;



```lua
msg_needCar = "You must be in front of a vehicle to take out this weapon.",
msg_alreadyWeared = "You must put down your gun before picking up a new one.",
msg_changingPosTo1 = "You will now carry your weapon on your chest.",
msg_changingPosTo2 = "You will now carry your weapon on your back.",
msg_suggChangePosition = "Allows you to change the position of the weapon (chest or back).",
msg_suggDebug = "Command to use in case of problems with carrying a weapon. This will reset the latter to its default state.",
```

</details>

<details>

<summary><em><strong>Holster system configuration</strong></em></summary>

This option allows you to list the different weapons that can be influenced by the scripts. The weapons present in this list will be animated by the holster system.

```lua
    weapon = { 
        'WEAPON_PISTOL',
        'WEAPON_COMBATPISTOL',
        'WEAPON_APPISTOL',
        'WEAPON_PISTOL50',
        'WEAPON_SNSPISTOL',
        'WEAPON_HEAVYPISTOL',
        'WEAPON_PISTOLXM3',
        'WEAPON_SNSPISTOL_MK2',
        'WEAPON_RAYPISTOL',
        'WEAPON_REVOLVER_MK2',
        'WEAPON_RAYPISTOL',
        'WEAPON_DOUBLEACTION',
        'WEAPON_VINTAGEPISTOL',
        'WEAPON_GADGETPISTOL',
        'WEAPON_FLAREGUN',
        'WEAPON_NAVYREVOLVER',
        'WEAPON_MARKSMANPISTOL',
        'WEAPON_REVOLVER',
        'WEAPON_PISTOL_MK2',
    },
```



With this option, you will can edit which animation is used to get a pistol from a holster.

```lua
    DefaultHolsterAnimation = "front",
```



This part is a little more complicated and allows you to specify which animation should be used and under what circumstances. You must enter the different accessories available on your server (via EUP in particular) for each of the peds that can carry them.

```lua

    SideHolsterComponents = {
        {"mp_m_freemode_01",{{7,{1,3,6,5,8,2,42,43,110,111,119,120}},{8,{16,18}}}}
    },

    BackHolsterComponents = {

    },

    FrontHolsterComponents = {

    },
    
    SideLegHolsterAnimation = {

    }
```

For each ped, you need to enter the model of the ped, and each accessories for each categories. If you need help to configure this part, don't hesitate to ask us on our Discord.



This command will allow you to change the holster animation. You can also change all differents texts for this functionnality.

````lua
```
    commandUsedToChangeHolsterAnim = "changeHolsterAnim", -- Accepted values : text (without the / )
    msg_changingAnim = "Animation changed to : ",
    msg_suggChangeAnim = "Change your default animation when you try to get a pistol from your holster.",
    msg_AnimType = "Available animation type.",
    msg_error = "An error has occured. Please try again."
```
````

</details>

<details>

<summary>Aim animation configuration</summary>

This option allows you to list the different weapons that can be influenced by the scripts. The weapons present in this list will be animated by the aiming animation system.

```
    weapon = { 
        'WEAPON_PISTOL',
        'WEAPON_COMBATPISTOL',
        'WEAPON_APPISTOL',
        'WEAPON_PISTOL50',
        'WEAPON_SNSPISTOL',
        'WEAPON_HEAVYPISTOL',
        'WEAPON_PISTOLXM3',
        'WEAPON_SNSPISTOL_MK2',
        'WEAPON_RAYPISTOL',
        'WEAPON_REVOLVER_MK2',
        'WEAPON_RAYPISTOL',
        'WEAPON_DOUBLEACTION',
        'WEAPON_VINTAGEPISTOL',
        'WEAPON_GADGETPISTOL',
        'WEAPON_FLAREGUN',
        'WEAPON_NAVYREVOLVER',
        'WEAPON_MARKSMANPISTOL',
        'WEAPON_REVOLVER',
        'WEAPON_PISTOL_MK2',
    },
```

With this option, you will can edit which animation is used to aim.

```lua
    DefaultAnim = "Default", -- Default - GangsterAS - HillbillAS
```

This command will allow you to change the aiming animation. You can also change all differents texts for this functionnality.

```lua
    commandUsedToChangeAimAnim = "changeAimAnim",
    msg_changingAnim = "The aim animation has been changed to : ",
    msg_suggChangeAnim = "Change your default aiming animation.",
    msg_AnimType = "Available animation type."
```

</details>
