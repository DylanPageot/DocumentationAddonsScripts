# First Launch



Before installing the resource on your server, you need to create and configure your **Madonn'Admin community** on the web platform. This step is required — the resource cannot load without a valid server token linked to an active subscription.

***

## 💳 Payment

When subscribing, it is imperative to **provide a valid email address**. All information relating to your Madonn'Admin account will be sent to this address.

After validating your payment, a confirmation email will be automatically sent by our service from **noreply@madonnadmin.com**. This email contains crucial information such as your credentials, your **community token**, and direct links to the documentation.

> 💡 If you do not receive the email within a few minutes, check your spam or junk mail folder. If you still cannot find it, contact our support on Discord immediately.

Keep this email somewhere safe — you will need it to set up your community.

***

## 👤 Step 1 — Create your account

Once you have received your email, create your Madonn'Admin account at [**madonnadmin.com**](https://madonnadmin.com/). This account is the main entry point to manage your server, your staff, and your community settings.

Once logged in, your account will be **automatically associated with your community**.

***

## 🔑 Step 2 — Retrieve your Community Token

Your **Community Token** is a unique identifier required for various administrative actions. It was included in the email sent by our services and looks like this:

```
x000xx0xx0xxx0xx00xx0xx0xx000xxx
```

It can also be found at any time in your **community settings** on the Madonn'Admin dashboard. Keep it safe and never share it publicly.

***

## ⚙️ Step 3 — Initial setup

Once registered, follow the initial setup steps on the dashboard:

* Configure your **community name** — this is displayed in-game as the prefix in notifications and staff chat messages
* Set your **language** (English, French, or Spanish)
* Set your **timezone** — used for accurate log timestamps

***

## 🖥️ Step 4 — Add your server

In the dashboard, navigate to **Servers** and add a new server. Fill in:

* The **server name**
* The **public IP address** of your FiveM server

> ⚠️ The IP address must match exactly the one your FiveM server is running on. An incorrect IP will prevent the resource from authenticating.

Once created, your **Server Token** will be generated. Copy it — you will need it in `config/cfg_main.lua` (see [📥 Installation](script-installation.md)).

***

## 🎭 Step 5 — Create your staff roles

In **Roles**, create the ranks for your moderation team. For each role you can configure:

* The **role name** and **display color** (shown on nametags and in the staff list)
* The **rank order**
* **Per-permission toggles** — teleportations, spectate, god mode, submarine mode, delete radius, broadcast, and more

> 💡 Rank `-1` is the **super admin** rank and bypasses all permission checks. Rank `0` means the player has no staff access.

***

## 👮 Step 6 — Add staff members

Adding a player as a staff member requires a few steps to ensure a secure and correct association.

**Requirements before adding a staff member:**

* The player must have **connected at least once** to your server. This initial connection allows Madonn'Admin to recognize the player and automatically generate their profile on the platform.
* You must send the player your **Community Token** (see Step 2). The player must enter this token in the settings of their own Madonn'Admin account to link themselves to your community.

**How to finalize the association:**

Once the player has connected and entered the token, go to their **Madonn'Admin profile**. A box will appear under their username, showing the name linked to their account. Click on this box to officially add the player to your community as a staff member.

<figure><img src="../../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

This creates a permanent link between the player and your community. If you later wish to remove this link, click the **trash icon** to delete the association.

***

## 🏷️ Step 7 — Assign a role to a staff member

At this point, the staff member is linked to your community but does not yet have a specific role. To assign one:

* Go to **Team Staffs** → **Manage Staffs** in the dashboard
* Select the **server** on which you want to assign the permissions
* Enter the **username** of the staff member
* Choose the **role** to assign

This ensures each staff member has the appropriate permissions to fulfill their functions while maintaining a clear and structured organization within your team.

<figure><img src="../../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

***

## 📣 Step 8 — Configure broadcasts & announcements _(optional)_

In **Broadcasts**, pre-save server-wide message templates that staff can send with a single click from the in-game dashboard.

In **Announcements**, post staff-facing messages that appear on the admin panel homepage — useful for shift instructions, event reminders, or moderation guidelines.

***

## ✅ You're ready

Your community, server, roles, and staff are now configured. Proceed to the [📥 Installation](script-installation.md) page to set up the resource on your FiveM server.

