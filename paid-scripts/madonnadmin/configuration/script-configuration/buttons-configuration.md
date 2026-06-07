# Buttons Configuration

The buttons configuration is located at `config/module/cfg_button.lua`. It defines the **custom quick action buttons** that appear on each player's profile in the admin panel and in the report panel sidebar.

Each button runs a Lua function directly on the **targeted player's client**, allowing you to perform any in-game action on them with a single click.

***

## 📐 Button Structure

```lua
BUTTONS = {
    [1] = {
        Title = "Heal",
        HaveAccess = true,
        EnableCommandForThisButton = true,
        CommandCanBeUsedOnlyInActiveStaff = true,
        CommandCanBeUsedOnHigherRank = false,
        MultiIdsCommand = true,
        CommandName = "heal",
        CommandSuggestionText = "Heal a player",
        AddInReportMenu = true,
        Actions = function()
            SetEntityHealth(PlayerPed, 200)
        end
    },
}
```

| Option                              | Type                 | Description                                                                                                                 |
| ----------------------------------- | -------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| `Title`                             | `string`             | Label displayed on the button in the admin panel                                                                            |
| `HaveAccess`                        | `boolean` \| `table` | `true` = all staff can use this button. Pass a table of rank IDs (e.g. `{1,2,3}`) to restrict access to specific ranks only |
| `EnableCommandForThisButton`        | `boolean`            | If `true`, a chat command is registered for this button so staff can also use it via `/CommandName [ID]`                    |
| `CommandCanBeUsedOnlyInActiveStaff` | `boolean`            | If `true`, the chat command can only be used while in active staff mode                                                     |
| `CommandCanBeUsedOnHigherRank`      | `boolean`            | If `true`, the command can target players with a higher rank than the staff member                                          |
| `MultiIdsCommand`                   | `boolean`            | If `true`, the command accepts multiple player IDs at once (e.g. `/heal 12 34 56`)                                          |
| `CommandName`                       | `string`             | The command name (without `/`)                                                                                              |
| `CommandSuggestionText`             | `string`             | Description shown in the chat suggestion                                                                                    |
| `AddInReportMenu`                   | `boolean`            | If `true`, this button also appears in the report panel sidebar when a staff member handles a report                        |
| `Actions`                           | `function`           | Lua function executed **on the targeted player's client**. `PlayerPed` refers to the target's ped.                          |

***

## 🧩 Default Buttons

Four buttons are included by default:

| # | Title           | Access    | Command       | Description                                                    |
| - | --------------- | --------- | ------------- | -------------------------------------------------------------- |
| 1 | **Heal**        | All staff | `/heal`       | Fully restores the player's health                             |
| 2 | **Kill**        | Ranks 1–5 | `/killplayer` | Kills the player                                               |
| 3 | **(Un)Freeze**  | Ranks 1–5 | `/freeze`     | Toggles the player's freeze state                              |
| 4 | **Fix Vehicle** | All staff | `/fixvcl`     | Repairs the player's current vehicle (engine, body, fuel tank) |

***

## ➕ Adding Custom Buttons

To add a new button, duplicate an existing entry and increment the key number:

```lua
BUTTONS = {
    -- ...existing buttons...
    [5] = {
        Title = "Revive",
        HaveAccess = true,
        EnableCommandForThisButton = true,
        CommandCanBeUsedOnlyInActiveStaff = true,
        CommandCanBeUsedOnHigherRank = false,
        MultiIdsCommand = true,
        CommandName = "revive",
        CommandSuggestionText = "Revive a player",
        AddInReportMenu = true,
        Actions = function()
            SetEntityHealth(PlayerPed, 200)
            NetworkResurrectLocalPlayer(
                GetEntityCoords(PlayerPed), 0, true, false
            )
        end
    },
}
```

> 💡 The `Actions` function is executed **on the targeted player's machine**, so `PlayerPed` always refers to their own character. You have access to all FiveM client-side natives.
