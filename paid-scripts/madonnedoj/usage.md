---
cover: .gitbook/assets/banner.png
coverY: 0
---

# Usage Guide

This guide will help you understand how to use the Madonne DOJ tablet interface effectively.

## Opening the Tablet

To open the DOJ tablet, use the command configured in your `config.lua`:

```
/tablet
```

By default, this is `/tablet`, but your server administrator may have changed it.

{% hint style="info" %}
**Note:** Only players with assigned police or justice services can access the tablet.
{% endhint %}

## Interface Overview

The tablet interface is divided into two main parts:

### Sidebar Menu (Left)

The sidebar contains navigation icons for all available sections:

* 📊 **Dashboard** - Your personal overview
* 📁 **Investigations** - Case management
* ⚖️ **Warrants** - Warrant system
* 👤 **Records** - Criminal records
* 🚨 **Violations** - Offense catalog
* ⚙️ **Services** - Service administration

### Main Content Area (Right)

The main area displays the content for the selected section.

## Features by Section

### 📊 Dashboard

Your personal dashboard shows:

* **My Investigations** - Cases you're assigned to
* **My Documents** - Documents you've created
* **My Examinations** - Interrogations you've conducted

**Quick Actions:**

* Click any item to open it
* See recent activity at a glance

***

### 📁 Investigations

Manage investigation folders and cases.

**What you can do:**

* ✅ Create new investigation folders
* ✅ View all investigations (if you have access)
* ✅ Edit investigation details
* ✅ Assign officers to cases
* ✅ Assign services to investigations

**Required Permission:** `MANAGE_FOLDERS` (1)

**How to create an investigation:**

1. Click the **"+"** button
2. Enter investigation title
3. Add description
4. Assign officers in charge
5. Select services involved
6. Click **Save**

***

### 📄 Documents

Create and manage documents related to investigations.

**What you can do:**

