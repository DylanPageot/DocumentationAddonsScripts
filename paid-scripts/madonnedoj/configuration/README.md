# Configuration Overview

Madonne DOJ offers extensive configuration options to adapt the script to your server's specific needs. This section will guide you through all available configuration options.

## Configuration Files

The main configuration is located in:
```
config.lua
```

This file contains all the settings for:
- Basic options (commands, debug mode, language)
- Services configuration (police departments, justice services)
- Permissions settings
- Webhooks configuration

## Configuration Sections

Our configuration is divided into several main sections:

### 🔧 Main Configuration

General settings that affect the entire script's behavior.

* [Main Configuration](main-configuration.md)

### 🏢 Services Configuration

Configure all your police and justice services, including their names, permissions, and roles.

* [Services Configuration](services-configuration.md)

### 🔐 Permissions System

Understand and configure the advanced bitmask-based permissions system.

* [Permissions System](permissions-system.md)

## Quick Start

For a quick setup, follow these steps:

1. **Set the tablet command** - Choose the command players will use to open the tablet
2. **Configure your language** - Select `"fr"` or `"en"` (or add your own)
3. **Set up your services** - Add your police departments and justice services
4. **Configure permissions** - Define what each role can do
5. **Add Discord webhook** (optional) - For warrant notifications

## Configuration Best Practices

✅ **Do:**
- Test configuration changes in a development environment first
- Keep a backup of your `config.lua` before making major changes
- Use meaningful names for your services
- Document custom permission values for your team

❌ **Don't:**
- Use duplicate service names
- Forget to configure permissions for each service
- Leave debug mode enabled in production
- Share your Discord webhooks publicly

## Need Help?

If you need assistance with configuration:

- 📖 Read the detailed configuration pages in this section
- 💬 Join our [Discord](https://discord.gg/madonne) for support
- 📧 Contact us at contact@madonnestudio.com

---

Let's dive into the specific configuration sections!
