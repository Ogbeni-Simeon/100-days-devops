# Day 07 – Password-less SSH Access (Jump Host to App Servers)

## Overview
This document captures my understanding of how **password-less SSH authentication** was configured from the **jump host** to all **application servers** in the Stratos Datacenter.

This task is part of **Day 7** of the *100 Days of DevOps Practice Challenge (KodeKloud)* and focuses on enabling **secure, non-interactive access** required for automation scripts.

---

## Objective
Set up **password-less SSH access** such that:

- User `thor` on the **jump host**
- Can SSH into **all app servers**
- Using their respective sudo user (`tony`)
- **Without being prompted for a password**

This is required so scheduled scripts on the jump host can run automatically.

---

## Why This Matters
Automation tools and scripts cannot type passwords.

In real DevOps environments:
- CI/CD pipelines
- Ansible playbooks
- Backup and monitoring scripts

all rely on **SSH key-based authentication** instead of passwords.

This task ensures:
- Secure authentication
- Non-interactive access
- Automation readiness

---

## Key Concept: How Password-less SSH Works

SSH key-based authentication uses **two keys**:

- **Private key** → stays on the client (jump host, user `thor`)
- **Public key** → copied to the server (app servers, user `tony`)

If the server trusts the public key and the client proves it owns the matching private key, SSH access is granted **without a password**.

---

## Environment Roles

| System | User | Purpose |
|-----|-----|------|
| Jump Host | `thor` | Initiates SSH connections |
| App Servers | `tony` | Receives SSH connections |
| Authentication | SSH keys | Enables password-less access |

All actions in this task start **from the jump host as user `thor`**.

---

## Step 1 – Confirm Current User and Location

I ensured I was logged into the jump host as `thor`.

```bash
whoami
hostname
````

Expected:

```text
thor
jumphost
```

---

## Step 2 – Check for Existing SSH Keys

Before creating new keys, I checked if SSH keys already existed.

```bash
ls ~/.ssh
```

If keys like `id_rsa` and `id_rsa.pub` exist, they can be reused.
If not, a new key pair must be generated.

---

## Step 3 – Generate an SSH Key Pair (If Needed)

```bash
ssh-keygen -t rsa -b 2048
```

During the prompts:

* File location → pressed **Enter** (default)
* Passphrase → pressed **Enter** (left empty)

### Why no passphrase?

Automation requires **non-interactive authentication**.
A passphrase would require manual input and break automation.

This created:

* `~/.ssh/id_rsa` (private key)
* `~/.ssh/id_rsa.pub` (public key)

---

## Step 4 – Copy Public Key to App Server 1

From the jump host, I copied the public key to App Server 1 using the `tony` user.

```bash
ssh-copy-id tony@stapp01.stratos.xfusioncorp.com
```

This command:

* Logs into the server once using a password
* Appends the public key to:

  ```
  /home/tony/.ssh/authorized_keys
  ```

After this step, `thor` can SSH into `stapp01` as `tony` without a password.

---

## Step 5 – Repeat for All App Servers

The same process was repeated for **every app server**:

```bash
ssh-copy-id tony@stapp02.stratos.xfusioncorp.com
ssh-copy-id tony@stapp03.stratos.xfusioncorp.com
```

Each server must have the public key installed, otherwise automation will fail.

---

## Step 6 – Verify Password-less SSH Access

I tested SSH access to each server to confirm no password was required.

```bash
ssh tony@stapp01.stratos.xfusioncorp.com
ssh tony@stapp02.stratos.xfusioncorp.com
ssh tony@stapp03.stratos.xfusioncorp.com
```

Expected behavior:

* Immediate login
* No password prompt

Each session was exited using:

```bash
exit
```

---

## Common Pitfalls Avoided

* Generating SSH keys as the wrong user
* Setting a passphrase on the key
* Copying the key to the wrong account
* Configuring only one app server
* Skipping verification

---

## Final State

* SSH key pair exists for `thor` on the jump host
* Public key installed for `tony` on all app servers
* Password-less SSH access confirmed
* Jump host scripts can now run automation safely

---

## Key Takeaways

* Passwords do not scale for automation
* SSH keys are the industry standard for secure access
* Automation always assumes **non-interactive authentication**
* Correct user context is critical

---

## Personal Reflection

This task clarified how most real-world DevOps automation actually connects to servers.
Understanding SSH keys is foundational for tools like Ansible, CI/CD pipelines, and remote execution workflows.

---
