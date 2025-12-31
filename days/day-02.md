# Day 02 – Temporary Linux User with Expiry Date

## Overview
This document covers the creation of a **temporary Linux user account with an expiry date** on App Server 1.  
The task was completed as part of the **100 Days of DevOps Practice Challenge (KodeKloud)** and focuses on controlled, time-bound access management.

---

## Objective
Create a user named `javed` on App Server 1 in the Stratos Datacenter and configure the account to **expire on 2024-04-15**.  
The username must be created in **lowercase** as per standard Linux user-naming conventions.

---

## Background
Temporary user accounts are commonly used in enterprise environments for:
- Short-term project assignments
- Contractors or consultants
- Time-bound access control

Linux supports account expiration through user management tools, allowing administrators to automatically disable access after a specified date. This helps enforce:
- Security compliance
- Least privilege
- Proper access lifecycle management

---

## Infrastructure Details

| Item | Value |
|---|---|
| Server Role | App Server 1 |
| Datacenter | Stratos |
| Hostname | `stapp01.stratos.xfusioncorp.com` |
| IP Address | `172.16.238.10` |
| Login User | `tony` |
| Access Level | sudo-enabled |

> Direct root login is disabled. All administrative operations are executed using `sudo`.

---

## Authentication Notes
- Linux does not display characters during password entry.
- SSH may show previous failed login attempts after successful authentication.
- These messages are informational and do not indicate an error.

---

## Implementation

### Step 1: Connect to App Server 1
```bash
ssh tony@172.16.238.10
````

or

```bash
ssh tony@stapp01.stratos.xfusioncorp.com
```

---

### Step 2: Create the Temporary User with Expiry Date

```bash
sudo useradd -e 2024-04-15 javed
```

#### Command Explanation

* `useradd` – Creates a new user account
* `-e 2024-04-15` – Sets the account expiration date
* `javed` – Lowercase username as required

---

## Verification

### Verify Account Expiry Date

```bash
sudo chage -l javed
```

**Expected output (example):**

```text
Account expires                                    : Apr 15, 2024
```

This confirms that the user account will automatically expire on the specified date.

---

### Verify User Existence

```bash
getent passwd javed
```

**Expected output (example):**

```text
javed:x:1007:1007::/home/javed:/bin/bash
```

---

## Observed System Behavior

| Observation                   | Explanation                        |
| ----------------------------- | ---------------------------------- |
| No output after user creation | Command executed successfully      |
| Silent password prompt        | Standard Linux security behavior   |
| Expiry date shown via `chage` | Confirms account lifecycle control |

---

## Common Pitfalls

* Using uppercase letters in the username
* Incorrect date format (must be `YYYY-MM-DD`)
* Forgetting to set the expiry date
* Running `useradd` without `sudo`
* Creating the user on the wrong server

---

## Final State

* User `javed` exists on App Server 1
* Account expiration is set to **2024-04-15**
* Username follows lowercase naming standards
* Task completed successfully

---

## DevOps Best Practice

> **Temporary access should always be time-bound to reduce security risk.**

This task reinforces:

* Access lifecycle management
* Secure Linux user administration
* Enterprise-grade DevOps operational discipline
