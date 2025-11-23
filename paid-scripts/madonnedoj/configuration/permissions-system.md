---
cover: ../.gitbook/assets/banner.png
coverY: 0
---

# Permission Management System

## Overview

The mg-dojscript permission system allows granular access control for each service. It uses a **bit flags** system to optimize storage and permission checks.

## Accessing the Permissions Page

The permissions management page is accessible via:
- **Route**: `/permissions?uid={serviceId}`
- **Component**: `Permissions.vue`
- **Access Conditions**: Reserved for service chiefs and users authorized to manage services

## Available Permissions List

The system has **10 distinct permissions**:

| Permission | Binary Value | Description |
|------------|--------------|-------------|
| `MANAGE_FOLDERS` | 1 (1 << 0) | Create and edit investigations |
| `MANAGE_DOCUMENTS` | 2 (1 << 1) | Create and edit documents |
| `MANAGE_WARRANTS` | 4 (1 << 2) | Create and edit warrants |
| `ISSUE_WARRANTS` | 8 (1 << 3) | Issue/send warrants (Justice only) |
| `MANAGE_EXAMINATIONS` | 16 (1 << 4) | Create and edit examinations |
| `MANAGE_REQUESTS` | 32 (1 << 5) | Manage requests (currently disabled) |
| `MANAGE_RECORDS` | 64 (1 << 6) | Edit criminal records |
| `MANAGE_SERVICES` | 128 (1 << 7) | Manage membership requests and service settings |
| `MANAGE_VIOLATIONS` | 256 (1 << 8) | Create and edit violations |
| `ARCHIVE_FOLDERS` | 512 (1 << 9) | Archive investigations (Justice only) |

## Technical Implementation

### Data Structure

Each role consists of:
```javascript
{
  name: "CHIEF",          // Role name
  value: 127              // Combined permission value (bit flags)
}
```

### Bit Flags System

Permissions use binary operations to combine multiple rights into a single value:

- **Check**: `(userRole.value & permission) === permission`
- **Enable**: `role.value |= bit`
- **Disable**: `role.value &= ~bit`

**Example**:
- A role with `MANAGE_FOLDERS` (1) + `MANAGE_DOCUMENTS` (2) + `MANAGE_WARRANTS` (4) = **value 7**
- A role with all permissions = **value 1023** (2^10 - 1)

## Management Interface

### Features

#### 1. Adding Roles
- Maximum **6 custom roles** per service
- The `USER` role is permanent and cannot be deleted
- Unique name validation

#### 2. Editing Roles
- Rename existing roles (except `USER`)
- Modify permissions via checkboxes
- Deletion possible (except `USER`)

#### 3. Permission Management
- Table interface with:
  - **Rows**: List of 10 permissions
  - **Columns**: Service roles
- Checkboxes to enable/disable each permission

#### 4. Smart Save

During save:

**a) Automatic User Synchronization**
- Users whose role was deleted are demoted to `USER` role
- Users keep their role if it still exists
- Automatic update of permission values if modified

**b) Service Chiefs Update**
- Chiefs automatically receive the **highest role** (highest permission value)
- Ensures chiefs always have maximum access

**c) Change Propagation**
- Changes are sent to the server via `sendNuiEvent('updateData')`
- Cascading update of service, users, and chiefs

## Usage in Code

### Permission Checks

The `isAuthorised(type, id)` function centralizes all checks:

```javascript
import { isAuthorised } from '@/utils/functions'

// Usage examples
if (isAuthorised('newFolder')) {
  // Create a new investigation
}

if (isAuthorised('editDoc', documentId)) {
  // Edit the document
}

if (isAuthorised('issueWarrant', warrantId)) {
  // Issue a warrant
}
```

### Available Check Types

#### Creations (`new*`)
- `newFolder`: Create an investigation
- `newDoc`: Create a document in an investigation
- `newWarrant`: Create a warrant in an investigation
- `newExam`: Create an examination in an investigation
- `newViolation`: Create a violation
- `newReccord`: Create a record (always authorized)

