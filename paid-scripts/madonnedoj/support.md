---
cover: .gitbook/assets/banner.png
coverY: 0
---

# Need Help?

Having trouble with Madonne DOJ? We're here to help! This page provides various support resources and troubleshooting guidance.

## Before Requesting Support

Before reaching out for help, please try these steps:

### 1. Check the Documentation

* ✅ Read relevant documentation sections
* ✅ Search for your specific issue
* ✅ Review configuration examples

### 2. Enable Debug Mode

Enable debug mode to see detailed error messages:

```lua
CONFIG_MADONNE_DOJ = {
  DebugMode = true, -- Enable this
}
```

Then restart the script:

```
restart MS_MaodonneDOJ
```

### 3. Check Server Console

Press **F8** in-game to open the console and look for:

* ❌ Red error messages
* ⚠️ Yellow warnings
* 🔍 Debug information (if enabled)

### 4. Reproduce the Issue

Try to reproduce the problem:

1. Note the exact steps that cause the issue
2. Check if it happens every time
3. Test with different users/roles
4. Document what you were trying to do

***

## Common Issues

### Installation Issues

<details>

<summary><strong>Script won't start / Database errors</strong></summary>

**Symptoms:**

* Script fails to load
* SQL errors in console
* Missing tables

**Solutions:**

1. ✅ Verify `db.sql` was imported correctly
2. ✅ Check database credentials in your framework
3. ✅ Ensure all tables were created
4. ✅ Check for table name conflicts

</details>

<details>

<summary><strong>Tablet command doesn't work</strong></summary>

**Symptoms:**

* `/tablet` command doesn't respond
* No interface opens

**Solutions:**

1. ✅ Verify command in `config.lua`
2. ✅ Check if player is assigned to a service
3. ✅ Look for errors in console (F8)
4. ✅ Ensure script is started after framework

</details>

### Configuration Issues

<details>

<summary><strong>Permissions not working correctly</strong></summary>

**Symptoms:**

* Users have wrong permissions
* Sections not visible
* Can't perform actions

**Solutions:**

1. ✅ Recalculate permission values
2. ✅ Verify service configuration
3. ✅ Check role assignments
4. ✅ Review [Permissions System](configuration/permissions-system.md)

</details>

<details>

<summary><strong>Language not changing</strong></summary>

**Symptoms:**

* UI still in wrong language
* Translations not appearing

**Solutions:**

1. ✅ Check `LocaleUi` value in `config.lua`
2. ✅ Verify language file exists in `/ui/locales/`
3. ✅ Ensure JSON syntax is valid
4. ✅ Restart the script
5. ✅ Clear browser cache (Ctrl+F5)

</details>

### Usage Issues

<details>

<summary><strong>Can't create investigations/documents</strong></summary>

**Symptoms:**

* Create button not visible
* Nothing happens when clicking create
* Save fails

**Solutions:**

1. ✅ Check your permissions
2. ✅ Ensure you're assigned to a service
3. ✅ Fill all required fields
4. ✅ Check console for errors

</details>

<details>

<summary><strong>Warrants not being issued</strong></summary>

**Symptoms:**

* Can't sign warrants
* Issue button not available

**Solutions:**

1. ✅ Only justice services can issue warrants
2. ✅ Verify `isJustice = true` in config
3. ✅ Check if user has `ISSUE_WARRANTS` permission (or is justice)
4. ✅ Ensure warrant is properly filled out

</details>

<details>

<summary><strong>Discord webhook not working</strong></summary>

**Symptoms:**

* No notifications in Discord
* Webhook errors in console

**Solutions:**

1. ✅ Verify webhook URL is correct
2. ✅ Check Discord server settings
3. ✅ Ensure webhook wasn't deleted
4. ✅ Test with a simple message
5. ✅ Check firewall settings

</details>

### Performance Issues

<details>

<summary><strong>Tablet is slow/laggy</strong></summary>

**Symptoms:**

* Interface loads slowly
* Actions take long time
* Freezing

**Solutions:**

1. ✅ Check server performance
2. ✅ Optimize database queries
3. ✅ Reduce number of records
4. ✅ Check client-side performance
5. ✅ Clear browser cache

</details>

***

## FAQ&#x20;

### Can I modify the script?

Depends on your license. Check your purchase agreement. Generally:

* ✅ You can modify for your server
* ❌ You cannot resell or redistribute
* ❌ You cannot share modifications publicly

### Can I use this with QBCore?

The script may need adaptation for QBCore. Check with support for compatibility.

### How many services can I add?

There's no hard limit, but practical considerations:

* Keep it reasonable (5-15 services typical)
* Too many services can clutter the interface
* Consider database performance with many services

### Can players change language individually?

No, language is server-wide. All players see the same language configured in `config.lua`.

### Do I need to know coding to use this?

Basic knowledge helps for configuration, but:

* Installation is straightforward
* Configuration uses simple Lua
* No coding needed for daily use
* Support available if you get stuck

### How often is the script updated?

Updates are released for:

* Bug fixes (as needed)
* New features (periodically)
* Security patches (immediately)
* Check Discord for announcements

***

**Thank you for using Madonne DOJ!**

We're committed to providing the best law enforcement management system for FiveM.

_Developed by M\_g for MadonneStudio © 2025 - All rights reserved_
