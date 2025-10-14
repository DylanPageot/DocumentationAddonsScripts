---
cover: ../.gitbook/assets/banner.png
coverY: 0
---

# Adding a New Language

This guide will walk you through adding a new language translation to Madonne DOJ. Whether you want to add Spanish, German, Portuguese, or any other language, follow these steps.

## Overview

Adding a new language involves:
1. Creating translation files
2. Translating all text strings
3. Configuring the script to use your language

**Estimated time:** 1-2 hours (depending on your familiarity with the interface)

## Prerequisites

Before you begin:
- ✅ Familiarity with JSON file format
- ✅ Access to the script files
- ✅ A text editor (VS Code, Notepad++, etc.)
- ✅ Optional: Knowledge of the interface to understand context

## Step-by-Step Guide

### Step 1: Choose Your Language Code

Use the standard ISO 639-1 two-letter language code:

| Language | Code |
|----------|------|
| Spanish | `es` |
| German | `de` |
| Italian | `it` |
| Portuguese | `pt` |
| Dutch | `nl` |
| Polish | `pl` |
| Russian | `ru` |
| Turkish | `tr` |

For this example, we'll add **Spanish** (`es`).

### Step 2: Create Translation Files

You need to create the translation file in the production folder:

```
/ui/locales/es.json
```

**How to create it:**

1. Navigate to `/ui/locales/`
2. Copy the existing `en.json` file
3. Rename the copy to `es.json` (or your language code)

{% hint style="info" %}
**Tip:** Start with `en.json` as it's usually more up-to-date than `fr.json`.
{% endhint %}

### Step 3: Translate the Content

Open your new `es.json` file and translate **only the values**, not the keys.

#### Translation Example

**Before (English):**
```json
{
  "COMPONENTS": {
    "DASHBOARD": {
      "NAME": "Dashboard",
      "MY_DOCUMENTS": "My documents",
      "MY_FOLDERS": "My investigations"
    }
  }
}
```

**After (Spanish):**
```json
{
  "COMPONENTS": {
    "DASHBOARD": {
      "NAME": "Panel de control",
      "MY_DOCUMENTS": "Mis documentos",
      "MY_FOLDERS": "Mis investigaciones"
    }
  }
}
```

{% hint style="danger" %}
**Important:** Never modify the keys (left side), only translate the values (right side)!
{% endhint %}

### Step 4: Full Translation Template

Here's a complete translation structure for reference:

<details>
<summary><strong>Complete JSON Structure (click to expand)</strong></summary>