* ✅ Create new documents
* ✅ View documents (from your service or investigations you're assigned to)
* ✅ Edit existing documents
* ✅ Link documents to investigations
* ✅ Assign officers to documents
* ✅ Add suspects and witnesses

**Required Permission:** `MANAGE_DOCUMENTS` (2)

**Document Types:**

* Reports
* Evidence logs
* Interview notes
* Case summaries
* Any custom document

**How to create a document:**

1. Click the **"+"** button
2. Select the investigation folder
3. Enter document title
4. Add content/description
5. Assign officers in charge
6. Add related citizens
7. Click **Save**

***

### ⚖️ Warrants

Manage arrest warrants and search warrants.

**What you can do:**

* ✅ Create warrant requests (police)
* ✅ View warrants
* ✅ Edit pending warrants
* ✅ Sign/Issue warrants (justice only)
* ✅ Send warrants to Discord

**Required Permissions:**

* `MANAGE_WARRANTS` (4) - Create and edit warrants
* `ISSUE_WARRANTS` (8) - Sign and issue warrants (justice only)

**Warrant Types:**

* 🚔 **Arrest Warrant** - To arrest a suspect
* 🔍 **Search Warrant** - To search property

**Warrant Workflow:**

1. **Police Officer** creates warrant request
2. Fills in suspect information
3. Adds probable cause
4. Submits for approval
5. **Judge** reviews the warrant
6. Judge signs and issues if approved
7. Warrant becomes active
8. Notification sent to Discord (if configured)

**How to create a warrant:**

1. Click the **"+"** button
2. Select warrant type (Arrest/Search)
3. Choose investigation folder
4. Select suspect from folder
5. Enter details and probable cause
6. Submit for approval

**How to issue a warrant (Justice only):**

1. Open pending warrant
2. Review details
3. Click **Issue Warrant**
4. Enter reason/notes
5. Confirm issuance
6. Warrant is now active

***

### 🎤 Examinations

Record interrogations and witness statements.

**What you can do:**

* ✅ Create examination records
* ✅ Document interrogations
* ✅ Link to investigation folders
* ✅ Record suspect/witness statements
* ✅ Assign conducting officers

**Required Permission:** `MANAGE_EXAMINATIONS` (16)

**How to record an examination:**

1. Click the **"+"** button
2. Select investigation folder
3. Enter examination title
4. Select examinee (suspect/witness)
5. Add interrogation details/transcript
6. Assign officers present
7. Click **Save**

***

### 👤 Records

View and manage citizen criminal records.

**What you can do:**

* ✅ Search for citizens
* ✅ View criminal history
* ✅ See all related investigations
* ✅ Create new citizen records
* ✅ Update citizen information

**Required Permission:** `MANAGE_RECORDS` (64)

**How to search records:**

1. Use the search bar
2. Enter citizen name or ID
3. Click on result to view full record
4. See all investigations, warrants, violations

**Record Information Includes:**

* Personal information
* Investigation history
* Active warrants
* Past violations
* Related documents

***

### 🚨 Violations

Manage the catalog of criminal offenses.

**What you can do:**

* ✅ View all violations
* ✅ Add new violation types
* ✅ Edit violation details
* ✅ Set fines and jail times
* ✅ Categorize offenses

**Required Permission:** `MANAGE_VIOLATIONS` (256)

**How to add a violation:**

1. Click the **"+"** button
2. Enter violation name
3. Add description
4. Set fine amount
5. Set jail time
6. Assign category
7. Click **Save**

**Violation Categories:**

* Traffic offenses
* Violent crimes
* Property crimes
* Drug offenses
* White collar crimes
* Custom categories

***

### ⚙️ Services

Manage service members and pending requests (Chiefs only).

**What you can do:**

* ✅ View service members
* ✅ Approve pending members
* ✅ Remove members from service
* ✅ Manage service roster

**Required Permission:** `MANAGE_SERVICES` (128)

**Service Management:**

1. View all current members
2. See pending join requests
3. Approve or deny requests
4. Remove officers from service

***

## Tips and Best Practices

### Organization

✅ **Do:**

* Create investigation folders for each case
* Link all related documents to investigations
* Assign officers to cases they're working on
* Keep descriptions clear and detailed

❌ **Don't:**

* Create duplicate investigations
* Leave documents unlinked
* Forget to assign officers
* Use vague titles

### Warrants

✅ **Do:**

* Provide detailed probable cause
* Select the correct suspect
* Wait for judicial approval before acting
* Document warrant execution

❌ **Don't:**

* Create warrants without sufficient cause
* Rush the approval process
* Act on unsigned warrants
* Forget to link to investigation

### Documentation

✅ **Do:**

* Document all investigative actions
* Record all examinations
* Keep records up-to-date
* Use proper grammar and spelling

❌ **Don't:**

* Skip documentation
* Leave fields empty
* Use abbreviations others won't understand
* Mix personal and official notes

## Keyboard Shortcuts

Currently, there are no keyboard shortcuts. Navigate using mouse clicks.

## Troubleshooting

### Can't see certain sections

**Cause:** You don't have permission\
**Solution:** Contact your supervisor or administrator

### Can't create items

**Cause:** Missing required permissions\
**Solution:** Check your role permissions

### Items not saving

**Cause:** Server connection issue\
**Solution:** Check console (F8), contact administrator

### Tablet won't open

**Cause:** Not assigned to a service or wrong command\
**Solution:** Verify you're employed and using correct command

## Permission Quick Reference

To use each section, you need:

| Section           | Required Permission  | Value |
| ----------------- | -------------------- | ----- |
| Dashboard         | (Any permission)     | -     |
| Investigations    | MANAGE\_FOLDERS      | 1     |
| Documents         | MANAGE\_DOCUMENTS    | 2     |
| Warrants (Create) | MANAGE\_WARRANTS     | 4     |
| Warrants (Issue)  | ISSUE\_WARRANTS      | 8     |
| Examinations      | MANAGE\_EXAMINATIONS | 16    |
| Requests          | MANAGE\_REQUESTS     | 32    |
| Records           | MANAGE\_RECORDS      | 64    |
| Services          | MANAGE\_SERVICES     | 128   |
| Violations        | MANAGE\_VIOLATIONS   | 256   |

For more on permissions, see:

* [Permissions System](configuration/permissions-system.md)

## Getting Help

If you need assistance:

* 📖 Check this documentation
* 💬 Ask your supervisor or chief
* 🎫 Contact server administration
* 📧 Report bugs to development team

