# Reports Configuration

The reports configuration is located at `config/module/cfg_reports.lua`. It controls the player report system — the command players use, the pre-configured quick report types, and how notifications are handled.

***

## ⚙️ General Settings

```lua
REPORTS_CONFIG = {
    ReportsEnabled = true,
    CreateReportCommand = "report",
    TakeScreenshotWhenReportIsCreated = true,
}
```

| Option                              | Type      | Description                                                                                                                         |
| ----------------------------------- | --------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| `ReportsEnabled`                    | `boolean` | Enable or disable the entire report system                                                                                          |
| `CreateReportCommand`               | `string`  | The command players use to open the report interface. Default: `"report"` → `/report`                                               |
| `TakeScreenshotWhenReportIsCreated` | `boolean` | If `true`, a screenshot is automatically captured and attached to the report when it is submitted. **Requires `screenshot-basic`.** |

***

## ⚡ Quick Reports

Quick reports are pre-configured one-click report buttons shown to players when they open the report interface. Players can choose one without typing anything.

```lua
QuickReports = {
    "Bug",
    "Question",
    "Freekill",
    "NoFear",
    "NoPain",
    "Insults",
    "Cheater",
    "Spectate me",
    "New player"
},
```

* You can define **up to 10** quick report types
* Each entry is a string that becomes the report title
* Players can also submit a fully custom report with their own title and description

> 💡 Quick reports and custom reports are both available simultaneously. Players choose between them when they open the report menu.

***

## 🔔 Notifications

Controls which events trigger a notification in-game:

```lua
Notifications = {
    OwnReportCreated = false,
    NewScreenshot    = false,
    NewMessage       = true,
    NewReport        = true,
}
```

| Option             | Type      | Description                                                           |
| ------------------ | --------- | --------------------------------------------------------------------- |
| `OwnReportCreated` | `boolean` | Notify the player when their own report is successfully created       |
| `NewScreenshot`    | `boolean` | Notify the player when a new screenshot is attached to their report   |
| `NewMessage`       | `boolean` | Notify the player when a staff member sends a message in their report |
| `NewReport`        | `boolean` | Notify all active staff members when a new report is submitted        |

***

## 🖼️ Screenshot Configuration

The screenshots taken on report submission are stored via Discord webhook, configured in `config/module/cfg_screenshots.lua`:

```lua
SCREENSHOTS = {
    ScreenshotBasicName = "screenshot-basic",
    DiscordWebhookToSaveScreenshots = "https://discord.com/api/webhooks/...",
}
```

| Option                            | Type     | Description                                                                             |
| --------------------------------- | -------- | --------------------------------------------------------------------------------------- |
| `ScreenshotBasicName`             | `string` | Name of the `screenshot-basic` resource. Do not change unless you renamed the resource. |
| `DiscordWebhookToSaveScreenshots` | `string` | Discord webhook URL where report screenshots are uploaded and stored                    |

> ⚠️ Without a valid webhook, screenshots will fail to save even if `screenshot-basic` is running.

***

## 📊 Report Statistics

All reports are saved to the Madonn'Admin platform and can be reviewed on the **web dashboard** under the **Reports** section. For a full breakdown of available statistics, refer to the 📊 Report Statistics page.

