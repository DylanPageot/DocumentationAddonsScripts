# Manage Permissions

The Manage Permissions section is where you create and configure the **staff roles** for your community. Each role defines a precise set of permissions that determines what a staff member can see and do — both in the in-game admin panel and on the web dashboard.

The maximum number of roles per server depends on your subscription plan:

* 🥉 **Bronze** — up to 5 roles per server
* 🥈 **Silver** — up to 10 roles per server
* 🥇 **Gold** — up to 15 roles per server

***

## 📋 Roles List

<figure><img src="../../../../.gitbook/assets/image (72).png" alt=""><figcaption></figcaption></figure>

Each server has its own roles list, displayed as a summary table. For each role you can see its name, color, and the permissions that have been granted to it.

From this table you can:

* **Reorder roles** — Drag and drop roles to change their hierarchy. The order determines authority levels between staff members: roles higher in the list outrank roles below them.
* **Edit a role** — Modify its name, color, or any of its permissions
* **Delete a role** — Remove it from the server. Staff members assigned to this role will lose their permissions until a new role is assigned.

<figure><img src="../../../../.gitbook/assets/image (73).png" alt=""><figcaption></figcaption></figure>

***

## ➕ Adding a Role

A form at the bottom of the page allows you to create new roles. The same form is used when editing an existing role.

<figure><img src="../../../../.gitbook/assets/image (74).png" alt=""><figcaption></figcaption></figure>

### 📝 Form Fields

**Server** Select the server for which this role is created. Roles are per-server — the same role name can exist on multiple servers with different permission sets.

**Role Name** The display name for this role, shown in:

* The staff list in the in-game admin panel
* Player nametags above staff members
* The web dashboard staff overview

**Color Code** _(hexadecimal)_ The color associated with this role. It is used for the role badge in the dashboard and for the nametag color displayed in-game above the staff member's character.

***

## 🔐 Permissions

Below the basic settings, you will find the full list of permissions available in Madonn'Admin. Simply check the ones you want to grant to the role you are creating.

### Standard Permissions

* **Spectate** — Allows the staff member to spectate players using the in-game spectate system or the `/spectate` command
* **God Mode** — Allows the staff member to enable invincibility while in active moderation mode, from the Settings tab of the admin panel
* **Broadcast** — Allows the staff member to send server-wide broadcast messages from the admin panel, using both free-text and pre-saved templates
* **Teleportations** — Allows the staff member to use Go To, Go To Car, Bring, and Return actions on players
* **Options Tab** — Grants access to the Settings tab in the admin panel. Automatically enabled if God Mode, Submarine, or Mass Delete are granted.

### ⚠️ Special Permissions

Some permissions have additional configuration options that appear when they are checked:

**🔨 Temporary Ban** When this permission is enabled, an additional field appears asking for the **maximum ban duration in days** that this role is allowed to apply. This caps the ban length a staff member of this rank can issue — they will not be able to apply a ban longer than the configured limit.

> 💡 Permanent bans and community bans are separate permissions and are not affected by this cap.

**🤿 Submarine Mode** Allows the staff member to activate their moderation mode while remaining **hidden from the view of other players**. When in Submarine mode, the staff member appears as a regular player on the map and in nametags, allowing them to monitor situations discreetly without alerting rule-breakers.

> 💡 Higher-ranked staff can still see Submarine-mode staff with a specific nametag prefix, configurable in `cfg_blips.lua`.

**🗑️ Massive Delete Radius** When this permission is enabled, an additional field appears to set the **maximum radius in units** within which the staff member can use the mass deletion tools (delete vehicles, delete objects) from the Settings tab of the admin panel.

Setting a radius of `0` effectively disables this tool for the role, while a large value gives the staff member broad deletion capabilities.

<figure><img src="../../../../.gitbook/assets/image (75).png" alt=""><figcaption></figcaption></figure>

***

## 🔄 Updating or Revoking a Role

* To **change** a staff member's role, go to **Team Staffs → Manage Staffs**, select the server, and assign a different role
* To **revoke** all access, delete the staff member's association with your community using the trash icon on their profile
* Permission changes take effect on the player's **next connection** to the server

***

> 💡 Rank `-1` is the **super admin** rank and bypasses all permission checks. Rank `0` means the player has no staff access at all. These special ranks cannot be assigned through the role creation form — they are reserved by the platform.
