# Day 7 – AWS Learning Journey

## Objective
The objective of Day 7 was to optimize cloud resource usage by modifying an existing EC2 instance. This task focused on changing the instance type of a running EC2 instance to a smaller size based on utilization needs.

---

## AWS Services / Concepts Covered
- Amazon EC2
- EC2 instance lifecycle (running, stopped)
- Instance resizing
- Status checks
- Cost and resource optimization

---

## Steps I Took

1. Logged into the AWS Management Console using the provided temporary credentials.
2. Confirmed that the AWS region was set to **us-east-1 (N. Virginia)**.
3. Navigated to the **EC2** service and opened the **Instances** page.
4. Selected the EC2 instance named **devops-ec2**.
5. Verified that the instance status checks were fully completed (2/2 checks passed).
6. Stopped the EC2 instance, as instance type changes cannot be made while running.
7. After the instance entered the **stopped** state, changed the instance type from **t2.micro** to **t2.nano**.
8. Started the EC2 instance again.
9. Confirmed that the instance returned to the **running** state with the updated instance type.

---

## Issues Faced
- No issues were encountered while changing the instance type.

---

## Key Takeaways

- EC2 instances must be stopped before changing their instance type.
- Status checks should be completed before performing any instance modifications.
- Downsizing instance types can help optimize costs and resource usage.
- EC2 instances can be safely resized without data loss when done correctly.
- Understanding instance lifecycle states is essential for EC2 management.

---

## Conclusion
Day 7 focused on resource optimization by resizing an EC2 instance. This task demonstrated how AWS allows flexibility in scaling compute resources up or down based on workload requirements, which is a key practice in efficient cloud infrastructure management.

You’re now confidently managing and optimizing EC2 resources — this is real-world AWS work ☁️💪
