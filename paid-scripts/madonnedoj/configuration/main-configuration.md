---
cover: ../.gitbook/assets/banner.png
coverY: 0
---

# Main Configuration

The main configuration section contains the general settings that affect the entire script's behavior.

## Basic Options

### Opening Command

```lua
OpenTabletCmd = "tablet"
```

This is the command players will use to open the tablet interface.

| Property        | Type     | Default    | Description                              |
| --------------- | -------- | ---------- | ---------------------------------------- |
| `OpenTabletCmd` | `string` | `"tablet"` | Command to open the tablet (without `/`) |

**Example:**

```lua
OpenTabletCmd = "doj" -- Players will use /doj
```

### Debug Mode

```lua
DebugMode = true
```

Enable or disable debug information in the console.

| Property    | Type      | Default | Description                          |
| ----------- | --------- | ------- | ------------------------------------ |
| `DebugMode` | `boolean` | `false` | Display debug information in console |

{% hint style="warning" %}
**Important:** Set `DebugMode = false` in production to avoid console spam.
{% endhint %}

**When to use Debug Mode:**

* ✅ During initial setup
* ✅ When troubleshooting issues
* ✅ When testing new configurations
* ❌ In production (regular use)

### User Interface Language

```lua
LocaleUi = "fr"
```

Set the default language for the user interface.

| Property   | Type     | Default | Options                   | Description                                       |
| ---------- | -------- | ------- | ------------------------- | ------------------------------------------------- |
| `LocaleUi` | `string` | `"fr"`  | `"fr"`, `"en"`, or custom | UI language (must match a file in `/ui/locales/`) |

**Available languages:**

* 🇫🇷 `"fr"` - French
* 🇬🇧 `"en"` - English
* 🌍 Custom - [Add your own language](adding-a-new-language.md)

## Text Messages

Customize the messages displayed to players:

```lua
Strings = {
  no_permission = "You are not authorized to use this.",
}
```

| Key             | Default Value                           | Description                                                              |
| --------------- | --------------------------------------- | ------------------------------------------------------------------------ |
| `no_permission` | `"You are not authorized to use this."` | Message shown when a player tries to access something without permission |

You can add more custom messages here and reference them throughout your script.

## Webhooks Configuration

Configure Discord webhooks for notifications:

```lua
Webhooks = {
  WarrantView = "https://discord.com/api/webhooks/YOUR_WEBHOOK_URL_HERE"
}
```

| Property      | Type     | Description                                   |
| ------------- | -------- | --------------------------------------------- |
| `WarrantView` | `string` | Discord webhook URL for warrant notifications |

**How to get a Discord webhook:**

1. Go to your Discord server
2. Select a channel → Edit Channel
3. Integrations → Webhooks → New Webhook
4. Copy the webhook URL
5. Paste it in the configuration

**What gets sent:**

* Warrant creation notifications
* Warrant issuance alerts
* Warrant details (suspect, type, issuing officer)

{% hint style="info" %}
**Optional:** You can leave the webhook empty if you don't want Discord notifications.
{% endhint %}

## Example Complete Configuration

Here's a complete example of the main configuration:

```lua
CONFIG_MADONNE_DOJ = {
  -- Basic Settings
  OpenTabletCmd = "tablet",
  DebugMode = false,
  LocaleUi = "en",
  
  -- Messages
  Strings = {
    no_permission = "You are not authorized to use this.",
  },
  
  -- Services will be configured in the next section
  Services = {
    -- See Services Configuration
  },
  
  -- Discord Integration
  Webhooks = {
    WarrantView = "https://discord.com/api/webhooks/1234567890/abcdefgh"
  }
}
```

## Next Steps

Now that you've configured the main settings, continue with:

* [Services Configuration](services-configuration.md) - Set up your police and justice departments
* [Permissions System](permissions-system.md) - Configure who can do what

***

Need help? Visit our [Support page](../support.md).
