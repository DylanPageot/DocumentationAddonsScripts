# Services Configuration

The Services section allows you to configure all police and justice services available on your server. Each service can have its own permissions and access levels.

## Service Structure

Each service in the configuration follows this structure:

```lua
{
  name = "LSPD",
  fullName = "Los Santos Police Department",
  isJustice = false
}
```

### Properties

| Property    | Type      | Required | Description                                |
| ----------- | --------- | -------- | ------------------------------------------ |
| `name`      | `string`  | ✅ Yes    | **Unique** short name/code for the service |
| `fullName`  | `string`  | ✅ Yes    | Full display name of the service           |
| `isJustice` | `boolean` | ✅ Yes    | Whether this is a judicial service         |

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
  isJustice = true
}
```

### What Justice Services Can Do

Services with `isJustice = true` have unlimited access:

* ✅ **Access all folders** - View any investigation regardless of service
* ✅ **View all documents** - Read all case files across services
* ✅ **Issue warrants** - Create and sign arrest/search warrants
* ✅ **Sign warrants** - Approve warrants created by police
* ✅ **Manage all records** - Edit criminal records

## Complete Configuration Example

Here's a complete example with multiple services:

```lua
Services = {
  -- Police Services
  {
    name = "LSPD",
    fullName = "Los Santos Police Department",
    isJustice = false
  },
  {
    name = "LSSD",
    fullName = "Los Santos Sheriff's Department",
    isJustice = false
  },
  {
    name = "SAHP",
    fullName = "San Andreas Highway Patrol",
    isJustice = false
  },
  {
    name = "FIB",
    fullName = "Federal Investigation Bureau",
    isJustice = false
  },
  
  -- Justice Services
  {
    name = "DOJ",
    fullName = "Department of Justice",
    isJustice = true
  },
}
```

## Best Practices

✅ **Do:**

* Use clear, recognizable service codes (`LSPD`, `SAHP`, etc.)
* Have at least one justice service for warrant management
* Keep service names consistent with your server's departments

❌ **Don't:**

* Use duplicate service names
* Give `isJustice = true` to police services
* Use special characters in the `name` field
* Change service names after data has been created

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
  isJustice = false
}
```

***

Need help? Visit our [Support page](../support.md).
