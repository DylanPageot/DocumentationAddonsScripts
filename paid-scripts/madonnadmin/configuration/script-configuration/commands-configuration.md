# Commands Configuration

The commands configuration is located at `config/module/cfg_commands.lua`. It allows you to enable, disable, and rename every in-game command available to staff members.

***

## 🔤 Command Suggestions

```lua
CommandSuggestions = true,
```

If `true`, all enabled commands will display auto-complete suggestions in the FiveM chat box when a staff member starts typing the command.

***

## 📋 Available Commands

### Admin Chat

```lua
AdminChatCommand = {
    Enabled = true,
    Command = "admin",
    ChatColor = {r = 255, g = 255, b = 255},
}
```

Send a private message visible only to online staff members.

| Option      | Description                                      |
| ----------- | ------------------------------------------------ |
| `Enabled`   | Enable or disable the command                    |
| `Command`   | Command name without `/`. Default: `"admin"`     |
| `ChatColor` | RGB color of admin chat messages in the chat box |

***

### Note

```lua
NoteCommand = {
    Enabled = true,
    Command = "note",
}
```

Add a private internal note to a player's profile. Notes are visible only to staff on the web dashboard and in the admin panel.

Usage: `/note [ID] [reason]`

***

### Commend

```lua
CommendCommand = {
    Enabled = true,
    Command = "commend",
}
```

Add a positive commendation to a player's sanction history.

Usage: `/commend [ID] [reason]`

***

### Warn

```lua
WarnCommand = {
    Enabled = true,
    Command = "warn",
}
```

Issue a formal warning to a player. The warning is saved to their permanent profile and displayed as a splash message.

Usage: `/warn [ID] [reason]`

***

### Kick

```lua
KickCommand = {
    Enabled = true,
    Command = "kick",
}
```

Remove a player from the server immediately.

Usage: `/kick [ID] [reason]`

***

### Ban

```lua
BanCommand = {
    Enabled = true,
    Command = "ban",
}
```

Ban a player for a specified duration or permanently.

Usage: `/ban [ID] [duration] [reason]`

**Duration examples:** `30m`, `2h`, `7d`, `2w`, `1mo`, `p` (permanent), `c` (community ban)

***

### Go To

```lua
GoToCommand = {
    Enabled = true,
    CanBeUsedOnHigherRank = false,
    Command = "goto",
}
```

Teleport to a player's position.

Usage: `/goto [ID]`

| Option                  | Description                                                                     |
| ----------------------- | ------------------------------------------------------------------------------- |
| `CanBeUsedOnHigherRank` | If `false`, staff cannot teleport to players with a higher rank than themselves |

***

### Bring

```lua
BringCommand = {
    Enabled = true,
    CanBeUsedOnHigherRank = false,
    Command = "bring",
    MultiIds = true,
}
```

Teleport one or several players to your position.

Usage: `/bring [ID]` or `/bring [ID1] [ID2] [ID3]` if `MultiIds` is `true`

***

### Return

```lua
ReturnCommand = {
    Enabled = true,
    CanBeUsedOnHigherRank = false,
    Command = "return",
    MultiIds = true,
}
```

Send a player back to their position before the last teleportation.

Usage: `/return [ID]`

***

### Spectate

```lua
SpectateCommand = {
    Enabled = true,
    CanBeUsedOnHigherRank = false,
    Command = "spectate",
    MultiIds = false,
}
```

Discretely spectate a player from their perspective.

Usage: `/spectate [ID]`

Press `F` in-game to exit spectate mode.

***

> 💡 Custom action buttons defined in `cfg_button.lua` with `EnableCommandForThisButton = true` also register their own commands automatically and will appear as suggestions if `CommandSuggestions` is `true`.

