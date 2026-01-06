# Day 08 – Installing Ansible on the Jump Host

## Overview
This document captures my understanding of how **Ansible** was installed and prepared on the **jump host** to act as an automation controller.  
This task marks the first step into **configuration management and automation** in the *100 Days of DevOps Practice Challenge (KodeKloud)*.

---

## Objective
Install **Ansible version 4.10.0** on the **jump host** with the following constraints:

- Installation must be done using **pip3 only**
- Ansible must be **globally available** (all users can run Ansible commands)
- Jump host will serve as the **Ansible controller**

---

## Why This Matters
Ansible is a popular automation and configuration management tool used to:
- Manage servers at scale
- Automate repetitive system tasks
- Enforce configuration consistency

Before using Ansible to manage other servers, it must be properly installed on a central control node (the jump host).

Using `pip3` allows:
- Precise version control
- Independence from OS package repositories
- Easier upgrades and maintenance

---

## Environment Context

| Component | Value |
|--------|------|
| Control Node | Jump Host |
| User | `thor` |
| Installation Method | `pip3` |
| Required Version | Ansible 4.10.0 |

All installation steps were performed **on the jump host**.

---

## Step 1 – Confirm Jump Host Access

I first confirmed I was logged into the correct system.

```bash
hostname
````

Expected output:

```text
jumphost
```

---

## Step 2 – Verify pip3 Availability

Since the task requires installing Ansible using `pip3`, I verified that it was available.

```bash
pip3 --version
```

If `pip3` was missing, it would be installed using:

```bash
sudo yum install -y python3-pip
```

---

## Step 3 – Install Ansible 4.10.0 Using pip3

To ensure a **system-wide installation**, I used `sudo` with `pip3`.

```bash
sudo pip3 install ansible==4.10.0
```

### Why this command works

* `sudo` installs the package globally
* `pip3` is the Python 3 package manager
* `ansible==4.10.0` ensures the exact required version is installed

This installs Ansible binaries such as:

* `ansible`
* `ansible-playbook`

into a global directory (e.g. `/usr/local/bin`).

---

## Step 4 – Verify Ansible Installation

After installation, I verified the version and availability.

```bash
ansible --version
```

Expected output includes:

* Ansible version **4.10.0**
* A global executable path such as `/usr/local/bin/ansible`

This confirms that Ansible is installed correctly and accessible from the command line.

---

## Step 5 – Confirm Global Availability

To ensure Ansible is available to **all users**, not just `thor`, I verified that the `ansible` command could be executed system-wide.

This confirms compliance with the requirement that Ansible must be globally accessible.

---

## Common Pitfalls Avoided

* Installing Ansible via `yum` instead of `pip3`
* Installing a different Ansible version
* Using `pip3 install --user`
* Installing Ansible on the wrong server
* Forgetting to verify the installed version

---

## Final State

* Ansible version **4.10.0** installed
* Installation performed using **pip3**
* Ansible commands available globally
* Jump host ready to act as an **Ansible controller**

---

## Key Takeaways

* Ansible is Python-based and integrates well with `pip`
* Global installation is required for automation workflows
* Version control is critical in DevOps tooling
* The jump host acts as a central point of control

---

## Personal Reflection

This task marked the transition from basic Linux administration into **automation and configuration management**.
Having Ansible installed correctly is foundational for managing multiple servers efficiently and consistently.

```
