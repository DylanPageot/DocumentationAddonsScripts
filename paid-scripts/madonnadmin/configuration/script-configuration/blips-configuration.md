# Blips Configuration

<details>

<summary>Default configuration file</summary>

```lua
ShowPlayerBlipsForActiveStaffs = true,

BlipSpritePlayerOnFoot = 1,
BlipSpritesForVehicleClasses = {
		['0'] = 225, -- Compacts
		['1'] = 225, -- Sedans
		['2'] = 225, -- SUVs
		['3'] = 225, -- Coupes
		['4'] = 225, -- Muscle
		['5'] = 225, -- Sports Classics
		['6'] = 225, -- Sports
		['7'] = 225, -- Super
		['8'] = 226, -- Motorcycles
		['9'] = 225, -- Off-road
		['10'] = 67, -- Industrial
		['11'] = 632, -- Utility
		['12'] = 616, -- Vans
		['13'] = 226, -- Cycles
		['14'] = 427, -- Boats
		['15'] = 43, -- Helicopters
		['16'] = 307, -- Planes
		['17'] = 225,	-- Service
		['18'] = 56, -- Emergency
		['19'] = 421, -- Military
		['20'] = 225, -- Commercial
		['21'] = 225, -- Trains
		['22'] = 225, -- Open Wheel
},

DistanceToShowBlipsAndNames = 100.0,

SubMarine = {
		Abbreviation = "SB",
		Color = 150,
		ShowActuallyTalking = true,
		ShowHealth = true,
		
		AbbreviationHigherRanks = "SB",
		ColorHigherRanks = 150,
		ShowActuallyTalkingHigherRanks = true,
		ShowHealthHigherRanks = false,
},

ActiveStaff = {
		Color = 176,
		ShowActuallyTalking = true,
		ShowHealth = true,
		
		ShowNameForPlayers = true,
		ShowActuallyTalkingForPlayers = true,
		ShowHealthForPlayers = false,
		ColorForPlayers = 1
},

PlayerBlips = {
		ShowActuallyTalking = true,
		ShowActuallyDriving = true,
		DriverPrefix = "C",
		ShowHealth = true,

		TrustLevelInNames = {
			Enabled = true,
			Default = 1,
			Trusted = 18,
			Untrusted = 6
		},
},

DeadPlayersBlips = {
		Enabled = true,
		BlipSprite = 310,
		BlipCategory = 10,
		DisplayOnMinimapOnlyAtShortRange = true,
		DelayBeforeRemovingBlip = 5, -- in minutes
},

HighDensityZones = {
		Enabled = true,
		Radius = 150.0,
		BlipSprite = 9,
		BlipAlpha = 100,
		BlipRotation = 50,
		DisplayOnMinimapOnlyAtShortRange = true,

		HighDensity = {
			Density = 30,
			Color = 59,
		},
		MediumDensity = {
			Density = 20,
			Color = 47,
		},
		LowDensity = {
			Density = 10,
			Color = 60,
		}
}
```

</details>

<pre class="language-lua"><code class="lang-lua"><strong>ShowPlayerBlipsForActiveStaffs = true,
</strong></code></pre>

Enable or disable names of each players. Each player will have a blip on each position. You can custom differents blips :

```lua
BlipSpritePlayerOnFoot = 1,
BlipSpritesForVehicleClasses = {
		['0'] = 225, -- Compacts
		['1'] = 225, -- Sedans
		['2'] = 225, -- SUVs
		['3'] = 225, -- Coupes
		['4'] = 225, -- Muscle
		['5'] = 225, -- Sports Classics
		['6'] = 225, -- Sports
		['7'] = 225, -- Super
		['8'] = 226, -- Motorcycles
		['9'] = 225, -- Off-road
		['10'] = 67, -- Industrial
		['11'] = 632, -- Utility
		['12'] = 616, -- Vans
		['13'] = 226, -- Cycles
		['14'] = 427, -- Boats
		['15'] = 43, -- Helicopters
		['16'] = 307, -- Planes
		['17'] = 225,	-- Service
		['18'] = 56, -- Emergency
		['19'] = 421, -- Military
		['20'] = 225, -- Commercial
		['21'] = 225, -- Trains
		['22'] = 225, -- Open Wheel
},
```

```lua
DistanceToShowBlipsAndNames = 100.0,
```

You can also set a custom distance to show each blips and names.

```lua
SubMarine = {
		Abbreviation = "SB",
		Color = 150,
		ShowActuallyTalking = true,
		ShowHealth = true,
		
		AbbreviationHigherRanks = "SB",
		ColorHigherRanks = 150,
		ShowActuallyTalkingHigherRanks = true,
		ShowHealthHigherRanks = false,
},
```

Submarine mode allows staffs with permission to activate their active staff, without players being able to see it. This can be a good solution to monitor players without being noticed as staff. Here you can modify some information about this mode, which will be visible to people of a similar or higher rank to the staff in question.

```lua
ActiveStaff = {
		Color = 176,
		ShowActuallyTalking = true,
		ShowHealth = true,
		
		ShowNameForPlayers = true,
		ShowActuallyTalkingForPlayers = true,
		ShowHealthForPlayers = false,
		ColorForPlayers = 1
},
```

Same principle for displaying active staff.

```lua
PlayerBlips = {
		ShowActuallyTalking = true,
		ShowActuallyDriving = true,
		DriverPrefix = "C",
		ShowHealth = true,

		TrustLevelInNames = {
			Enabled = true,
			Default = 1,
			Trusted = 18,
			Untrusted = 6
		},
},
```

Here you can change how player names are displayed in-game, for staffs. You can notably change the prefix for vehicle drivers and whether you want the trustscore to be displayed on the player's nickname or not, in the form of a color: green for trusted players, red for untrusted players.

```lua
DeadPlayersBlips = {
		Enabled = true,
		BlipSprite = 310,
		BlipCategory = 10,
		DisplayOnMinimapOnlyAtShortRange = true,
		DelayBeforeRemovingBlip = 5, -- in minutes
},
```

For each player killed, staff members will see a dot displayed on the map for 5 minutes (default). You can change how these blips are displayed here.

```lua
HighDensityZones = {
		Enabled = true,
		Radius = 150.0,
		BlipSprite = 9,
		BlipAlpha = 100,
		BlipRotation = 50,
		DisplayOnMinimapOnlyAtShortRange = true,

		HighDensity = {
			Density = 30,
			Color = 59,
		},
		MediumDensity = {
			Density = 20,
			Color = 47,
		},
		LowDensity = {
			Density = 10,
			Color = 60,
		}
}
```

Finally, high density areas are displayed for staff in moderation, when more than 10% of the server (by default, modifiable in density) is in the same sector. Different color codes can be indicated according to your wishes, for more or less dense areas.
