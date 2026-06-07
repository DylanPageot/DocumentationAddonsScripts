# Anticheat Configuration

The anti-cheat configuration is located at `config/module/cfg_anticheat.lua`.

> ⚠️ **This module requires a Silver or Gold subscription.** It will not run on Bronze plans regardless of configuration.

Each detection module can be independently enabled or disabled, and each has its own configurable ban length and sensitivity settings.

***

## 🚫 Anti Props

Blocks unauthorized prop spawning. If a player spawns any object from the blacklist, they are **immediately and automatically banned**.

```lua
AntiProps = {
    Enabled = true,
    BanLength = "p",
    BlacklistedProps = {
        [GetHashKey("stt_prop_stunt_jump45")] = true,
        -- ...
    }
}
```

| Option             | Type      | Description                                                                           |
| ------------------ | --------- | ------------------------------------------------------------------------------------- |
| `Enabled`          | `boolean` | Enable or disable this detection                                                      |
| `BanLength`        | `string`  | Ban duration applied on detection (uses `BanDurations` codes, e.g. `"p"` = permanent) |
| `BlacklistedProps` | `table`   | List of prop model hashes to block. Use `GetHashKey("model_name")` to add entries     |

> 💡 The default blacklist includes all stunt ramps, tubes, jumps, and various LOD map objects commonly used for griefing.

***

## 💥 Anti Explosions

Detects players generating an abnormal number of explosions in a short period.

```lua
AntiExplosions = {
    Enabled = true,
    BanLength = "p",
    MaxPlaytime = 300,
    WhitelistedExplosions = {
        ['BIRD_CRAP'] = true,
        ['FIREWORK'] = true,
        ['SNOWBALL'] = true,
    }
}
```

| Option                  | Type      | Description                                                                                                      |
| ----------------------- | --------- | ---------------------------------------------------------------------------------------------------------------- |
| `Enabled`               | `boolean` | Enable or disable this detection                                                                                 |
| `BanLength`             | `string`  | Ban duration on detection                                                                                        |
| `MaxPlaytime`           | `number`  | Players with more playtime than this value (in minutes) are **exempt** from this check. Default: `300` (5 hours) |
| `WhitelistedExplosions` | `table`   | Explosion types that are ignored by the counter                                                                  |

***

## 🚗 Anti Vehicle Spam

Detects players spawning vehicles at an abnormally high rate.

```lua
AntiVehiclesSpam = {
    Enabled = true,
    BanLength = "p",
    MaxPlaytime = 300,
}
```

| Option        | Type      | Description                             |
| ------------- | --------- | --------------------------------------- |
| `Enabled`     | `boolean` | Enable or disable this detection        |
| `BanLength`   | `string`  | Ban duration on detection               |
| `MaxPlaytime` | `number`  | Playtime exemption threshold in minutes |

***

## 📡 Anti Trigger Event

Protects your server events from being triggered by unauthorized client-side resources or exploits. Any event triggered from a resource that is not started on the server will automatically ban the player.

```lua
AntiTriggerEvent = {
    Enabled = true,
    BanLength = "p",
    ProtectedClientEvents = {},
    ProtectedServerEvents = {},
}
```

| Option                  | Type      | Description                              |
| ----------------------- | --------- | ---------------------------------------- |
| `Enabled`               | `boolean` | Enable or disable this detection         |
| `BanLength`             | `string`  | Ban duration on detection                |
| `ProtectedClientEvents` | `table`   | Additional client-side events to monitor |
| `ProtectedServerEvents` | `table`   | Additional server-side events to monitor |

***

## ✈️ Anti Noclip

Detects players moving through the air at suspicious speeds and heights without a valid animation or parachute, indicating the use of a noclip exploit.

```lua
AntiNoClip = {
    Enabled = true,
    BanLength = "p",
    MaxPlaytime = 300,
    DistanceTrigger = 20.0,
    MinHeight = 5.0,
    WhitelistedAnimation = {
        {dict = "nm", anim = "firemans_carry"}
    }
}
```

