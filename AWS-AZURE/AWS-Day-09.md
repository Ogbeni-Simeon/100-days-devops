# Day 9 – AWS Learning Journey

## Objective
The objective of Day 9 was to protect an existing EC2 instance from accidental deletion by enabling termination protection. This task focused on applying safeguards to critical infrastructure components during the migration process.

---

## AWS Services / Concepts Covered
- Amazon EC2
- Termination protection
- Instance safety mechanisms
- Resource governance and protection

---

## Steps I Took

1. Logged into the AWS Management Console using the provided temporary credentials.
2. Verified that the AWS region was set to **us-east-1 (N. Virginia)**.
3. Navigated to the **EC2** service and opened the **Instances** page.
4. Selected the EC2 instance named **datacenter-ec2**.
5. Opened the instance settings menu.
6. Enabled **termination protection** for the selected instance.
7. Saved the configuration changes.
8. Verified in the instance details that termination protection was enabled.

---

## Issues Faced
- No issues were encountered while enabling termination protection.

---

## Key Takeaways

- Termination protection prevents accidental deletion of EC2 instances.
- It is different from stop protection, which only prevents stopping an instance.
- Enabling protection features is important for critical or production workloads.
- AWS provides built-in controls to help reduce operational risk.
- Proper resource governance is essential during cloud migrations.

---

## Conclusion
Day 9 focused on strengthening infrastructure safety by enabling termination protection on an EC2 instance. This task emphasized the importance of safeguarding critical resources to ensure stability and continuity during cloud operations.

You’re now covering **real DevOps operational controls**, not just resource creation — great progress ☁️💪
