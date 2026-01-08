# Day 2 – AWS Learning Journey

## Objective
The objective of Day 2 was to understand how AWS controls network access to resources by creating a security group. This task focused on defining inbound traffic rules that determine which services are allowed to reach application servers running in AWS.

---

## Scenario Overview
As part of the Nautilus DevOps team’s gradual migration to AWS, infrastructure components are being created step by step. Security is a critical part of this migration, and security groups are used to control access to cloud resources in a secure and manageable way.

---

## AWS Services / Concepts Covered
- EC2 Security Groups
- Default VPC
- Inbound and outbound traffic rules
- Network-level security in AWS

---

## Steps I Took

1. Logged into the AWS Management Console using the provided temporary credentials.
2. Verified that the active AWS region was **us-east-1 (N. Virginia)** to ensure compliance with task requirements.
3. Navigated to the **EC2** service from the AWS console.
4. Selected **Security Groups** from the *Network & Security* section in the EC2 dashboard.
5. Clicked on **Create security group**.
6. Entered the security group name as **datacenter-sg**.
7. Added the description **Security group for Nautilus App Servers**.
8. Ensured the security group was created under the **default VPC**.
9. Added an inbound rule to allow **HTTP traffic on port 80** from **0.0.0.0/0**.
10. Added another inbound rule to allow **SSH access on port 22** from **0.0.0.0/0**.
11. Left outbound rules as default (allow all traffic).
12. Created the security group and verified that the rules were correctly applied.

---

## Issues Faced
- No issues were encountered during the creation of the security group.

---

## Key Takeaways

- Security groups act as virtual firewalls for AWS resources.
- Inbound rules control incoming traffic, while outbound rules control outgoing traffic.
- The default VPC is commonly used for basic deployments and labs.
- Allowing SSH from `0.0.0.0/0` is convenient for labs but should be restricted in production.
- Correct region selection is critical when creating AWS resources.

---

## Conclusion
Day 2 focused on securing AWS infrastructure by defining controlled access through security groups. This task built on the foundational knowledge from Day 1 and introduced a key security concept that will be used repeatedly when deploying EC2 instances and applications in AWS.
You’re building this journey properly — step by step, just like real DevOps work ☁️💪
