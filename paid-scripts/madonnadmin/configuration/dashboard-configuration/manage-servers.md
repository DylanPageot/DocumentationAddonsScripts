# Manage Servers

The Manage Servers section lists all the FiveM servers linked to your Madonn'Admin community. Each server has its own **Server Token** used to authenticate the in-game resource.

The maximum number of servers depends on your subscription plan:

* 🥉 **Bronze** — up to 2 servers
* 🥈 **Silver** — up to 5 servers
* 🥇 **Gold** — up to 10 servers

***

## 📋 Server List

For each server in the list, the following information is displayed:

* **Name** — The name you gave the server when creating it
* **IP Address** — The public IP of the FiveM server. This must be exact for all Madonn'Admin features to work correctly.
* **Status** — Whether the server is currently online or offline
* **Connected players** — The number of players currently on the server
* **Connected staff** — The number of staff members currently online

<figure><img src="../../../../.gitbook/assets/image (70).png" alt=""><figcaption></figcaption></figure>

Each server also has three action buttons:

* 📋 **Copy Token** — Copies the unique Server Token to your clipboard. This token is what you paste into `config/cfg_main.lua` on your FiveM server.
* ✏️ **Edit** — Opens the server settings form to modify its configuration
* 🗑️ **Delete** — Removes the server from your community

***

## ➕ Adding a Server

Click **Add a server** to open the configuration form. The same form is used when editing an existing server.

### 📝 Form Fields

**Server Name** A display name for this server, shown in the dashboard and in statistics.

**Server IP Address** The public IP address of your FiveM server.

> ⚠️ The IP address must be **correct and the server must be running** at the time of registration. Madonn'Admin will attempt to connect to this IP to verify it before saving. An unreachable or incorrect IP will prevent the server from being registered.

**Discord Webhook — Pending Sanctions** An optional Discord webhook URL. When a staff member applies a sanction that requires **validation from a superior** before being applied, a notification is automatically sent to this webhook. The message indicates which staff member submitted the request and which sanction is awaiting approval.

> 💡 This webhook is useful for servers with a multi-tier moderation system where higher-ranked staff must approve certain sanctions before they go through.

**Discord Webhook — Announcements** An optional Discord webhook URL for staff announcements. When an announcement is posted from the Madonn'Admin dashboard, it is automatically forwarded to the specified Discord channel.

By default, no Discord role is pinged when an announcement is sent. To ping a specific role, enter its **Discord role ID** in the field provided below the webhook URL.

> 💡 To get a role ID in Discord, enable **Developer Mode** in Discord Settings → Advanced, then right-click any role in the role list and select **Copy ID**.

<figure><img src="../../../../.gitbook/assets/image (71).png" alt=""><figcaption></figcaption></figure>

***

## 🔑 Retrieving your Server Token

After creating a server, its unique token can be retrieved at any time using the **Copy Token** button on the server's entry in the list.

Paste it into your FiveM resource configuration:

```lua
-- config/cfg_main.lua
Server_Token = "your-server-token-here",
```

> ⚠️ Each server has its own unique token. Never use the same token across multiple servers.

***

## 🗑️ Removing a Server

Click the **Delete** button on a server entry to remove it from your community. This frees up a server slot within your plan's limit.

> Removing a server does not delete its historical data (players, sanctions, logs). All data remains accessible on the dashboard.

