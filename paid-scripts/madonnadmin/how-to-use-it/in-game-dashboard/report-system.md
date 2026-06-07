# Report System

The in-game report system allows players to quickly contact the staff team directly from the game, without leaving their session. Staff members are instantly notified and can manage reports through the in-game administration panel.

***

## How to Submit a Report

Any player can open the report interface at any time by using the following command:

```
/report
```

The report flow works in the following steps:

**1. Type selection** — A first window opens asking the player to choose the type of report (quick report or custom report).

**2. Screenshot** — Once the type is selected, a **screenshot of the player's current view is automatically captured** and attached to the report.

**3. Report content** — The report window then opens, displaying the screenshot alongside the report content.

**4. Floating notification** — When the player **closes the report window**, a **floating notification widget appears on the left side of the screen**, keeping them informed of any updates in real time.

***

## Report Types

Players can choose between two types of reports depending on their situation:

### Quick Reports

Quick reports are **pre-configured short messages** defined by the server administrators in the configuration files. They allow players to send a report in just one click, without typing anything.

> Quick reports are fully customizable — server administrators can add, edit, or remove them freely in the config.

### Custom Reports

Custom reports allow players to **type a detailed message** to describe their issue precisely. This is the recommended option for complex situations requiring context.

***

## What Happens After Submitting?

Once the report is submitted and the window is closed:

* 🔲 A **floating notification widget appears on the left side of the screen**, keeping the player updated without interrupting gameplay
* 🔔 Staff members are **notified in-game** and can see the new report in the administration panel
* 💬 The player will be **updated in real time** through the floating widget whenever:
  * Their report is **taken in charge** by a staff member
  * A staff member **sends a message** in response

***

## Communication with Staff

The report system includes a **built-in messaging system** between the player and the staff member handling the report. Both parties can exchange messages directly within the report interface, without needing to use any external tool.

***

## Report Status

Each report goes through the following status lifecycle:

| Status             | Description                                                                |
| ------------------ | -------------------------------------------------------------------------- |
| 🟡 **New**         | The report has been submitted and is waiting for a staff member to take it |
| 🔵 **In Progress** | A staff member has taken charge of the report and is handling it           |
| 🟢 **Closed**      | The report has been resolved and closed by the staff                       |

Players are notified at each status change via the **floating notification widget** on the left side of the screen.

***

## Staff Side

Staff members receive a **real-time in-game notification** when a new report is submitted. They can then:

* View the report details including the **automatic screenshot**
* Read the player's message
* **Change the report status** (Pending → In Progress → Closed)
* **Reply directly** to the player through the messaging system
* **Execute quick actions** on the reported player directly from the report panel
* Manage all active reports from the **in-game administration panel**

### Quick Action Buttons

Staff members have access to **configurable quick action buttons** directly within the report panel. These allow them to apply common moderation actions on a player in one click, without having to type any command.

The following actions are available by default and can be fully customized in the resource configuration files:

| Button         | Description                                                  |
| -------------- | ------------------------------------------------------------ |
| 🚀 **Goto**    | Teleports the staff member to the reported player            |
| 🔄 **Bring**   | Teleports the reported player to the staff member            |
| ↩️ **Return**  | Sends the reported player back to their original position    |
| 🧊 **Freeze**  | Freezes or unfreezes the reported player in place            |
| 💊 **Heal**    | Fully restores the reported player's health                  |
| 💀 **Kill**    | Kills the reported player                                    |
| 🔧 **Fix VCL** | Repairs the reported player's current vehicle                |
| _(+ custom)_   | Any additional action configured by the server administrator |

> 🔧 **All quick action buttons are configurable** — server administrators can add, remove, or modify them freely in the resource configuration files, including the button label, the associated action, and the required permission level to use them.

***

> 💡 **Tip for players:** Always use a **custom report** if your issue requires explanation. The automatic screenshot will help staff understand your situation immediately
