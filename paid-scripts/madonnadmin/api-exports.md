# API / Exports

In order to make Madonn'Admin usable from other resources, exports/events have been planned. Here is their list and how to use them.

If you need specific access to Madonn'Admin, do not hesitate to contact us, we can unlock new exports to suit your needs.

## To use in a client-side script

```lua
GetStaffRank()
```

Returns as int, the rank of the player who is performing the function.

* -1 = Owner
* 0 = Player
* 1 + = Staff Member

```lua
IsPlayerTrusted()
```

Returns false if the player who is performing the function have one of this following flags :

* Last Chance
* Sanction Lover
* Untrusted
* Untrusted +

```lua
TriggerServerEvent("MadonnAdmin:SendBroadcast",message)
```

Send a message to all players, through Madonn'Admin

* Message (string) = Message that you want to send to everyone



## To use in a server-side script

```lua
GetStaffLevelServerSide(source)
```

Returns as int, the rank of the player specified

* -1 = Owner
* 0 = Player
  * 1 + = Staff Member

```lua
TriggerEvent("MadonnAdmin:SendBroadcast",message)
```

Send a message to all players, through Madonn'Admin

* Message (string) = Message that you want to send to everyone

