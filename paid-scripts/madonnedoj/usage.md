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

### Login or Register ?

<figure><img src="../../.gitbook/assets/image (3).png" alt="Screenshot of the account creation screen"><figcaption><p>Account creation screen</p></figcaption></figure>

The first screen you will encounter is the account creation screen.&#x20;

* Enter your role-play information (surname, first name, date of birth) and the department you wish to join.
* Click on ‘Submit profile’ and a request will be sent to the managers of the requested service.

> Administrators can also use the "Connect as a server admin" button to access their view.

<figure><img src="../../.gitbook/assets/image (2).png" alt="Screenshot of the login screen"><figcaption><p>Login screen</p></figcaption></figure>

Once your request has been accepted, you will be able to log in to your profile. Simply select it and click on ‘Login’.

You also have the option to create other profiles (they are all linked to your Discord ID).

### Sidebar Menu (Left)

<figure><img src="../../.gitbook/assets/image (4).png" alt="Sidebar screenshot"><figcaption><p>Sidebar</p></figcaption></figure>

The sidebar contains navigation icons for all available sections:

* 📊 **Dashboard** - Your personal overview
* ⚙️ **Services** - Service administration
* 📁 **Investigations** - Case management
* ⚖️ **Warrants** - Warrant system
* 👤 **Records** - Criminal records
* 🚨 **Violations** - Offense catalog
* 🗄️**Archives** - Archived case viewing

{% hint style="info" %}
Click on your name to log out.
{% endhint %}

### Main Content Area (Right)

The main area displays the content for the selected section.

## Features by Section

### 📊 Dashboard

<figure><img src="../../.gitbook/assets/image (6).png" alt="Dashboard screenshot"><figcaption><p>Dashboard</p></figcaption></figure>

Your personal dashboard shows:

* **My Investigations** - Cases you're assigned to
* **My Documents** - Documents you've created
* **My Examinations** - Interrogations you've conducted

**Quick Actions:**

* Click any item to open it
* See recent activity at a glance

***

### ⚙️ Services

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption><p>Detailed vue of a service</p></figcaption></figure>

Manage service members and pending requests (Chiefs only).

**What you can do:**

* ✅ View service members
* ✅ Approve pending members
* ✅ Remove members from service
* ✅ Manage service roster

{% hint style="warning" %}
**Required Permission:** `MANAGE_SERVICES` (128)
{% endhint %}

**Service Management:**

1. View all current members
2. See pending join requests
3. Approve or deny requests
4. Remove officers from service

***

### 📁 Investigations

<figure><img src="../../.gitbook/assets/image (8).png" alt="Screenshot of the main view of investigations tab"><figcaption><p>Investigations main view</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption><p>Detailed view of an investigation</p></figcaption></figure>

Manage investigation folders and cases.

**What you can do :**

* ✅ Create new investigation folders
* ✅ View all investigations (if you have access)
* ✅ Edit investigation details
* ✅ Assign officers to cases
* ✅ Assign services to investigations

{% hint style="warning" %}
**Required Permission:** `MANAGE_FOLDERS` (1)
{% endhint %}

{% hint style="info" %}
* The investigations you are responsible for appear in purple.
* You only have access to your own investigations or those of your department.
{% endhint %}

**How to create an investigation:**

<figure><img src="../../.gitbook/assets/image (10).png" alt="Creating an investigation" width="563"><figcaption><p>Creating an investigation</p></figcaption></figure>

1. Click the **"+"** button
2. Enter investigation title
3. Add description
4. Assign officers in charge
5. Select services involved
6. Click **Save**

***

### ⚖️ Warrants

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption><p>Detailed view of a warrant</p></figcaption></figure>

Manage arrest warrants and search warrants.

**What you can do:**

* ✅ Create warrant requests (police)
* ✅ View warrants
* ✅ Edit pending warrants
* ✅ Sign/Issue warrants (justice only)
* ✅ Send warrants to Discord

{% hint style="warning" %}
**Required Permissions:**

* `MANAGE_WARRANTS` (4) - Create and edit warrants
* `ISSUE_WARRANTS` (8) - Sign and issue warrants (justice department only)
{% endhint %}

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
3. Select suspect from folder
4. Enter details and probable cause
5. Submit for approval

**How to issue a warrant (Justice only):**

1. Open pending warrant
2. Review details
3. Click **Issue Warrant**
4. Enter reason/notes
5. Confirm issuance
6. Warrant is now active

***

### 📄 Documents (only in investigation view)

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption><p>Detailed view of a document</p></figcaption></figure>

Create and manage documents related to investigations.

**What you can do:**

* ✅ Create new documents
* ✅ View documents (from your service or investigations you're assigned to)
* ✅ Edit existing documents
* ✅ Assign officers to documents
* ✅ Add suspects and witnesses

{% hint style="warning" %}
**Required Permission:** `MANAGE_DOCUMENTS` (2)
{% endhint %}

***

### 🎤 Examinations (only in investigation view)

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption><p>Detailed view of an examination</p></figcaption></figure>

Record interrogations and witness statements.

**What you can do:**

* ✅ Create examination records
* ✅ Document interrogations
* ✅ Link to investigation folders
* ✅ Record suspect/witness statements
* ✅ Assign conducting officers

{% hint style="warning" %}
**Required Permission:** `MANAGE_EXAMINATIONS` (16)
{% endhint %}

**How to record an examination:**

1. Click the **"+"** button
2. Enter examination title
3. Select examinee (suspect/witness)
4. Add interrogation details/transcript
5. Assign officers present
6. Click **Save**

***

### 👤 Records

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption><p>Detailed view of a criminal record</p></figcaption></figure>

View and manage citizen criminal records.

**What you can do:**

* ✅ Search for citizens
* ✅ View criminal history
* ✅ See all related investigations
* ✅ Create new citizen records
* ✅ Update citizen information

{% hint style="warning" %}
**Required Permission:** `MANAGE_RECORDS` (64)
{% endhint %}

**How to search records:**

1. Use the search bar
2. Enter citizen name or ID
3. Click on result to view full record
4. See all investigations, warrants

**Record Information Includes:**

* Personal information
* Investigation history
* Active warrants

***

### 🚨 Violations

Manage the catalog of criminal offenses.

**What you can do:**

* ✅ View all violations
* ✅ Add new violation types
* ✅ Edit violation details
* ✅ Set fines and jail times
* ✅ Categorize offenses

{% hint style="warning" %}
**Required Permission:** `MANAGE_VIOLATIONS` (256)
{% endhint %}

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

| Section                | Required Permission  | Value |
| ---------------------- | -------------------- | ----- |
| Dashboard              | (Any permission)     | -     |
| Investigations         | MANAGE\_FOLDERS      | 1     |
| Documents              | MANAGE\_DOCUMENTS    | 2     |
| Warrants (Create)      | MANAGE\_WARRANTS     | 4     |
| Warrants (Issue)       | ISSUE\_WARRANTS      | 8     |
| Examinations           | MANAGE\_EXAMINATIONS | 16    |
| Requests               | MANAGE\_REQUESTS     | 32    |
| Records                | MANAGE\_RECORDS      | 64    |
| Services               | MANAGE\_SERVICES     | 128   |
| Violations             | MANAGE\_VIOLATIONS   | 256   |
| Archive investigations | ARCHIVE\_FOLDERS     | 512   |

For more on permissions, see:

* [Permissions System](configuration/permissions-system.md)

## Getting Help

If you need assistance:

* 📖 Check this documentation
* 💬 Ask your supervisor or chief
* 🎫 Contact server administration
* 📧 Report bugs to development team
