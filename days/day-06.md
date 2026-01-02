# Day 06 – Scheduling Tasks with Cron (cronie)

## Overview
This document captures my understanding of **cron job scheduling** in Linux, completed as part of **Day 6** of the *100 Days of DevOps Practice Challenge (KodeKloud)*.

The task focused on installing and running the cron service, then configuring a **sample scheduled task** for testing automation readiness across all application servers.

---

## Objective
On **all Nautilus app servers** in the Stratos Datacenter:

1. Install the `cronie` package  
2. Ensure the `crond` service is running  
3. Configure a cron job for the **root user** that runs every 5 minutes:
```

*/5 * * * * echo hello > /tmp/cron_text

````

---

## Why This Matters
Cron is one of the most fundamental Linux automation tools. It is used for:
- Backups
- Log rotation
- Cleanup jobs
- Health checks
- Scheduled scripts

Before deploying real automation scripts, it is important to:
- Confirm the cron service works
- Ensure jobs run under the correct user (often `root`)
- Validate scheduling syntax

---

## Infrastructure Scope

This task was completed on **all app servers**:
- `stapp01`
- `stapp02`
- `stapp03`

Each server was configured individually.

---

## Step 1 – Install Cron Service (cronie)

### Command used
```bash
sudo yum install -y cronie
````

### Explanation

* `yum` is the package manager for RHEL-based systems
* `install` installs new packages
* `-y` automatically confirms prompts
* `cronie` provides the `crond` daemon (the cron scheduler)

---

## Step 2 – Start and Enable the Cron Service

### Commands used

```bash
sudo systemctl start crond
sudo systemctl enable crond
```

### Explanation

* `systemctl start crond` starts the cron service immediately
* `systemctl enable crond` ensures cron starts automatically after reboot

### Verification

```bash
sudo systemctl status crond
```

The service must show:

```
Active: active (running)
```

---

## Step 3 – Add a Cron Job for the Root User

### Important Note

Cron jobs are **user-specific**.
Since the task required the job to run as **root**, it must be added to **root’s crontab**, not a normal user’s.

Because interactive editors were unreliable in the lab environment, a **non-interactive method** was used.

---

### Command used (editor-free, reliable method)

```bash
sudo bash -c 'echo "*/5 * * * * echo hello > /tmp/cron_text" | crontab -'
```

### Command explanation

* `sudo bash -c` runs the entire command as root
* `echo "*/5 * * * * echo hello > /tmp/cron_text"` creates the cron entry
* `|` pipes the output
* `crontab -` installs the input as root’s crontab

This method avoids editors and works reliably in automated environments.

---

## Step 4 – Verify the Cron Job

### Command used

```bash
sudo crontab -l
```

### Expected output

```text
*/5 * * * * echo hello > /tmp/cron_text
```

This confirms:

* The cron job exists
* It belongs to the root user
* The schedule is correct

---

## Cron Timing Breakdown (Important for Understanding)

```
*/5 * * * *
```

| Field | Meaning            |
| ----- | ------------------ |
| `*/5` | Every 5 minutes    |
| `*`   | Every hour         |
| `*`   | Every day of month |
| `*`   | Every month        |
| `*`   | Every day of week  |

---

## Common Pitfalls Avoided

* Adding the cron job as a normal user instead of root
* Forgetting to install `cronie`
* Forgetting to start the `crond` service
* Relying on interactive editors in unstable terminals
* Configuring the job on only one server

---

## Final State

* `cronie` installed on all app servers
* `crond` service running on all app servers
* Root cron job scheduled every 5 minutes
* Task completed successfully across the environment

---

## Key Takeaways

* Cron jobs are a core automation primitive in Linux
* Cron configuration is user-specific
* Non-interactive approaches scale better and are automation-friendly
* Service status must always be verified, not assumed

---

**End of Day 06 – Personal Study Notes**

```

---

## ✅ Progress Update
You now have **personal, beginner-friendly, well-explained documentation** for:

- Day 1 ✔ Users & shells  
- Day 2 ✔ Temporary access  
- Day 3 ✔ SSH security  
- Day 4 ✔ File permissions  
- Day 5 ✔ SELinux configuration  
- Day 6 ✔ Cron scheduling  

This is already **portfolio-level DevOps documentation**.

When you’re ready, send **Day 7** 🚀
```
