# Day 13 – AWS Learning Journey

## Objective
The objective of Day 13 was to create an Amazon Machine Image (AMI) from an existing EC2 instance. This task focused on capturing the configuration and state of an EC2 instance so it can be reused for backups, scaling, or future deployments.

---

## AWS Services / Concepts Covered
- Amazon EC2
- Amazon Machine Images (AMI)
- EC2 snapshots
- Instance imaging
- Resource state validation

---

## Steps I Took

1. Logged into the AWS Management Console using the provided credentials.
2. Verified that the AWS region was set to **us-east-1 (N. Virginia)**.
3. Navigated to the **EC2** service.
4. Opened the **Instances** section and selected the instance named **devops-ec2**.
5. Used **Actions → Image and templates → Create image** to begin AMI creation.
6. Set the image name to **devops-ec2-ami**.
7. Created the image and monitored the AMI status.
8. Waited for the AMI state to transition from **Pending** to **Available**.
9. Verified that the AMI was successfully created and available for use.

---

## Issues Faced
- The AMI initially appeared in a **Pending** state, which is expected while AWS completes snapshot and registration processes.
- No errors occurred once the AMI reached the **Available** state.

---

## Key Takeaways

- AMI creation is an asynchronous process.
- An AMI must be in the **Available** state before it can be used or considered complete.
- AMIs capture the instance’s root volume configuration.
- Creating AMIs is useful for backups, scaling, and disaster recovery.
- Always verify resource states after creation.

---

## Conclusion
Day 13 focused on creating an Amazon Machine Image from an existing EC2 instance. This task reinforced the importance of understanding AWS resource lifecycle states and highlighted how AMIs are used to standardize and replicate EC2 environments.
