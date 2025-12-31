# Day 05 – Install and Permanently Disable SELinux

## Overview
This document describes the installation of required **SELinux packages** and the **permanent disabling of SELinux** on App Server 1.  
The task was completed as part of the **100 Days of DevOps Practice Challenge (KodeKloud)** and focuses on controlled security configuration management.

---

## Objective
On **App Server 1** in the Stratos Datacenter:
- Install the required SELinux packages
- Permanently disable SELinux
- Do **not** reboot the server
- Ignore the current runtime SELinux status; the expected state is **disabled after reboot**

---

## Background
SELinux (Security-Enhanced Linux) is a mandatory access control system used to enhance system security.  
In enterprise environments, SELinux is sometimes temporarily disabled during initial testing or while making configuration changes, with plans to re-enable it later.

Disabling SELinux **permanently** requires modifying its configuration file so that the change takes effect after the next reboot.

---

## Infrastructure Details

| Item | Value |
|---|---|
| Datacenter | Stratos |
| Server Role | App Server 1 |
| Hostname | `stapp01.stratos.xfusioncorp.com` |
| Login User | `tony` |
| Access Level | sudo-enabled |

---

## Implementation

### Step 1: Connect to App Server 1
```bash
ssh tony@stapp01.stratos.xfusioncorp.com
````

Confirm correct server:

```bash
hostname
```

Expected output:

```text
stapp01
```

---

### Step 2: Install Required SELinux Packages

```bash
sudo yum install -y selinux-policy selinux-policy-targeted policycoreutils
```

This ensures all necessary SELinux components are present on the system.

---

### Step 3: Permanently Disable SELinux

```bash
sudo sed -i 's/^SELINUX=.*/SELINUX=disabled/' /etc/selinux/config
```

This modifies the persistent SELinux configuration so that SELinux will be disabled after the next reboot.

---

### Step 4: Verify Configuration

```bash
cat /etc/selinux/config
```

Expected output (relevant line):

```text
SELINUX=disabled
```

---

## Notes on Runtime Status

* The `getenforce` command may still show `Enforcing` or `Permissive`
* This is expected because the system was **not rebooted**
* The task explicitly requires ignoring the current runtime status

---

## Common Pitfalls

* Using `setenforce 0` without updating the config file (temporary change only)
* Editing the wrong configuration file
* Rebooting the server
* Applying the change on the wrong server

---

## Final State

* Required SELinux packages installed
* SELinux permanently disabled via configuration
* No reboot performed
* System ready for future SELinux reconfiguration

---

## DevOps Best Practice

> **Permanent security configuration changes should always be made via configuration files, not runtime commands.**

This task reinforces:

* Secure system configuration management
* Understanding of SELinux behavior
* Change control discipline in production environments

```
Whenever you’re ready, send **Day 6** 🚀
```
