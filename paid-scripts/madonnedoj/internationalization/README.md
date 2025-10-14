# Internationalization (i18n)

Madonne DOJ supports multiple languages through a comprehensive internationalization system. The interface can be displayed in different languages, and you can easily add your own translations.

## Available Languages

By default, Madonne DOJ comes with:

- 🇫🇷 **French** (`fr.json`) - Fully translated
- 🇬🇧 **English** (`en.json`) - Fully translated

## Language Files

Translation files are organized in two locations:

### Production Files (Compiled)
```
/ui/locales/
  ├── fr.json
  └── en.json
```

These are the compiled translation files used by the script.

### Development Files (Source)
```
/vue/public/locales/
  ├── fr.json
  └── en.json
```

These are the source files used during Vue.js development.

## Setting the Default Language

To change the default language, edit the `config.lua` file:

```lua
CONFIG_MADONNE_DOJ = {
  LocaleUi = "en", -- Change to "fr" for French, or your custom language code
}
```

## Translation File Structure

Each language file follows this JSON structure:

```json
{
  "COMPONENTS": {
    "DASHBOARD": {
      "NAME": "Dashboard",
      "MY_FOLDERS": "My investigations",
      "MY_DOCUMENTS": "My documents",
      "MY_EXAMINATIONS": "My examinations"
    },
    "FOLDERS": {
      "NAME": "Investigations",
      "TITLE": "Title",
      "DATE": "Date",
      "DESCRIPTION": "Description",
      "EMPTY": "No investigations"
    }
  },
  "GENERIC": {
    "SAVE": "Save",
    "CANCEL": "Cancel",
    "DELETE": "Delete",
    "EDIT": "Edit"
  },
  "DATE_FORMAT": "MM/dd/yyyy"
}
```

## Important Translation Keys

Some keys have special meanings:

| Key | Description | Example |
|-----|-------------|---------|
| `DATE_FORMAT` | Format for displaying dates | `"dd/MM/yyyy"` (EU) or `"MM/dd/yyyy"` (US) |
| `GENERIC.*` | Common UI actions | Save, Cancel, Delete, etc. |
| `COMPONENTS.*.NAME` | Section titles | Dashboard, Documents, etc. |
| `COMPONENTS.*.EMPTY` | Empty state messages | "No documents", etc. |

## Adding a New Language

Want to add a new language to Madonne DOJ? Check out our detailed guide:

* [Adding a New Language](adding-a-new-language.md)

## Language Best Practices

✅ **Do:**
- Keep translations concise and clear
- Use consistent terminology across the interface
- Test translations in the actual UI
- Consider text length for button labels

❌ **Don't:**
- Translate technical terms (like variable names)
- Use informal language unless appropriate
- Forget to translate all sections
- Mix multiple languages in one file

## Switching Languages

Users cannot switch languages dynamically. The language is set server-wide in `config.lua`. 

If you want to offer multiple languages:
1. Inform players of the server language
2. Consider creating separate servers for different languages
3. Or modify the script to support per-player language preferences (custom modification)

## Translation Credits

If you create a translation, you can add credits in the file:

```json
{
  "_meta": {
    "language": "Spanish",
    "translator": "Your Name",
    "version": "1.0.0"
  },
  "COMPONENTS": {
    ...
  }
}
```

{% hint style="info" %}
The `_meta` section is optional and won't affect functionality.
{% endhint %}

## Need Help?

- 📖 Read the [Adding a New Language](adding-a-new-language.md) guide
- 💬 Join our [Discord](https://discord.gg/madonne) for translation help
- 📧 Contact us at contact@madonnestudio.com

---

Ready to add a new language? Continue to:
* [Adding a New Language](adding-a-new-language.md)
