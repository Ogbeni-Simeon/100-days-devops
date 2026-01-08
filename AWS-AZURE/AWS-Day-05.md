# Day 5 – AWS Learning Journey

## Objective
The objective of Day 5 was to learn how to create persistent storage in AWS by provisioning an Elastic Block Store (EBS) volume. This task introduced how AWS provides block-level storage that can be attached to EC2 instances.

---

## AWS Services / Concepts Covered
- Amazon EBS (Elastic Block Store)
- EBS volume types
- Persistent block storage
- Resource tagging
- Availability Zones

---

## Steps I Took

1. Logged into the AWS Management Console using the provided temporary credentials.
2. Verified that the active AWS region was **us-east-1 (N. Virginia)**.
3. Navigated to the **EC2** service from the AWS console.
4. Selected **Volumes** under the *Elastic Block Store* section.
5. Clicked on **Create volume**.
6. Set the volume type to **gp3**.
7. Set the volume size to **2 GiB**.
8. Selected an Availability Zone within the us-east-1 region.
9. Left IOPS, throughput, and encryption settings at their default values.
10. Added a tag with:
    - Key: `Name`
    - Value: `xfusion-volume`
11. Created the volume and verified that its state was **Available**.

---

## Issues Faced
- No issues were encountered while creating the EBS volume.

---

## Key Takeaways

- EBS volumes provide persistent storage for EC2 instances.
- gp3 is a modern, cost-effective EBS volume type.
- EBS volumes are created within a specific Availability Zone.
- AWS resources are commonly identified and organized using tags.
- Storage resources can be created independently and attached later when needed.

---

## Conclusion
Day 5 focused on introducing AWS storage fundamentals by creating an EBS volume. This step is essential for supporting applications that require reliable and persistent disk storage in the cloud and prepares the groundwork for attaching storage to EC2 instances in future tasks.
