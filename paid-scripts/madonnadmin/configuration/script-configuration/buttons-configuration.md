# Buttons Configuration

<details>

<summary>Default configuration file</summary>

```lua
BUTTONS = {
	-- Use this models to create buttons on differents in game player profiles
	[1] = {
		Title = "Heal",
		HaveAccess = true, -- true = visible for all staffs | {1,2,3} = visible only for this ranks
		Actions = function()
			if IsPedMale(PlayerPedId()) then
				SetEntityHealth(PlayerPedId(),200)
			else
				SetEntityHealth(PlayerPedId(),100)
			end
		end
	},
	[2] = {
		Title = "Tuer",
		HaveAccess = {1,2,3,4,5},
		Actions = function()
			SetEntityHealth(PlayerPedId(),0)
		end
	},
	[3] = {
		Title = "Dégeler / Geler",
		HaveAccess = {1,2,3,4,5},
		Actions = function()
			PlayerFrozen = not PlayerFrozen
		end
	},
	[4] = {
		Title = "Réparer le véhicule",
		HaveAccess = true,
		Actions = function()
			local vcl = GetVehiclePedIsIn(PlayerPedId(),false)
			SetVehicleEngineHealth(vcl, 1000.0)
			SetVehicleBodyHealth(vcl, 1000.0)
			SetVehiclePetrolTankHealth(vcl, 1000.0)
			SetVehicleFixed(vcl)
		end
	},
}
```

</details>

Player profile pages in games have several buttons. The first 4 correspond to teleport options and can be managed from the role settings, on the Web Dashboard.

For each button, you can choose a name, the ranks that have access to it, and the actions that this button will perform. These actions will be performed client-side. Do not hesitate to contact us for any help.
