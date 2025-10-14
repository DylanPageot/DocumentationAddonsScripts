---
cover: .gitbook/assets/banner.png
coverY: 0
---

# Installation

This guide will walk you through the installation process of **Madonne DOJ** on your FiveM server.

## Prerequisites

Before installing Madonne DOJ, make sure you have:

- ✅ A **FiveM Server** up and running
- ✅ A **MySQL Database** configured
- ✅ **ESX or QBCore Framework** installed (depending on your server configuration)
- ✅ Basic knowledge of FiveM server administration

## Installation Steps

Follow these steps to install Madonne DOJ on your server:

### Step 1: Download the Resource

Download the `mg-dojscript` resource and place it in your server's `resources` folder.

```
resources/
  └── mg-dojscript/
```

### Step 2: Import the Database

Execute the SQL file to create the necessary database tables:

```sql
-- Execute the db.sql file in your MySQL database
```

You can import it using:
- **phpMyAdmin**: Import the `db.sql` file
- **MySQL Command Line**: 
  ```bash
  mysql -u username -p database_name < db.sql
  ```
- **HeidiSQL** or any other database management tool

### Step 3: Configure the Script

Open the `config.lua` file and configure it according to your server's needs.

At minimum, you should configure:

```lua
CONFIG_MADONNE_DOJ = {
  OpenTabletCmd = "tablet", -- Command to open the tablet
  DebugMode = false, -- Set to true only for debugging
  LocaleUi = "en", -- "fr" or "en"
  
  Services = {
    -- Configure your police and justice services here
  },
  
  Webhooks = {
    WarrantView = "YOUR_DISCORD_WEBHOOK_URL_HERE"
  }
}
```

For detailed configuration options, see the [Configuration Guide](configuration/README.md).

### Step 4: Add to Server Configuration

Add the resource to your `server.cfg` file:

```cfg
ensure mg-dojscript
```

Make sure it's placed **after** your framework (ESX/QBCore) in the load order.

**Example:**
```cfg
ensure es_extended
ensure oxmysql
ensure mg-dojscript
```

### Step 5: Restart Your Server

Restart your FiveM server to load the resource:

```bash
restart mg-dojscript
```

Or restart the entire server if you prefer.

## Verification

To verify the installation was successful:

1. **Check the server console** for any errors
2. **Join your server** as a player
3. **Type the command** `/tablet` (or the command you configured)
4. The tablet interface should open successfully

## Troubleshooting

### The tablet won't open

- ✅ Check that you have the necessary permissions in your job/service
- ✅ Verify the command in `config.lua` matches what you're typing
- ✅ Check the server console for errors

### Database errors

- ✅ Ensure `db.sql` was imported correctly
- ✅ Check your database credentials
- ✅ Verify all tables were created

### Configuration errors

- ✅ Make sure your `config.lua` syntax is correct
- ✅ Verify all required fields are filled
- ✅ Enable `DebugMode = true` to see detailed logs

## Next Steps

Now that Madonne DOJ is installed, you should:

1. **[Configure your services](configuration/services-configuration.md)** - Set up your police and justice departments
2. **[Configure permissions](configuration/permissions-system.md)** - Define who can do what
3. **[Learn how to use it](usage.md)** - Understand the tablet interface
4. **[Set up language](internationalization/README.md)** - Configure your preferred language

---

Need help? Check our [Support page](support.md) or join our [Discord](https://discord.gg/madonne).
