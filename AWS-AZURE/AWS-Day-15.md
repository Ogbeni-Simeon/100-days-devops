# Day 15 – AWS Learning Journey

## Objective
The objective of Day 15 was to create a snapshot of an existing Amazon EBS volume. This task focused on understanding how AWS handles volume backups and how snapshots are used for data protection and recovery.

---

## AWS Services / Concepts Covered
- Amazon Elastic Block Store (EBS)
- EBS Volumes
- EBS Snapshots
- AWS resource tagging
- Snapshot lifecycle and status 

---

## Steps I Took

1. Logged into the AWS Management Console using the provided credentials.
2. Confirmed the region was set to **us-east-1 (N. Virginia)**.
3. Navigated to **EC2** from the AWS services menu.
4. Opened **Volumes** under the **Elastic Block Store** section.
5. Identified the correct source volume (**xfusion-vol**) as required by the environment.
6. Selected the volume and chose **Actions → Create snapshot**.
7. Entered the snapshot details:
   - **Description:** `devops Snapshot`
8. Added a tag to define the snapshot name:
   - **Key:** `Name`
   - **Value:** `devops-vol-ss`
9. Created the snapshot.
10. Navigated to **Snapshots** in the EC2 console.
11. Waited until the snapshot status changed from **Pending** to **Completed**.
12. Verified that the snapshot was created from the correct volume and had the expected name and description.

---

## Issues Faced and How They Were Resolved

- **Initial snapshot created from the wrong volume**  
  The lab validation expected the snapshot to be created from a specific volume (`xfusion-vol`). After carefully checking the volume names and recreating the snapshot from the correct source volume, the issue was resolved.

- **Confusion around snapshot naming**  
  AWS does not provide a direct “Name” field for snapshots. Instead, the snapshot name is set using a **Name tag**, which was applied correctly.

---

## Key Takeaways

- EBS snapshots are **incremental**, capturing only changed data after the first snapshot.
- Snapshot creation is asynchronous; the status must be **Completed** before use.
- Snapshot “names” in AWS are implemented using **resource tags**.
- Always verify the **source volume** when creating backups.
- Paying attention to validation error messages helps quickly identify misconfigurations.

---

## Conclusion
Day 15 reinforced the importance of backups in AWS by creating an EBS snapshot from an existing volume. This task highlighted how AWS manages snapshots, the role of tagging for identification, and the need to verify snapshot completion and source correctness before relying on them for recovery or automation.
