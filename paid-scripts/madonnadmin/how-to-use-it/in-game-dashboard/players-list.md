# Players list

The player list interface displays all players currently connected to the server in a detailed table. For each player you can see their nickname, in-game ID, cumulative playtime, first connection date, and a summary of their sanctions (warns, kicks, bans).

Clicking on a player's nickname opens their **Madonn'Admin profile** directly within the in-game menu, where you can view detailed statistics, connection history, and past sanctions.

<figure><img src="../../../../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>

***

## Direct Action Buttons

Each player profile includes a series of **action buttons** for common moderation interventions, executable in one click without typing any command.

The following actions are available by default and can be fully customized in the resource configuration files:

| Button              | Description                                                  |
| ------------------- | ------------------------------------------------------------ |
| 🚀 **Goto**         | Teleport to the player's position                            |
| 🚗 **Goto Vehicle** | Teleport to the player's vehicle                             |
| 🔄 **Bring**        | Teleport the player to your position                         |
| ↩️ **Return**       | Send the player back to their original position              |
| 💊 **Heal**         | Fully restore the player's health                            |
| 💉 **Revive**       | Revive the player                                            |
| 💀 **Kill**         | Kill the player                                              |
| 🧊 **Freeze**       | Freeze or unfreeze the player in place                       |
| _(+ custom)_        | Any additional action configured by the server administrator |

> 🔧 All quick action buttons are configurable — administrators can add, remove, or modify them freely in the resource configuration files, including the label, the associated action, and the required permission level.

<figure><img src="../../../../.gitbook/assets/image (7) (1).png" alt=""><figcaption></figcaption></figure>

***

## Sanctions

The player profile also includes a detailed view of their **sanction history** (warns, kicks, bans). Administrators can apply new sanctions directly from this in-game panel, using the same options available on the web dashboard.
