# Community Settings

Community Settings is the first section to configure after creating your Madonn'Admin account. It defines the identity of your community and contains the token your server uses to authenticate with the platform.

Access it from the Madonn'Admin dashboard sidebar under **Community Settings**.

<figure><img src="../../../../.gitbook/assets/image (52).png" alt=""><figcaption></figcaption></figure>

***

## 🏷️ Community Name

The community name is displayed in-game as the **prefix** in several places:

* Staff chat messages (`[STAFF CHAT] CommunityName :`)
* Broadcast messages
* Notification messages sent to players
* The loading screen during profile verification

Choose a short, recognizable name for your community.

***

## 🌐 Language

Madonn'Admin supports three languages out of the box:

* 🇬🇧 **English**
* 🇫🇷 **French**
* 🇪🇸 **Spanish**

The selected language applies to all in-game text — nametag labels, sanction messages, log descriptions, ban screen translations, and the admin panel interface.

> 💡 The language is set at the community level and applies to all servers in your community. It can be changed at any time — staff members will see the new language on their next connection.

***

## 🕐 Timezone

The timezone setting controls the timestamp formatting used in **activity logs**. Set it to your local UTC offset to ensure log times match your team's timezone.

Examples:

* `+1` → UTC+1 (Central European Time)
* `0` → UTC
* `-5` → UTC-5 (Eastern Standard Time)

This value is also used by the restart announcement system to correctly calculate when to send warnings before scheduled restarts.

***

## 🔑 Community Token

The **Community Token** is the unique identifier for your community. It is used in two situations:

* **Server authentication** — pasted into `config/cfg_main.lua` as `Server_Token` to link your FiveM server to your community
* **Staff member onboarding** — shared with new staff members so they can link their player profile to your community from their Madonn'Admin account settings

Your token is displayed in the Community Settings page and looks like this:

```
x000xx0xx0xxx0xx00xx0xx0xx000xxx
```

> ⚠️ Keep your Community Token private. Anyone with this token can attempt to link themselves to your community. Never post it publicly.

***

## ⭐ Trust Score Settings

The Trust Score is a numerical value attached to each player's profile that evolves over time based on their behavior and history on your server. It is used by Madonn'Admin to automatically assign **trust flags** that are visible to your staff team.

<figure><img src="../../../../.gitbook/assets/image (53).png" alt=""><figcaption></figcaption></figure>

You can configure the following parameters:

* **Starting score** — The score assigned to a new player on their first connection
* **Score increase rate** — How much the score increases per hour of playtime. The longer a player stays without incidents, the more trusted they become.
* **Penalty weights** — The score impact (positive or negative) of each type of sanction on a player's profile (warns, kicks, bans, commends…)

### 🏅 Flag Thresholds

The following three options configure the thresholds at which **visual flags** are applied to a player's profile:

* **Perfect Player** — After a configurable ratio of hours played per penalty, a player is awarded the _Perfect Player_ flag
* **Negative flags** — After a configurable number of penalties, negative flags such as _Untrusted_ or _Sanction Lover_ are applied

> 💡 These flags are **visual indicators only**. They appear in the admin panel and on player profiles to help staff assess a player at a glance, but they do not automatically restrict or affect gameplay.

***

## 🔁 Accumulation of Sanctions

Madonn'Admin can automatically apply a **temporary ban** when a player accumulates a certain number of warnings on their profile. This allows you to enforce progressive discipline without requiring manual intervention from your staff.

<figure><img src="../../../../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>

You can configure:

* **Number of warnings required** — After this many active warnings, a temporary ban is automatically triggered
* **Ban duration** — The length of the automatic ban applied

> ⚠️ Only **active warnings** are counted. Warnings that have been removed through a successful appeal are not included in the total.

If you wish to effectively disable this feature, set the warning threshold to an unreachable number such as `99` or `999`. There is very little risk of a player ever reaching such a count.

***

## ⚖️ Appeals Management

Players have the ability to submit **appeal requests** to contest sanctions applied to their profile. You can configure the conditions under which a player is eligible to submit an appeal:

* **Duration between two appeals** — The minimum amount of time a player must wait before submitting a new appeal after a previous one
* **Minimum and remaining ban duration** — A ban appeal can only be submitted if the ban meets a minimum total duration and still has a sufficient amount of time remaining
* **Age of a sanction** — For sanctions other than active bans, you can define a maximum age beyond which the sanction can no longer be appealed

<figure><img src="../../../../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

> 💡 Appeals that are accepted by your staff result in the sanction being removed from the player's profile. Accepted appeals are **not counted** in the warning accumulation system
