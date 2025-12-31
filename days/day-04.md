# Day 04 – Grant Executable Permissions to a Bash Script

## Overview
This document describes the process of granting **executable permissions** to a bash script used for automating backup processes.  
The task was completed as part of the **100 Days of DevOps Practice Challenge (KodeKloud)** and focuses on Linux file permission management.

---

## Objective
Grant executable permissions to the script located at:

```

/tmp/xfusioncorp.sh

````

on **App Server 3** in the Stratos Datacenter, ensuring that **all users** are able to execute the script.

---

## Background
In Linux, files are not executable by default.  
For automation tasks such as backups, scripts must be explicitly granted execute permissions.

Linux file permissions are divided into three categories:
- **Owner**
- **Group**
- **Others**

To allow all users to execute a script, the execute (`x`) permission must be set for each category.

---

## Infrastructure Details

| Item | Value |
|---|---|
| Datacenter | Stratos |
| Server Role | App Server 3 |
| Hostname | `stapp03.stratos.xfusioncorp.com` |
| Login User | `tony` |
| Access Level | sudo-enabled |

---

## Implementation

### Step 1: Connect to App Server 3
```bash
ssh tony@stapp03.stratos.xfusioncorp.com
````

Confirm correct server:

```bash
hostname
```

Expected output:

```text
stapp03
```

---

### Step 2: Verify Script Existence

```bash
ls -l /tmp/xfusioncorp.sh
```

Example output before permission change:

```text
-rw-r--r-- 1 root root ... xfusioncorp.sh
```

---

### Step 3: Grant Executable Permissions to All Users

```bash
sudo chmod 755 /tmp/xfusioncorp.sh
```

#### Permission Breakdown

* `7` → Owner: read, write, execute
* `5` → Group: read, execute
* `5` → Others: read, execute

This ensures that **all users** can execute the script.

---

### Step 4: Verify Permissions

```bash
ls -l /tmp/xfusioncorp.sh
```

Expected output:

```text
-rwxr-xr-x 1 root root ... xfusioncorp.sh
```

---

## Observed System Behavior

| Observation             | Explanation                    |
| ----------------------- | ------------------------------ |
| No output from `chmod`  | Command executed successfully  |
| Updated permission bits | Confirms executable access     |
| Script not executed     | Execution not required by task |

---

## Common Pitfalls

* Applying permissions on the wrong server
* Using an incorrect file path
* Forgetting to verify permissions
* Assuming script execution is required

---

## Final State

* Script `/tmp/xfusioncorp.sh` exists on App Server 3
* Executable permissions granted to all users
* Task completed successfully

---

## DevOps Best Practice

> **Always explicitly set executable permissions for automation scripts.**

This task reinforces:

* Linux permission management
* Secure automation practices
* Attention to task-specific requirements

```


