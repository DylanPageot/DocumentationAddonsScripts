# Logs Configuration

<details>

<summary>Default configuration file</summary>

```lua
LOGS = {

	LogsEnabled = {
		Disconnections = true,
		Chat = true,
		Explosions = true,
		Shots = true,
		Injuries = true,
		Death = true,
		Other = true,
	},

	-- Other logs can be edited in custom folders (client and server)

	IgnoredWeapons = {
		"WEAPON_FIREEXTINGUISHER",
        "WEAPON_PETROLCAN"
	},

	MaxLogsShowedInGame = 100
}
```

</details>

```lua
LogsEnabled = {
		Disconnections = true,
		Chat = true,
		Explosions = true,
		Shots = true,
		Injuries = true,
		Death = true,
		Other = true,
},
```

Simply disable or enable certain parts of the logs to receive some and not receive others, depending on your wishes!

```lua
IgnoredWeapons = {
	"WEAPON_FIREEXTINGUISHER",
        "WEAPON_PETROLCAN"
},
```

Some weapons can be disabled to not appear in the firing logs.

```lua
MaxLogsShowedInGame = 100
```

Finally, set the maximum amount of log entries you want to have in the game. Be careful, the larger the amount of data, the greater the network load used by MadonnAdmin.