```json
{
  "COMPONENTS": {
    "CREATOR": {
      "DOCUMENTS": "Documento",
      "EXAMINATIONS": "Interrogatorio",
      "FOLDERS": "Investigación",
      "INSERT_DESCRIPTION": "Insertar descripción...",
      "NAME": "nuevo elemento",
      "RECORDS": "ciudadano",
      "WARRANTS": "Orden judicial"
    },
    "DASHBOARD": {
      "MY_DOCUMENTS": "Mis documentos",
      "MY_EXAMINATIONS": "Mis interrogatorios",
      "MY_FOLDERS": "Mis investigaciones",
      "NAME": "Panel de control"
    },
    "DOCUMENTS": {
      "DATE": "Fecha",
      "DESCRIPTION": "Descripción",
      "EMPTY": "No hay documentos",
      "EMPTY_DESCRIPTION": "Sin descripción",
      "FOLDER": "Invest.",
      "IN_CHARGE": "Oficiales a cargo",
      "NAME": "Documentos",
      "TITLE": "Nombre"
    },
    "EXAMINATIONS": {
      "DATE": "Fecha",
      "DESCRIPTION": "Descripción",
      "EMPTY": "No hay interrogatorios",
      "EMPTY_DESCRIPTION": "Sin descripción",
      "FOLDER": "Invest.",
      "IN_CHARGE": "Oficiales a cargo",
      "NAME": "Interrogatorios",
      "TITLE": "Nombre"
    },
    "FOLDERS": {
      "DATE": "Fecha",
      "DESCRIPTION": "Descripción",
      "EMPTY": "No hay investigaciones",
      "EMPTY_DESCRIPTION": "Sin descripción",
      "IN_CHARGE": "Oficiales a cargo",
      "IN_CHARGE_SERVICES": "Servicios a cargo",
      "NAME": "Investigaciones",
      "SEARCH": {
        "NOT_FOUND": "¡No se encontraron resultados!",
        "PLACEHOLDER": "Buscar investigaciones..."
      },
      "TITLE": "Título"
    },
    "WARRANTS": {
      "DATE": "Fecha",
      "NAME": "Órdenes judiciales",
      "STATUS": "Estado",
      "TITLE": "Título",
      "TYPE": "Tipo"
    },
    "RECORDS": {
      "NAME": "Antecedentes",
      "SEARCH": "Buscar ciudadano..."
    },
    "VIOLATIONS": {
      "NAME": "Infracciones",
      "CATEGORY": "Categoría",
      "FINE": "Multa",
      "JAIL_TIME": "Tiempo de prisión"
    },
    "SERVICES": {
      "NAME": "Servicios",
      "MEMBERS": "Miembros",
      "PENDING": "Pendientes"
    }
  },
  "GENERIC": {
    "SAVE": "Guardar",
    "CANCEL": "Cancelar",
    "DELETE": "Eliminar",
    "EDIT": "Editar",
    "CREATE": "Crear",
    "SEARCH": "Buscar...",
    "LOADING": "Cargando...",
    "UNKNOWN_DATE": "Fecha desconocida",
    "CONFIRM": "Confirmar",
    "CLOSE": "Cerrar"
  },
  "DATE_FORMAT": "dd/MM/yyyy"
}
```

</details>

### Step 5: Configure Date Format

The `DATE_FORMAT` key controls how dates are displayed. Use the format that's common in your region:

| Region | Format | Example |
|--------|--------|---------|
| Europe | `dd/MM/yyyy` | 25/12/2024 |
| USA | `MM/dd/yyyy` | 12/25/2024 |
| ISO | `yyyy-MM-dd` | 2024-12-25 |

**Spanish example:**
```json
{
  "DATE_FORMAT": "dd/MM/yyyy"
}
```

### Step 6: Configure in config.lua

Update your `config.lua` to use the new language:

```lua
CONFIG_MADONNE_DOJ = {
  LocaleUi = "es", -- Your new language code
  -- ... rest of config
}
```

### Step 7: Test Your Translation

1. **Restart the script:**
   ```
   restart mg-dojscript
   ```

2. **Open the tablet:**
   ```
   /tablet
   ```

3. **Check all sections:**
   - Dashboard
   - Investigations
   - Documents
   - Warrants
   - Examinations
   - Records
   - Violations
   - Services

4. **Look for:**
   - Missing translations (English text appearing)
   - Truncated text (too long for buttons)
   - Special characters not displaying correctly
   - Context issues (wrong meaning)

## Advanced: Adding Date Locale Support

For proper date formatting with month names, you may need to add date-fns locale support.

### Step 8: Add Date-fns Locale (Optional)

If you're building from source, edit `/vue/src/utils/functions.js`:

```javascript
import { fr, enUS, es } from 'date-fns/locale'

export const getFormatedDate = (timestamp) => {
  const locales = {
    fr,
    en: enUS,
    es // Add your locale here
  };
  // ... rest of function
}
```

Then rebuild the Vue project:
```bash
cd vue
npm run build
```

{% hint style="warning" %}
**Note:** This step requires Node.js and npm installed. Skip if you're not building from source.
{% endhint %}

## Translation Checklist

Use this checklist to ensure complete translation:

- [ ] All `COMPONENTS.*` sections translated
- [ ] All `GENERIC.*` actions translated
- [ ] `DATE_FORMAT` set appropriately
- [ ] Special characters display correctly
- [ ] Text fits in UI elements (not truncated)
- [ ] Context is correct (meanings are accurate)
- [ ] Empty state messages translated
- [ ] Error messages translated
- [ ] Tested all interface sections
- [ ] Config.lua updated with language code

## Common Translation Keys

Here are the most important keys to translate:

