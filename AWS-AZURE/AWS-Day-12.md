# Day 12 – AWS Learning Journey

## Objective
The objective of Day 12 was to attach an existing EBS volume to an existing EC2 instance and ensure it was attached using a specific device name. This task focused on managing persistent storage and associating it correctly with compute resources.

---

## AWS Services / Concepts Covered
- Amazon EC2
- Amazon EBS (Elastic Block Store)
- Volume attachment
- Device naming in Linux-based EC2 instances
- AWS Management Console

---

## Steps I Took

1. Logged into the AWS Management Console using the provided temporary credentials.
2. Verified that the AWS region was set to **us-east-1 (N. Virginia)**.
3. Navigated to the **EC2** service from the AWS console.
4. Opened the **Instances** section and confirmed the EC2 instance named **datacenter-ec2** existed.
5. Navigated to **Volumes** under the *Elastic Block Store* section.
6. Selected the volume named **datacenter-volume** and confirmed its status was **Available**.
7. Used the **Attach volume** action.
8. Selected the EC2 instance **datacenter-ec2** as the target.
9. Set the device name explicitly to **/dev/sdb**.
10. Completed the attachment and verified the volume status changed to **In-use**.

---

## Issues Faced
- No issues were encountered while attaching the EBS volume.

---

## Key Takeaways

- EBS volumes can be created independently and attached to EC2 instances when needed.
- The device name must be specified correctly when attaching volumes.
- After attachment, the volume status changes from **Available** to **In-use**.
- Storage and compute resources are managed separately in AWS.
- Verifying attachment details is important before considering the task complete.

---

## Conclusion
Day 12 focused on managing AWS storage by attaching an existing EBS volume to an EC2 instance with a specific device name. This task reinforced the relationship between EC2 instances and EBS volumes and highlighted the importance of correct configuration during cloud migrations.
