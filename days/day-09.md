# Day 09 – MariaDB Service Outage (Incident Analysis & Resolution)

## Overview
This document explains how a **MariaDB service outage** on the database server was investigated and resolved during **Day 9** of the *100 Days of DevOps Practice Challenge (KodeKloud)*.

Unlike previous days, this task involved **incident troubleshooting**, not configuration or installation.  
The focus was on **service lifecycle understanding**, not database administration.

---

## Problem Statement
The Nautilus application was unable to connect to its database.

After investigation, the production support team identified that:
- The **MariaDB service was down**
- The issue was on the **database server**

The task requirement was simple:
> Look into the issue and fix the same.

---

## Initial Observation
After logging into the database server and checking the service status:

```bash
sudo systemctl status mariadb
````

The output showed variations such as:

* `inactive (dead)`
* `failed (exit-code)`
* `status=0/SUCCESS`
* `MariaDB server is down`

These mixed signals caused initial confusion and led to multiple troubleshooting paths.

---

## Where the Confusion Came From

### 1. Misleading Error Messages

Some outputs suggested a failure:

```
Job for mariadb.service failed because the control process exited with error code
```

While others showed:

```
Main process exited, status=0/SUCCESS
```

This combination meant:

* MariaDB was **not crashing**
* It was **starting and then shutting down cleanly**

This is a key distinction in Linux service management.

---

### 2. Installation Assumption

At one point, it seemed possible that MariaDB was not installed correctly.

However:

* The service unit existed
* Binaries were present
* `systemctl` recognized the service

This ruled out installation issues.

---

### 3. Initialization Assumption

Running:

```bash
sudo mariadb-install-db --user=mysql --basedir=/usr --datadir=/var/lib/mysql
```

Returned:

```
mysql.user table already exists!
Run mysql_upgrade, not mysql_install_db
```

This confirmed:

* The database **was already initialized**
* System tables existed
* The issue was **not setup-related**

At this point, both **installation** and **initialization** were ruled out.

---

## Key Insight (Turning Point)

The critical realization was:

> MariaDB was **exiting cleanly**, not crashing.

This strongly indicates a **runtime state problem**, not corruption.

In Linux database services, the most common runtime blockers are:

* Stale **socket files**
* Stale **PID files**

These files can cause MariaDB to believe:

* Another instance is already running
* Or the runtime environment is inconsistent

As a result, MariaDB exits immediately.

---

## The Correct Fix (Final Working Solution)

The fix focused on **resetting MariaDB’s runtime state**, without touching data.

---

### Step 1 – Stop MariaDB Completely

```bash
sudo systemctl stop mariadb
```

This ensured no partial or orphaned process was holding runtime files.

---

### Step 2 – Remove Stale Runtime Files

```bash
sudo rm -f /var/lib/mysql/mysql.sock
sudo rm -f /var/run/mariadb/mariadb.pid
sudo rm -f /var/run/mysqld/mysqld.pid
```

#### Why this works:

* These files are **not data**
* They are recreated automatically on startup
* Stale versions can block the service from starting

---

### Step 3 – Ensure Correct Ownership (Safety Check)

```bash
sudo chown -R mysql:mysql /var/lib/mysql
```

This guarantees MariaDB can access its data directory.

---

### Step 4 – Start MariaDB Again

```bash
sudo systemctl start mariadb
```

---

### Step 5 – Verify Service Status

```bash
sudo systemctl status mariadb
```

Expected output:

```
Active: active (running)
```

At this point:

* MariaDB stayed running
* Database connectivity was restored
* The application issue was resolved

---

## Why Earlier Attempts Failed

| Attempt                    | Why It Did Not Work                  |
| -------------------------- | ------------------------------------ |
| Reinstalling MariaDB       | Service was already installed        |
| Initializing database      | Database was already initialized     |
| Repeated `systemctl start` | Stale runtime files blocked startup  |
| Log inspection alone       | Identified symptoms, not the cleanup |

The root cause was **runtime artifacts**, not broken software.

---

## Final Outcome

* MariaDB service restored
* Database server operational
* Application connectivity resolved
* Task completed successfully

---

## Key Lessons from Day 9

### 1. Service State Matters

Not all failures mean crashes.
A service that exits cleanly often indicates **environment or runtime state issues**.

---

### 2. Don’t Rebuild What Isn’t Broken

Reinstalling or reinitializing should be a **last resort**, not a first response.

---

### 3. Runtime Files Can Break Services

Stale PID and socket files are a common cause of database startup failures.

---

### 4. Production Support Is About Restoration

The goal is not perfection — it is **restoring service safely and quickly**.

---

## Personal Reflection

Day 9 was a turning point from “task execution” to **real troubleshooting**.

It reinforced:

* Calm, methodical debugging
* Eliminating assumptions with evidence
* Understanding Linux service behavior
You handled Day 9 like a real production engineer — well done 👏
```