### User Actions
```json
{
  "GENERIC": {
    "SAVE": "...",
    "CANCEL": "...",
    "DELETE": "...",
    "EDIT": "...",
    "CREATE": "...",
    "CONFIRM": "..."
  }
}
```

### Section Names
```json
{
  "COMPONENTS": {
    "DASHBOARD": { "NAME": "..." },
    "FOLDERS": { "NAME": "..." },
    "DOCUMENTS": { "NAME": "..." },
    "WARRANTS": { "NAME": "..." },
    "EXAMINATIONS": { "NAME": "..." },
    "RECORDS": { "NAME": "..." },
    "VIOLATIONS": { "NAME": "..." },
    "SERVICES": { "NAME": "..." }
  }
}
```

### Empty States
```json
{
  "COMPONENTS": {
    "FOLDERS": { "EMPTY": "..." },
    "DOCUMENTS": { "EMPTY": "..." },
    "EXAMINATIONS": { "EMPTY": "..." }
  }
}
```

## Tips for Quality Translation

### Context Matters

Some words have different meanings in different contexts. View the interface to understand:

- Is "Record" a verb (to record) or noun (a record)?
- Is "File" a document or an action (to file)?
- Is "Warrant" singular or can it be plural?

### Keep It Concise

UI translations should be:
- ✅ Short and clear
- ✅ Easy to understand
- ✅ Consistent in terminology
- ❌ Not overly formal (unless appropriate)
- ❌ Not too long for buttons

### Test on Different Screen Sizes

Some languages are more verbose than others:
- German translations are typically 30% longer than English
- Spanish translations are typically 20-25% longer
- Make sure text doesn't overflow on smaller screens

## Sharing Your Translation

If you've created a translation for a new language:

1. **Test it thoroughly**
2. **Join our Discord** - [https://discord.gg/madonne](https://discord.gg/madonne)
3. **Share your translation** - We can include it in future releases!
4. **Get credited** - Your name in the documentation

## Troubleshooting

### Text appears in English instead of my language

- ✅ Check the file name matches your `LocaleUi` setting
- ✅ Verify the JSON syntax is valid (no missing commas, brackets)
- ✅ Ensure the file is in the correct folder (`/ui/locales/`)
- ✅ Restart the script

### Special characters don't display correctly

- ✅ Save the file with UTF-8 encoding
- ✅ Don't use HTML entities (use actual characters)
- ✅ Test with various special characters (é, ñ, ü, etc.)

### JSON syntax errors

- ✅ Use a JSON validator (like jsonlint.com)
- ✅ Check for missing commas between items
- ✅ Ensure all quotes are properly closed
- ✅ Watch for trailing commas (not allowed in JSON)

### Text is cut off in the UI

- ✅ Shorten the translation
- ✅ Use abbreviations where appropriate
- ✅ Check on different screen resolutions

## Example: Complete Spanish Translation

Here's a real working example for Spanish:

```json
{
  "COMPONENTS": {
    "CREATOR": {
      "DOCUMENTS": "Documento",
      "EXAMINATIONS": "Interrogatorio",
      "FOLDERS": "Investigación",
      "INSERT_DESCRIPTION": "Insertar descripción...",
      "NAME": "nuevo elemento",
      "RECORDS": "ciudadano",
      "WARRANTS": "Orden"
    },
    "DASHBOARD": {
      "MY_DOCUMENTS": "Mis documentos",
      "MY_EXAMINATIONS": "Mis interrogatorios",
      "MY_FOLDERS": "Mis investigaciones",
      "NAME": "Panel"
    }
  },
  "GENERIC": {
    "SAVE": "Guardar",
    "CANCEL": "Cancelar",
    "DELETE": "Eliminar",
    "EDIT": "Editar",
    "SEARCH": "Buscar..."
  },
  "DATE_FORMAT": "dd/MM/yyyy"
}
```

## Next Steps

After adding your language:

* [Configuration](../configuration/README.md) - Set up your server
* [Usage Guide](../usage.md) - Learn the interface
* [Support](../support.md) - Get help if needed

---

Created a translation? Share it with the community on our [Discord](https://discord.gg/madonne)!
