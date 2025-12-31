# Day 01 – Linux User Management (Non-Interactive Shell)

## Overview
This document covers the creation of a Linux user account with a **non-interactive shell** on App Server 1.  
The task was completed as part of the **100 Days of DevOps Practice Challenge (KodeKloud)** and focuses on secure system user management.

---

## Objective
Create a user named `yousuf` with a **non-interactive shell** to meet the requirements of a backup agent tool.

---

## Background
In production Linux environments, service or system users are commonly created without interactive login capabilities.  
This approach improves security by preventing SSH or terminal access while still allowing system-level usage by applications or automated tools.

A non-interactive shell such as `/sbin/nologin` ensures:
- The account exists on the system
- Interactive login is blocked
- The principle of least privilege is enforced

---

## Infrastructure Details

| Item | Value |
|---|---|
| Server Role | App Server 1 |
| Hostname | `stapp01.stratos.xfusioncorp.com` |
| IP Address | `172.16.238.10` |
| Login User | `tony` |
| Access Level | sudo-enabled |

> Direct root login is disabled. Administrative actions are performed via `sudo`.

---

## Authentication Behavior Notes
- Linux does not echo password characters during input.
- No asterisks (`*`) or cursor movement is displayed.
- SSH may display previous failed login attempts after a successful login; these are informational logs.

---

## Implementation

### Step 1: Connect to the Server
```bash
ssh tony@172.16.238.10
````

or

```bash
ssh tony@stapp01.stratos.xfusioncorp.com
```

---

### Step 2: Create the User with a Non-Interactive Shell

```bash
sudo useradd -s /sbin/nologin yousuf
```

#### Command Explanation

* `useradd` – Creates a new user account
* `-s /sbin/nologin` – Assigns a non-interactive shell
* `yousuf` – Username required by the task

---

## Verification

### Verify User Creation

```bash
getent passwd yousuf
```

**Expected output (example):**

```text
yousuf:x:1006:1006::/home/yousuf:/sbin/nologin
```

Key confirmation:

* The assigned shell is `/sbin/nologin`

---


## Observed System Behavior

| Observation                   | Explanation                      |
| ----------------------------- | -------------------------------- |
| No output after user creation | Command executed successfully    |
| SSH authenticity prompt       | First-time server connection     |
| Silent password entry         | Standard Linux security behavior |
| Failed login messages         | Informational SSH security logs  |

---

## Common Pitfalls

* Assigning an interactive shell (e.g. `/bin/bash`)
* Running administrative commands without `sudo`
* Attempting direct root login
* Assuming lack of output indicates failure

---

## Final State

* User `yousuf` exists on App Server 1
* Interactive shell access is disabled
* System security requirements are satisfied
* Task completed successfully

---

## DevOps Best Practice

> **Service accounts should not have interactive shells unless explicitly required.**

This task reinforces:

* Secure Linux user management
* Least privilege access control
* Production-ready system administration practices
