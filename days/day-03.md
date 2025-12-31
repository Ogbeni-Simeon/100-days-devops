# Day 03 – Disable Direct Root SSH Login

## Overview
This document describes the process of **disabling direct SSH login for the root user** on all application servers in the Stratos Datacenter.  
The task was completed as part of the **100 Days of DevOps Practice Challenge (KodeKloud)** and focuses on Linux security hardening.

---

## Objective
Disable direct SSH access for the `root` user on **all app servers** within the Stratos Datacenter while preserving administrative access via `sudo`.

---

## Background
Allowing direct SSH access for the root user poses a security risk, as it:
- Increases the attack surface
- Enables brute-force attempts against the most privileged account
- Reduces accountability and auditability

Industry best practice is to:
- Disable root SSH login
- Use named user accounts with `sudo` privileges
- Enforce least privilege and traceability

---

## Infrastructure Details

| Item | Value |
|---|---|
| Datacenter | Stratos |
| Server Role | Application Servers |
| Servers | `stapp01`, `stapp02`, `stapp03` |
| Login User | `tony` |
| Access Level | sudo-enabled |

> Root login via SSH is disabled by design. Administrative access is granted via `sudo`.

---

## Implementation Approach
A **non-interactive, editor-free method** was used to ensure consistency and reliability across servers.  
This approach is automation-friendly and mirrors real-world DevOps practices.

---

## Implementation Steps
The following steps were performed **on each app server**.

### Step 1: Connect to the App Server
```bash
ssh tony@stapp0X.stratos.xfusioncorp.com
````

---

### Step 2: Verify Current Root Login Setting

```bash
sudo grep -i PermitRootLogin /etc/ssh/sshd_config
```

---

### Step 3: Disable Root SSH Login

```bash
sudo sed -i 's/^#\?PermitRootLogin.*/PermitRootLogin no/' /etc/ssh/sshd_config
```

This command ensures that:

* Existing `PermitRootLogin` entries are replaced
* Commented and uncommented entries are handled
* The configuration is enforced consistently

---

### Step 4: Confirm Configuration

```bash
sudo grep -i PermitRootLogin /etc/ssh/sshd_config
```

**Expected output:**

```text
PermitRootLogin no
```

---

### Step 5: Restart SSH Service

```bash
sudo systemctl restart sshd
```

Verify service status:

```bash
sudo systemctl status sshd
```

Expected state:

```text
Active: active (running)
```

---

## Verification

### Root SSH Access Test

From a separate terminal:

```bash
ssh root@stapp0X.stratos.xfusioncorp.com
```

**Expected result:**

```text
Permission denied, please try again.
```

This confirms that direct root SSH login is disabled.

---

## Observed System Behavior

| Observation                             | Explanation                                      |
| --------------------------------------- | ------------------------------------------------ |
| No output from `sed` command            | Command executed successfully                    |
| SSH remains accessible for normal users | Root restriction does not affect standard access |
| Root access via `sudo` still works      | Administrative access preserved                  |

---

## Common Pitfalls

* Forgetting to restart the SSH service
* Editing the wrong configuration file
* Applying changes to only one server
* Logging out before validating SSH service status

---

## Final State

* Direct root SSH login disabled on all app servers
* SSH service running normally
* Administrative access maintained via `sudo`
* Security posture improved

---

## DevOps Best Practice

> **Never allow direct SSH access to the root account.**

This task reinforces:

* Linux security hardening
* Access control best practices
* Production-grade operational discipline
