# Day 14 – AWS Learning Journey

## Objective
The objective of Day 14 was to delete an obsolete EC2 instance by terminating it completely. This task focused on proper resource cleanup and understanding EC2 instance lifecycle states.

---

## AWS Services / Concepts Covered
- Amazon EC2
- EC2 instance lifecycle
- Instance termination
- Resource cleanup and cost optimization
- AWS Management Console

---

## Steps I Took

1. Logged into the AWS Management Console using the provided credentials.
2. Verified that the AWS region was set to **us-east-1 (N. Virginia)**.
3. Navigated to the **EC2** service.
4. Opened the **Instances** section.
5. Located the EC2 instance named **nautilus-ec2**.
6. Carefully selected the correct instance to avoid accidental deletion.
7. Used **Instance state → Terminate instance** to delete the instance.
8. Confirmed the termination action when prompted.
9. Monitored the instance state until it changed to **Terminated**.

---

## Issues Faced
- No issues were encountered during the termination process.

---

## Key Takeaways

- Terminating an EC2 instance permanently deletes it.
- A **stopped** instance can be restarted, but a **terminated** instance cannot.
- Always double-check instance names before termination.
- Proper cleanup helps reduce costs and keeps the environment organized.
- Monitoring instance state is essential before confirming task completion.

---

## Conclusion
Day 14 focused on AWS resource cleanup by terminating an unused EC2 instance. This task reinforced the importance of managing instance lifecycles responsibly and highlighted best practices for maintaining a clean and cost-efficient AWS environment.
