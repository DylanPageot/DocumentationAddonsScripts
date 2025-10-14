---
cover: ../.gitbook/assets/banner.png
coverY: 0
---

# Services Configuration

The Services section allows you to configure all police and justice services available on your server. Each service can have its own permissions and access levels.

## Service Structure

Each service in the configuration follows this structure:

```lua
{
  name = "LSPD",
  fullName = "Los Santos Police Department",
  permissions = {
    user = 371,
    administrator = 495,
  },
  isJustice = false
}
```

### Properties

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | `string` | ✅ Yes | **Unique** short name/code for the service |
| `fullName` | `string` | ✅ Yes | Full display name of the service |
| `permissions.user` | `number` | ✅ Yes | Permission value for regular users |
| `permissions.administrator` | `number` | ✅ Yes | Permission value for administrators |
| `isJustice` | `boolean` | ✅ Yes | Whether this is a judicial service |

{% hint style="danger" %}
**Important:** The `name` property must be **unique** across all services. It's used as the service identifier throughout the system.
{% endhint %}

## Police Services

Police services are standard law enforcement agencies. They have configurable permissions based on roles.

### Example: Police Department

```lua
{
  name = "LSPD", -- MUST BE UNIQUE
  fullName = "Los Santos Police Department",
  permissions = {
    user = 19,        -- Basic officer permissions
    administrator = 495, -- Supervisor/Chief permissions
  },
  isJustice = false
}
```

### Common Police Services

<details>
<summary><strong>Los Santos Police Department (LSPD)</strong></summary>

```lua
{
  name = "LSPD",
  fullName = "Los Santos Police Department",
  permissions = {
    user = 371, 
    administrator = 495,
  },
  isJustice = false
}
```

</details>

<details>
<summary><strong>Los Santos Sheriff's Department (LSSD)</strong></summary>

```lua
{
  name = "LSSD",
  fullName = "Los Santos Sheriff's Department",
  permissions = {
    user = 371,
    administrator = 495,
  },
  isJustice = false
}
```

</details>

<details>
<summary><strong>San Andreas Highway Patrol (SAHP)</strong></summary>

```lua
{
  name = "SAHP",
  fullName = "San Andreas Highway Patrol",
  permissions = {
    user = 371,
    administrator = 495,
  },
  isJustice = false
}
```

</details>

<details>
<summary><strong>Federal Investigation Bureau (FIB)</strong></summary>

```lua
{
  name = "FIB",
  fullName = "Federal Investigation Bureau",
  permissions = {
    user = 371,
    administrator = 495,
  },
  isJustice = false
}
```

</details>

## Justice Services

Justice services (`isJustice = true`) have special properties and automatically receive **all permissions**.

### Example: Department of Justice

```lua
{
  name = "DOJ",
  fullName = "Department of Justice",
  permissions = { -- WILL BE IGNORED
    user = 0,
    administrator = 0,
  },
  isJustice = true -- Grants ALL permissions automatically
}
```

### What Justice Services Can Do

Services with `isJustice = true` have unlimited access:

- ✅ **Access all folders** - View any investigation regardless of service
- ✅ **View all documents** - Read all case files across services
- ✅ **Issue warrants** - Create and sign arrest/search warrants
- ✅ **Sign warrants** - Approve warrants created by police
- ✅ **Manage all records** - Edit criminal records
- ✅ **Override permissions** - Bypass service restrictions

{% hint style="info" %}
**Note:** The `permissions` values are ignored when `isJustice = true`. You can set them to 0 or any value.
{% endhint %}

## Complete Configuration Example

Here's a complete example with multiple services:

```lua
Services = {
  -- Police Services
  {
    name = "LSPD",
    fullName = "Los Santos Police Department",
    permissions = {
      user = 371,
      administrator = 495,
    },
    isJustice = false
  },
  {
    name = "LSSD",
    fullName = "Los Santos Sheriff's Department",
    permissions = {
      user = 371,
      administrator = 495,
    },
    isJustice = false
  },
  {
    name = "SAHP",
    fullName = "San Andreas Highway Patrol",
    permissions = {
      user = 371,
      administrator = 495,
    },
    isJustice = false
  },
  {
    name = "FIB",
    fullName = "Federal Investigation Bureau",
    permissions = {
      user = 371,
      administrator = 495,
    },
    isJustice = false
  },
  
  -- Justice Services
  {
    name = "DOJ",
    fullName = "Department of Justice",
    permissions = {
      user = 0,
      administrator = 0,
    },
    isJustice = true
  },
}
```

## Understanding Permission Values

The numbers in `permissions.user` and `permissions.administrator` are calculated using a bitmask system.

**Common permission values:**
- `19` - Basic officer (folders, documents, examinations)
- `87` - Detective (+ warrants, records)
- `371` - Sergeant (+ requests, services)
- `495` - Chief (all except issuing warrants)
- `511` - All permissions

For a detailed explanation of how to calculate these values, see:
* [Permissions System](permissions-system.md)

## Best Practices

✅ **Do:**
- Use clear, recognizable service codes (`LSPD`, `SAHP`, etc.)
- Set appropriate permissions for each role level
- Have at least one justice service for warrant management
- Keep service names consistent with your server's departments

❌ **Don't:**
- Use duplicate service names
- Give `isJustice = true` to police services
- Use special characters in the `name` field
- Change service names after data has been created

## Adding a New Service

To add a new service to your server:

1. Copy an existing service block
2. Change the `name` to a unique identifier
3. Update the `fullName` to the full service name
4. Set appropriate permission values
5. Set `isJustice` to `true` or `false`
6. Add it to the `Services` table

**Example - Adding a Park Ranger service:**

```lua
{
  name = "PARK",
  fullName = "San Andreas Park Rangers",
  permissions = {
    user = 19,    -- Basic permissions
    administrator = 151, -- More permissions for supervisors
  },
  isJustice = false
}
```

## Next Steps

Now that you understand services, learn about the permissions system:

* [Permissions System](permissions-system.md) - Learn how to calculate permission values

---

Need help? Visit our [Support page](../support.md).
