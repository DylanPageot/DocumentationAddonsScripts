---
cover: ../.gitbook/assets/banner.png
coverY: 0
---

# Permissions System

The Madonne DOJ permissions system uses **bitmasks** (bit masks) for efficient and flexible access rights management. This advanced system allows you to combine multiple permissions into a single number.

## Understanding Bitmasks

Bitmasks are a programming technique where each permission is represented by a single bit (power of 2). This allows multiple permissions to be combined using binary operations.

### Why Use Bitmasks?

✅ **Efficient** - Store multiple permissions in one number\
✅ **Fast** - Quick permission checks using bitwise operations\
✅ **Flexible** - Easy to add or remove specific permissions\
✅ **Compact** - Saves database space

## Available Permissions

Here are all available permissions in Madonne DOJ:

```javascript
const PERMISSIONS = {
  MANAGE_FOLDERS: 1 << 0,      // = 1    (Bit 0)
  MANAGE_DOCUMENTS: 1 << 1,    // = 2    (Bit 1)
  MANAGE_WARRANTS: 1 << 2,     // = 4    (Bit 2)
  ISSUE_WARRANTS: 1 << 3,      // = 8    (Bit 3)
  MANAGE_EXAMINATIONS: 1 << 4, // = 16   (Bit 4)
  MANAGE_REQUESTS: 1 << 5,     // = 32   (Bit 5)
  MANAGE_RECORDS: 1 << 6,      // = 64   (Bit 6)
  MANAGE_SERVICES: 1 << 7,     // = 128  (Bit 7)
  MANAGE_VIOLATIONS: 1 << 8,   // = 256  (Bit 8)
}
```

### Permission Details

| Permission            | Value | Bit | Description                                |
| --------------------- | ----- | --- | ------------------------------------------ |
| `MANAGE_FOLDERS`      | 1     | 0   | Create and manage investigation folders    |
| `MANAGE_DOCUMENTS`    | 2     | 1   | Create and modify documents                |
| `MANAGE_WARRANTS`     | 4     | 2   | Create and modify warrants                 |
| `ISSUE_WARRANTS`      | 8     | 3   | Issue/sign warrants (reserved for justice) |
| `MANAGE_EXAMINATIONS` | 16    | 4   | Manage examinations/interrogations         |
| `MANAGE_REQUESTS`     | 32    | 5   | Manage requests                            |
| `MANAGE_RECORDS`      | 64    | 6   | Manage criminal records                    |
| `MANAGE_SERVICES`     | 128   | 7   | Manage services and staff                  |
| `MANAGE_VIOLATIONS`   | 256   | 8   | Manage violations catalog                  |

{% hint style="warning" %}
**Reserved Permission:** `ISSUE_WARRANTS` (8) should only be given to justice services. Police can create warrants, but only judges can issue/sign them.
{% endhint %}

## How to Calculate Permission Codes

To create a permission value, you need to **add** the values of all permissions you want to include.

### Method 1: Simple Addition

This is the easiest method - just add the numbers!

#### Example 1: Basic Officer

**Desired Permissions:**

* Create folders (1)
* Create documents (2)
* Conduct examinations (16)

**Calculation:**

```
1 + 2 + 16 = 19
```

**Configuration:**

```lua
permissions = {
  user = 19,
}
```

#### Example 2: Detective

**Desired Permissions:**

* All from basic officer (1 + 2 + 16)
* Create warrants (4)
* Manage records (64)

**Calculation:**

```
1 + 2 + 4 + 16 + 64 = 87
```

**Configuration:**

```lua
permissions = {
  user = 87,
}
```

#### Example 3: Chief/Administrator

**Desired Permissions:**

* Everything except ISSUE\_WARRANTS

**Calculation:**

```
1 + 2 + 4 + 16 + 32 + 64 + 128 + 256 = 503
(Note: We skip 8 for ISSUE_WARRANTS)
```

**Configuration:**

```lua
permissions = {
  administrator = 495, -- All except issue warrants
}
```

{% hint style="info" %}
**Quick tip:** To get all permissions, add them all: 1+2+4+8+16+32+64+128+256 = **511**
{% endhint %}

### Method 2: Binary OR Operator (|)

For developers, you can use the bitwise OR operator:

#### JavaScript/TypeScript Example

```javascript
const userPermissions = 
  PERMISSIONS.MANAGE_FOLDERS |      // 1
  PERMISSIONS.MANAGE_DOCUMENTS |    // 2
  PERMISSIONS.MANAGE_EXAMINATIONS;  // 16

console.log(userPermissions); // Output: 19
```

#### Lua Example

```lua
local userPermissions = bit.bor(
  1,   -- MANAGE_FOLDERS
  2,   -- MANAGE_DOCUMENTS
  16   -- MANAGE_EXAMINATIONS
)
-- Result: 19
```

## Common Permission Configurations

Here are pre-calculated permission values for common roles:

### Basic Roles

<details>

<summary><strong>Cadet/Probationary Officer (Code: 3)</strong></summary>

**Permissions:**

* ✅ Manage folders
* ✅ Manage documents

**Code:** `3`

**Calculation:** `1 + 2 = 3`

```lua
permissions = {
  user = 3,
}
```

</details>

<details>

<summary><strong>Police Officer (Code: 19)</strong></summary>

**Permissions:**

* ✅ Manage folders
* ✅ Manage documents
* ✅ Manage examinations

**Code:** `19`

**Calculation:** `1 + 2 + 16 = 19`

```lua
permissions = {
  user = 19,
}
```

</details>

<details>

<summary><strong>Senior Officer (Code: 23)</strong></summary>

**Permissions:**

* ✅ Manage folders
* ✅ Manage documents
* ✅ Manage warrants
* ✅ Manage examinations

