# AWS Learning Summary (Days 1–10)

## Overview
During Days 1–10, the focus was on building foundational AWS skills by creating, configuring, and managing core infrastructure components. Tasks were performed incrementally to mirror real-world DevOps and cloud migration practices.

---

## Core AWS Services Learned
- Amazon EC2
- Elastic IP (EIP)
- Elastic Block Store (EBS)
- Elastic Network Interface (ENI)
- AWS Key Pairs
- Security Groups
- Subnets and VPC concepts

---

## Key Skills and Concepts Learned

### 1. Identity and Access Foundations
- Created EC2 key pairs using RSA encryption.
- Understood the role of key pairs for secure SSH access.

---

### 2. Networking Fundamentals
- Created and managed security groups.
- Configured inbound rules for HTTP (port 80) and SSH (port 22).
- Learned how Elastic IPs provide static public IP addresses.
- Attached Elastic IPs to EC2 instances for stable connectivity.
- Attached Elastic Network Interfaces (ENIs) to EC2 instances.
- Understood instance initialization requirements before networking changes.

---

### 3. Compute Management
- Launched EC2 instances with specific AMIs and instance types.
- Changed EC2 instance types to optimize resource usage.
- Learned how to safely stop, modify, and restart instances.
- Enabled stop protection and termination protection for critical instances.

---

### 4. Storage Management
- Created EBS volumes with specific size and type requirements.
- Attached EBS volumes to EC2 instances using explicit device names.
- Understood volume states (Available vs In-use).

---

### 5. Resource Protection and Governance
- Enabled termination protection to prevent accidental deletion.
- Enabled stop protection to prevent unintended downtime.
- Learned the importance of safeguarding production resources.

---

## Key DevOps Takeaways
- AWS resources are modular and can be created independently.
- Proper sequencing (instance readiness before attachment) is critical.
- Networking, compute, and storage are managed as separate components.
- Naming consistency and region awareness are essential.
- AWS Console workflows reinforce understanding of cloud architecture.

---

## Summary
By Day 10, a strong foundation was built in AWS core services, covering compute, networking, storage, and resource protection. These skills form the baseline for advanced AWS operations, automation, and DevOps workflows.