#### Modifications (`edit*`)
- `editFolder`: Edit an investigation
- `editDoc`: Edit a document
- `editWarrant`: Edit a warrant
- `editExam`: Edit an examination
- `editReccords`: Edit criminal records
- `editOff`: Edit an officer (chiefs only)
- `editPendings`: Manage membership requests
- `editService`: Edit service settings

#### Special Actions
- `issueWarrant`: Issue a warrant (Justice + permission)
- `sendWarrant`: Send a warrant (Justice + permission)
- `archiveFolder`: Archive an investigation (Justice + permission)

## Permission Logic

### Authorization Hierarchy

For most actions, multiple authorization levels exist:

1. **Agent in charge**: Can always edit elements they are responsible for
2. **Service permission**: Requires permission + belonging to the right service
3. **Service chief**: Priority access to the service
4. **Justice service**: Special permissions for certain actions (warrants, archives)

**Example for editing a document**:
```javascript
// Authorized IF:
// - User is in charge of the document OR
// - User has MANAGE_DOCUMENTS AND belongs to a service linked to the investigation
// AND the folder is not archived
```

### Special Restrictions

- **Archived items**: Documents, warrants, and examinations in archived investigations can no longer be edited
- **Justice warrants**: Only members of a justice service with `ISSUE_WARRANTS` can issue them
- **Archives**: Only justice services with `ARCHIVE_FOLDERS` can archive

## Warnings and Limitations

### Warning Messages

In the management interface:
- **Maximum roles**: "COMPONENTS.NOTIFICATIONS.MAX_ROLES" (6 roles max)
- **Justice roles**: "Some roles will not be used if your service is not judicial"
- **Navigation**: "Scroll wheel for vertical / Shift + Scroll wheel for horizontal"

### Useless Permissions for Non-Justice Services

The following permissions will only work for services marked as `isJustice: true`:
- `ISSUE_WARRANTS`
- `ARCHIVE_FOLDERS`

## Recommendations

### Typical Configuration by Role

**USER Role (default)**
- No permissions (value: 0)
- Can only view items they are responsible for

**AGENT Role**
- `MANAGE_DOCUMENTS` (2)
- `MANAGE_EXAMINATIONS` (16)
- `MANAGE_VIOLATIONS` (256)
- **Total value: 274**

**LIEUTENANT Role**
- `MANAGE_FOLDERS` (1)
- `MANAGE_DOCUMENTS` (2)
- `MANAGE_WARRANTS` (4)
- `MANAGE_EXAMINATIONS` (16)
- `MANAGE_VIOLATIONS` (256)
- **Total value: 279**

**CHIEF Role (maximum)**
- All permissions
- **Total value: 1023**

**JUDGE Role (justice service)**
- All permissions including:
- `ISSUE_WARRANTS` (8)
- `ARCHIVE_FOLDERS` (512)
- **Total value: 1023**

## Server Integration

Permission changes are sent to the server via:

```javascript
sendNuiEvent('updateData', {
  tabletData: { /* user data */ },
  elt: service,
  type: 'services' // or 'users'
})
```

The server must handle these events to:
- Persist changes to the database
- Synchronize permissions across all clients
- Validate permission modifications

## Source Code

### Main Files

- **Component**: `vue/src/components/Permissions.vue`
- **Utilities**: `vue/src/utils/functions.js` (`PERMISSIONS` constant and `isAuthorised` function)
- **Translations**: `vue/public/locales/fr.json` and `en.json`

### Dependencies

- Vue 3 (Composition API)
- Vue Router (navigation)
- i18n (internationalization)

---

**Note**: This system is designed to be scalable. Adding new permissions requires:
1. Add the constant in `PERMISSIONS` with the next binary value (`1 << 10`, `1 << 11`, etc.)
2. Add cases in `isAuthorised()`
3. Update translations
