# Commands Configuration

<details>

<summary>Default configuration file</summary>

```lua
COMMANDS = {
	AdminChatCommand = {
		Enabled = true,
		Command = "admin",
		ChatColor = {r = 255, g = 255, b = 255},
	},

	NoteCommand = {
		Enabled = true,
		Command = "note",
	},

	CommendCommand = {
		Enabled = true,
		Command = "commend"
	},

	WarnCommand = {
		Enabled = true,
		Command = "warn"
	},

	KickCommand = {
		Enabled = true,
		Command = "kick"
	},

	BanCommand = {
		Enabled = true,
		Command = "ban"
	},

	GoToCommand = {
		Enabled = true,
		CanBeUsedOnHigherRank = false,
		Command = "goto",
	},

	BringCommand = {
		Enabled = true,
		CanBeUsedOnHigherRank = false,
		Command = "bring",
		MultiIds = true,
	},

	ReturnCommand = {
		Enabled = true,
		CanBeUsedOnHigherRank = false,
		Command = "return",
		MultiIds = true,
	},
}
```

</details>

For each command, you can simply change whether it is active or not, as well as the text of the command.
