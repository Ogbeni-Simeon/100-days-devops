# Day 8 – AWS Learning Journey

## Objective
The objective of Day 8 was to protect an existing EC2 instance from accidental shutdown by enabling stop protection. This task focused on applying safeguards to running compute resources during an ongoing migration.

---

## AWS Services / Concepts Covered
- Amazon EC2
- Stop protection
- Instance configuration settings
- Resource safety and governance

---

## Steps I Took

1. Logged into the AWS Management Console using the provided temporary credentials.
2. Verified that the AWS region was set to **us-east-1 (N. Virginia)**.
3. Navigated to the **EC2** service and opened the **Instances** page.
4. Selected the EC2 instance named **devops-ec2**.
5. Opened the instance settings menu.
6. Enabled **stop protection** for the selected instance.
7. Saved the configuration changes.
8. Verified in the instance details that stop protection was enabled.

---

## Issues Faced
- No issues were encountered while enabling stop protection.

---

## Key Takeaways

- Stop protection helps prevent accidental stopping of critical EC2 instances.
- This feature is useful during migrations and production operations.
- Stop protection is different from termination protection.
- Instance-level safeguards improve infrastructure reliability.
- AWS provides built-in controls to reduce operational risk.

---

## Conclusion
Day 8 focused on improving operational safety by enabling stop protection on an EC2 instance. This task highlighted the importance of protecting critical resources during cloud migrations and ongoing infrastructure changes.
