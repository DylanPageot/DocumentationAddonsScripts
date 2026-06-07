---
icon: discord
---

# Discord Functionalities

## 💬 Available Commands

Once installed, the bot registers the following slash commands on your Discord server:

### `/infojoueur`

Retrieves information about a specific player from your Madonn'Admin community. The bot returns a detailed embed including:

* FiveM username
* Total playtime
* Join date and last connection date
* License identifiers
* A direct link to their **Madonn'Admin profile**
* A **sanction preview** button
* An **Apply a sanction** button for quick moderation actions directly from Discord

<figure><img src="../../../.gitbook/assets/image (26).png" alt="" width="240"><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (27).png" alt="" width="327"><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (28).png" alt="" width="367"><figcaption></figcaption></figure>

### `/profil`

Displays your own Madonn'Admin profile — your linked player information, rank, and community association.

### `/statut embed`

Sends a **permanent status embed** in the current channel. This embed automatically updates to reflect the live status of your FiveM servers, showing:

* Server name
* Online / Offline status
* Number of connected players
* The F8 connection command (`connect xxx`)
* Last update timestamp and resource version

> 💡 This command is ideal for a dedicated `#server-status` channel. The embed updates automatically — no need to resend it.

<figure><img src="../../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

### `/statut obtenir`

Retrieves the current status of your servers on demand, without posting a permanent embed. Useful for quickly checking server status in any channel.
