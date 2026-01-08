# Day 3 – AWS Learning Journey

## Objective
The objective of Day 3 was to understand how AWS networking is structured by creating a subnet inside a Virtual Private Cloud (VPC). This task introduced how AWS divides a VPC into smaller network segments to better organize and control resources.

---

## AWS Services / Concepts Covered
- Amazon VPC
- Subnets
- Default VPC
- CIDR blocks
- Availability Zones

---

## Steps I Took

1. Logged into the AWS Management Console using the provided temporary credentials.
2. Confirmed that the active region was **us-east-1 (N. Virginia)**.
3. Navigated to the **VPC** service from the AWS console.
4. Selected **Subnets** from the VPC dashboard.
5. Clicked on **Create subnet**.
6. Selected the **default VPC** as the target VPC.
7. Entered the subnet name as **devops-subnet**.
8. Chose an Availability Zone within us-east-1.
9. Selected an available IPv4 CIDR block that did not overlap with existing subnets.
10. Created the subnet and verified that its status was marked as available.

---

## Issues Faced
- No issues were encountered during the subnet creation process.

---

## Key Takeaways

- A VPC is a logically isolated network in AWS.
- Subnets divide a VPC into smaller, manageable network segments.
- Each subnet belongs to a single Availability Zone.
- CIDR blocks define the IP address range for a subnet.
- Proper subnet planning is important for scalable cloud architectures.

---

## Conclusion
Day 3 focused on AWS networking fundamentals by creating a subnet within the default VPC. This step is crucial for organizing cloud resources and lays the foundation for deploying EC2 instances and other services in a structured network environment.