| Option                 | Type      | Description                                                                                                                                    |
| ---------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| `Enabled`              | `boolean` | Enable or disable this detection                                                                                                               |
| `BanLength`            | `string`  | Ban duration on detection                                                                                                                      |
| `MaxPlaytime`          | `number`  | Playtime exemption threshold in minutes                                                                                                        |
| `DistanceTrigger`      | `number`  | Horizontal distance traveled in 2 seconds to trigger detection                                                                                 |
| `MinHeight`            | `number`  | Minimum height above ground required to trigger detection                                                                                      |
| `WhitelistedAnimation` | `table`   | List of animations that exempt a player from detection (add `{dict, anim}` entries for animations that put the player in the air legitimately) |

***

## 👻 Anti Invisible

Detects players who become invisible without a whitelisted animation active.

```lua
AntiInvisible = {
    Enabled = true,
    BanLength = "p",
    MaxPlaytime = 300,
    WhitelistedAnimation = {
        {dict = "nm", anim = "firemans_carry"}
    }
}
```

| Option                 | Type      | Description                                          |
| ---------------------- | --------- | ---------------------------------------------------- |
| `Enabled`              | `boolean` | Enable or disable this detection                     |
| `BanLength`            | `string`  | Ban duration on detection                            |
| `MaxPlaytime`          | `number`  | Playtime exemption threshold in minutes              |
| `WhitelistedAnimation` | `table`   | Animations that legitimately make a player invisible |

***

## 📷 Anti Freecam

Detects players whose camera moves far away from their character position, indicating a freecam exploit.

```lua
AntiFreecam = {
    Enabled = true,
    BanLength = "p",
    MaxPlaytime = 300,
    DistanceTrigger = 50,
    MaxHeight = 45.0
}
```

| Option            | Type      | Description                                                     |
| ----------------- | --------- | --------------------------------------------------------------- |
| `Enabled`         | `boolean` | Enable or disable this detection                                |
| `BanLength`       | `string`  | Ban duration on detection                                       |
| `MaxPlaytime`     | `number`  | Playtime exemption threshold in minutes                         |
| `DistanceTrigger` | `number`  | Distance between the player and the camera to trigger detection |
| `MaxHeight`       | `number`  | Maximum camera height before triggering detection               |

***

## 🔊 Anti Sound

Detects players broadcasting blacklisted sounds at suspicious distances via InteractSound, which is a common exploit vector.

```lua
AntiSound = {
    Enabled = true,
    BanLength = "p",
    MaxPlaytime = 300,
    BlacklistedSounds = {
        {name = "handcuff", maxDistance = 10000},
        {name = "alarm", maxDistance = 5},
        -- ...
    }
}
```

| Option              | Type      | Description                                                                                                               |
| ------------------- | --------- | ------------------------------------------------------------------------------------------------------------------------- |
| `Enabled`           | `boolean` | Enable or disable this detection                                                                                          |
| `BanLength`         | `string`  | Ban duration on detection                                                                                                 |
| `MaxPlaytime`       | `number`  | Playtime exemption threshold in minutes                                                                                   |
| `BlacklistedSounds` | `table`   | List of `{name, maxDistance}` entries. If the exact sound name and distance combination is detected, the player is banned |

***

## 🧹 Anti Clear Tasks

Detects players sending an abnormally high number of `clearPedTask` events in a short window, which is a common method used by menus to force ragdoll other players.

```lua
AntiClearTasks = {
    Enabled = true,
    BanLength = "p",
    MaxPlaytime = 300,
    MaxTasks = 20
}
```

| Option        | Type      | Description                                                                          |
| ------------- | --------- | ------------------------------------------------------------------------------------ |
| `Enabled`     | `boolean` | Enable or disable this detection                                                     |
| `BanLength`   | `string`  | Ban duration on detection                                                            |
| `MaxPlaytime` | `number`  | Playtime exemption threshold in minutes                                              |
| `MaxTasks`    | `number`  | Maximum number of `clearPedTask` events allowed in a 10-second window before banning |

***

## 💡 Notes on Playtime Exemption

Every anti-cheat module has a `MaxPlaytime` option (in minutes). Players whose total playtime on your server exceeds this value are **exempt from that specific detection**. This is the trusted player system — long-time regulars are less likely to be false-positived by movement or camera detections.

The default value of `300` minutes (5 hours) is a reasonable starting point. Adjust it based on your server's population and tolerance for false positives.

