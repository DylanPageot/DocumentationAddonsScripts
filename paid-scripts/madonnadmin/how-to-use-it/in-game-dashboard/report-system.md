# Report System

The in-game report system allows players to quickly contact the staff team directly from the game, without leaving their session. Staff members are instantly notified and can manage reports through the in-game administration panel.

***

## 📋 How to Submit a Report

Any player can open the report interface at any time by using the following command:

```
/report
```

Once the command is executed, the report window opens and a **screenshot of the player's current view is automatically captured** and attached to the report. This allows staff members to immediately visualize the context of the issue.

***

## 📝 Report Types

Players can choose between two types of reports depending on their situation:

### ⚡ Quick Reports

Quick reports are **pre-configured short messages** defined by the server administrators in the configuration files. They allow players to send a report in just one click, without typing anything.

> Quick reports are fully customizable — server administrators can add, edit, or remove them freely in the config.

### ✍️ Custom Reports

Custom reports allow players to **type a detailed message** to describe their issue precisely. This is the recommended option for complex situations requiring context.

***

## 📬 What Happens After Submitting?

Once a report is submitted:

* ✅ The report window closes and a **notification appears in the top-left corner** of the screen
* 🔔 Staff members are **notified in-game** and can see the new report in the administration panel
* 💬 The player will be **updated in real time** through the top-left notification area whenever:
  * Their report is **taken in charge** by a staff member
  * A staff member **sends a message** in response

***

## 💬 Communication with Staff

The report system includes a **built-in messaging system** between the player and the staff member handling the report. Both parties can exchange messages directly within the report interface, without needing to use any external tool.

***

## 📊 Report Status

Each report goes through the following status lifecycle:

| Status             | Description                                                                |
| ------------------ | -------------------------------------------------------------------------- |
| 🟡 **Pending**     | The report has been submitted and is waiting for a staff member to take it |
| 🔵 **In Progress** | A staff member has taken charge of the report and is handling it           |
| 🟢 **Closed**      | The report has been resolved and closed by the staff                       |

Players are notified at each status change via the **top-left notification area**.

***

## 🛠️ Staff Side

Staff members receive a **real-time in-game notification** when a new report is submitted. They can then:

* View the report details including the **automatic screenshot**
* Read the player's message
* **Change the report status** (Pending → In Progress → Closed)
* **Reply directly** to the player through the messaging system
* Manage all active reports from the **in-game administration panel**

### ⚡ Quick Action Buttons

When handling a report, staff members have access to **configurable quick action buttons** that allow them to perform common in-game actions on the reported player directly from the report panel, without needing to use separate commands.

Default available actions include:

| Button        | Description                          |
| ------------- | ------------------------------------ |
| 💊 **Heal**   | Fully restores the player's health   |
| 🔄 **Revive** | Revives an incapacitated player      |
| ⛽ **Refuel**  | Refuels the player's current vehicle |

> 🔧 **These buttons are fully configurable** — server administrators can add, edit, or remove action buttons in the resource configuration files. Any custom server-side action can be wired up as a quick action button.

***

> 💡 **Tip for players:** Always use a **custom report** if your issue requires explanation. The automatic screenshot will help staff understand your situation immediately.

***

_MadonneStudio ·_ [_Discord_](https://discord.gg/madonnestudio) _·_ [_Website_](https://madonnestudio.com/)
