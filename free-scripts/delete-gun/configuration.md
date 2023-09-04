# Configuration

The configuration file (named config.lua) allows you to modify all the different parameters taken into account within our script. In case of problems with the scripts, first check that you have correctly edited this document

<details>

<summary><em><strong>Content of the configuration file by default</strong></em></summary>

```lua
----------------------------------------------------------------------------------------------------
--                           Madonne Studio © 2023 - All rights reserved                          --
--                                                                                                --
--                                       "DELETE GUN - v.1.0.0"                                   --
--                                                                                                --
--               For any issue with this ressource, please contact us on Discord :                --
--                                                                                                --
--                                  https://discord.gg/nmBAJrFhQB                                 --
--                                                                                                --
--                                    https://madonnestudio.com                                   --
--                                    contact@madonnestudio.com                                   --
--                                                                                                --
----------------------------------------------------------------------------------------------------

CONFIG_DELETE_GUN = {
    -- ace | custom
    PERMISSION_SYSTEM = "ace",
    
    WEAPON_TO_USE = "WEAPON_RAYCARBINE",
    AUTOMATICALLY_GIVE_WEAPON = true,

    NOTIFICATION_TEXT = "Entity deleted !",
    -- notification | chat | other
    NOTIFICATION_TYPE = "notification",
    notifChatColor = {255,255,255},
}
```

</details>

<details>

<summary><em>Main Delete Gun Configuration</em></summary>

Configure which permission must be used to give access to the delete gun.

```lua
-- ace | custom
PERMISSION_SYSTEM = "ace",
```



Select which weapon must be used as Delete Gun, and if you want this wepaon to be given automatically to players able to use it.

<pre class="language-lua"><code class="lang-lua"><strong> WEAPON_TO_USE = "WEAPON_RAYCARBINE",
</strong> AUTOMATICALLY_GIVE_WEAPON = true,
</code></pre>



Whether or not to show a notification above the map when an entity is deleted with the delete gun.

```lua
    NOTIFICATION_TEXT = "Entity deleted !",
    -- notification | chat | other
    NOTIFICATION_TYPE = "notification",
    notifChatColor = {255,255,255},
```

</details>
