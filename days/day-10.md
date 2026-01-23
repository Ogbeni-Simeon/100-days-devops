# Day 10 – Automating Website Backup with Bash Script (Ecommerce)

## Overview
This document captures my experience designing and debugging a **bash backup automation script** on **App Server 1** as part of **Day 10** of the *100 Days of DevOps Practice Challenge (KodeKloud)*.

Unlike earlier days, this task involved:
- Writing a real bash script
- Handling SSH automation
- Debugging syntax errors
- Fixing environment issues
- Understanding how small mistakes break automation

This day was a major lesson in **practical scripting and troubleshooting**.

---

## Task Summary

On **App Server 1**, create a bash script named:

```

/scripts/ecommerce_backup.sh

```

The script must:

1. Create a zip archive:
   - Name: `xfusioncorp_ecommerce.zip`
   - Source: `/var/www/html/ecommerce`

2. Save the archive locally in:
```

/backup/

```

3. Copy the archive to the **Nautilus Backup Server**:
```

/backup/xfusioncorp_ecommerce.zip

````

4. Ensure:
- No password prompt during copy
- No `sudo` inside the script
- Script is executable by the server user

---

## Environment Context

| Component | Value |
|------|------|
| Server | App Server 1 |
| User | `tony` |
| Script Path | `/scripts/ecommerce_backup.sh` |
| Local Backup Dir | `/backup` |
| Source Dir | `/var/www/html/ecommerce` |
| Backup Server | `stbkp01.stratos.xfusioncorp.com` |
| Backup User | `clint` |

---

## Step 1 – Install Required Package (Outside Script)

```bash
sudo yum install -y zip
````

This satisfied the requirement that `zip` must be installed **outside the script**.

---

## Step 2 – Ensure Directories Exist

```bash
mkdir -p /scripts
mkdir -p /backup
```

---

## Step 3 – Configure Password-less SSH to Backup Server

Initially, SSH from App Server 1 to the backup server required a password.

This violated the task requirement:

> “script won't ask for password while copying the archive file”

### Actions taken:

1. Checked for existing SSH keys:

   ```bash
   ls ~/.ssh
   ```

2. Generated a key pair:

   ```bash
   ssh-keygen -t rsa -b 2048
   ```

   (All prompts accepted with Enter, no passphrase)

3. Copied the public key:

   ```bash
   ssh-copy-id clint@stbkp01.stratos.xfusioncorp.com
   ```

4. Verified:

   ```bash
   ssh clint@stbkp01.stratos.xfusioncorp.com
   ```

   Login worked **without password**.

This step was mandatory for the script to run unattended.

---

## Step 4 – Initial Script Creation Attempt (Problems Faced)

When attempting to create the script using `vi`, the terminal:

* Showed a blank screen
* Cursor blinked
* Did not accept input even after pressing `i`

This was a **terminal/editor issue**, not a scripting issue.

### Resolution

Instead of fighting the editor, the script was created using a **non-interactive here-document**:

```bash
cat > /scripts/ecommerce_backup.sh << 'EOF'
...script content...
EOF
```

This avoided all editor problems.

---

## Step 5 – Debugging Script Errors (Major Learning Point)

After viewing the initial script content:

```bash
cat /scripts/ecommerce_backup.sh
```

Several critical issues were discovered.

### ❌ Problem 1 – Missing Shebang

The script did not start with:

```bash
#!/bin/bash
```

Without this, the system may not execute the script correctly.

---

### ❌ Problem 2 – Invalid Variable Name

One variable was written as:

```bash
LOCAL_BACKUP DIR="/backup"
```

This contains a **space in the variable name**, which is **invalid in bash**.

This single mistake made the entire script syntactically broken.

---

### ❌ Problem 3 – Partial / Inconsistent Script Structure

* Missing standard formatting
* Risk of checker failure

These issues explained why the script would not run correctly.

---

## Step 6 – Final Correct Script

The file was completely overwritten with a clean, correct version:

```bash
#!/bin/bash

ZIP_NAME="xfusioncorp_ecommerce.zip"
SOURCE_DIR="/var/www/html/ecommerce"
LOCAL_BACKUP_DIR="/backup"
REMOTE_BACKUP_DIR="/backup"
REMOTE_SERVER="clint@stbkp01.stratos.xfusioncorp.com"

zip -r ${LOCAL_BACKUP_DIR}/${ZIP_NAME} ${SOURCE_DIR}

scp ${LOCAL_BACKUP_DIR}/${ZIP_NAME} ${REMOTE_SERVER}:${REMOTE_BACKUP_DIR}
```

This fixed:

* Shebang issue
* Variable naming issue
* Formatting issues
* Compliance with task requirements

---

## Step 7 – Make Script Executable

```bash
chmod +x /scripts/ecommerce_backup.sh
```

Verified:

```bash
ls -l /scripts/ecommerce_backup.sh
```

Expected:

```
-rwxr-xr-x
```

---

## Step 8 – Execute the Script

```bash
/scripts/ecommerce_backup.sh
```

Observed behavior:

* Zip archive created locally
* File copied to backup server
* No password prompt
* No sudo used

---

## Step 9 – Verification

### Local check:

```bash
ls -l /backup/xfusioncorp_ecommerce.zip
```

### Remote check:

```bash
ssh clint@stbkp01.stratos.xfusioncorp.com "ls -l /backup/xfusioncorp_ecommerce.zip"
```

File existed in both locations.

---

## Final Outcome

* Script created at correct location
* Archive created with correct name
* Local backup stored in `/backup`
* Remote backup copied to backup server
* Script runs without password
* Task completed successfully

---

## Key Problems Faced and Lessons Learned

| Problem                    | Lesson                                 |
| -------------------------- | -------------------------------------- |
| `vi` not accepting input   | Use non-interactive file creation      |
| Password prompt during scp | SSH keys are mandatory for automation  |
| Missing shebang            | Always declare interpreter             |
| Space in variable name     | Bash is very strict about syntax       |
| Script failing silently    | Always inspect file content with `cat` |

---

## Key Takeaways from Day 10

1. **Automation breaks on small mistakes**
   A single space in a variable name can break everything.

2. **Password-less SSH is foundational**
   Automation and passwords do not mix.

3. **Avoid fighting broken editors**
   Non-interactive methods are often more reliable.

4. **Always verify before running**
   `cat`, `ls -l`, and manual inspection are critical.

---

## Personal Reflection

* Writing real automation code
* Debugging syntax issues
* Handling environment problems
* Understanding how production scripts fail