**Code:** `23`

**Calculation:** `1 + 2 + 4 + 16 = 23`

```lua
permissions = {
  user = 23,
}
```

</details>

### Advanced Roles

<details>

<summary><strong>Detective/Investigator (Code: 87)</strong></summary>

**Permissions:**

* ✅ Manage folders
* ✅ Manage documents
* ✅ Manage warrants
* ✅ Manage examinations
* ✅ Manage records

**Code:** `87`

**Calculation:** `1 + 2 + 4 + 16 + 64 = 87`

```lua
permissions = {
  user = 87,
}
```

</details>

<details>

<summary><strong>Sergeant/Corporal (Code: 151)</strong></summary>

**Permissions:**

* ✅ Manage folders
* ✅ Manage documents
* ✅ Manage warrants
* ✅ Manage examinations
* ✅ Manage requests
* ✅ Manage records
* ✅ Manage services

**Code:** `151`

**Calculation:** `1 + 2 + 4 + 16 + 32 + 64 + 128 = 247`\
**Alternate:** `1 + 2 + 4 + 16 + 64 + 128 = 215`

```lua
permissions = {
  user = 151,
}
```

</details>

### Leadership Roles

<details>

<summary><strong>Lieutenant/Captain (Code: 371)</strong></summary>

**Permissions:**

* ✅ Manage folders
* ✅ Manage documents
* ✅ Manage examinations
* ✅ Manage records
* ✅ Manage violations

**Code:** `371`

**Calculation:** `1 + 2 + 16 + 64 + 32 + 256 = 371`

```lua
permissions = {
  user = 371,
}
```

</details>

<details>

<summary><strong>Chief/Commander (Code: 495)</strong></summary>

**Permissions:**

* ✅ Everything except ISSUE\_WARRANTS

**Code:** `495`

**Calculation:** `1 + 2 + 4 + 16 + 32 + 64 + 128 + 256 = 503` (without 8)

```lua
permissions = {
  administrator = 495,
}
```

</details>

### Justice Roles

{% hint style="success" %}
**Justice services** should use `isJustice = true` instead of calculating permissions. This automatically grants all permissions.
{% endhint %}

<details>

<summary><strong>Judge/Prosecutor</strong></summary>

**Configuration:**

```lua
{
  name = "DOJ",
  fullName = "Department of Justice",
  permissions = {
    user = 0,        -- Ignored
    administrator = 0, -- Ignored
  },
  isJustice = true -- Grants ALL permissions automatically
}
```

</details>

## Quick Reference Table

Use this table to quickly find the right permission code:

| Role            | Code  | Included Permissions                          |
| --------------- | ----- | --------------------------------------------- |
| Cadet           | `3`   | FOLDERS + DOCUMENTS                           |
| Officer         | `19`  | FOLDERS + DOCUMENTS + EXAMINATIONS            |
| Senior Officer  | `23`  | FOLDERS + DOCUMENTS + WARRANTS + EXAMINATIONS |
| Detective       | `87`  | Basic + WARRANTS + RECORDS                    |
| Sergeant        | `151` | Detective + REQUESTS + SERVICES               |
| Lieutenant      | `371` | Advanced + VIOLATIONS                         |
| Chief           | `495` | Everything except ISSUE\_WARRANTS             |
| All Permissions | `511` | All 9 permissions                             |

## Permission Calculator

Follow these steps to calculate custom permissions:

### Step 1: List Desired Permissions

```
☑ MANAGE_FOLDERS (1)
☑ MANAGE_DOCUMENTS (2)
☐ MANAGE_WARRANTS (4)
☐ ISSUE_WARRANTS (8)
☑ MANAGE_EXAMINATIONS (16)
☐ MANAGE_REQUESTS (32)
☑ MANAGE_RECORDS (64)
☐ MANAGE_SERVICES (128)
☐ MANAGE_VIOLATIONS (256)
```

### Step 2: Add Selected Values

```
1 + 2 + 16 + 64 = 83
```

### Step 3: Use in Configuration

```lua
permissions = {
  user = 83,
}
```

## Visual Permission Guide

Here's a visual representation of how permissions combine:

```
Bit Position:  8    7    6    5    4    3    2    1    0
Permission:   256  128   64   32   16   8    4    2    1
              VIO  SRV  REC  REQ  EXM  ISS  WAR  DOC  FOL

Example: Officer (19)
Binary:       0    0    0    0    1    0    0    1    1
Decimal:                          16        +    2  + 1  = 19

Example: Chief (495)
Binary:       1    1    1    1    1    0    1    1    1
Decimal:    256+ 128+  64+  32+  16  (no 8)+ 4 +  2 + 1  = 503
```

## Testing Permissions

After configuring permissions, test them:

1. **Log in** as a user with the configured role
2. **Open the tablet** with `/tablet`
3. **Check sections** - You should only see sections you have access to
4. **Try actions** - Attempt to create/edit items
5. **Verify restrictions** - Ensure you can't access unauthorized features

## Troubleshooting

### User has too many permissions

* Check the calculated value - it might be too high
* Verify which permissions are actually needed
* Recalculate without unwanted permissions

### User has too few permissions

* Add the missing permission values
* Ensure `isJustice` is not accidentally set to `false` for judges
* Check that the role is correctly assigned to the user

### Permission calculation is wrong

* Use the calculator method step by step
* Verify you're not including the same permission twice
* Make sure you're adding, not multiplying

## Next Steps

Now that you understand permissions:

* [Services Configuration](services-configuration.md) - Apply permissions to your services
* [Usage Guide](../usage.md) - Learn what each permission allows users to do

***

Need help? Visit our [Support page](../support.md) or use our [Discord](https://discord.gg/madonne) for permission calculation assistance.
