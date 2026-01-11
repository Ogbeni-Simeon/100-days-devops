# Azure Learning Summary (Days 1–10)

## Overview
During Days 1–10, the learning journey focused on understanding Azure core services through both Azure Portal and Azure CLI. The tasks simulated real enterprise cloud migrations with strict policies, resource governance, and incremental changes.

---

## Core Azure Services Learned
- Azure Virtual Machines
- Azure Virtual Networks (VNet)
- Subnets
- Public IP Addresses
- Network Interfaces (NIC)
- Managed Disks
- Azure Resource Groups
- Azure Tags

---

## Key Skills and Concepts Learned

### 1. Secure Access and Authentication
- Created SSH key pairs for Linux VM access.
- Used SSH keys as the primary authentication mechanism.
- Worked in both portal-based and CLI-only environments.

---

### 2. Virtual Machine Management
- Created Linux VMs using Azure Portal and Azure CLI.
- Selected VM images (Ubuntu 22.04) and VM sizes.
- Resized VMs to optimize resource utilization.
- Managed VM lifecycle states (start, stop, deallocate).

---

### 3. Networking Fundamentals
- Created Virtual Networks (VNets) with custom CIDR ranges.
- Created subnets within VNets.
- Allocated and managed Public IP addresses.
- Attached Public IPs to NICs rather than directly to VMs.
- Attached additional NICs to VMs (requiring VM stop/start).

---

### 4. Storage Management
- Attached managed data disks to Azure VMs.
- Understood the difference between OS disks and data disks.
- Learned Azure Policy restrictions on disk types and sizes.
- Handled failed deployments by cleaning up orphaned resources.

---

### 5. Governance and Organization
- Used resource groups to organize Azure resources.
- Applied tags (e.g., Environment=dev) for governance.
- Learned how tags support cost management and policy enforcement.

---

### 6. Real-World Troubleshooting Lessons
- Azure Policies can block valid-looking configurations.
- Failed deployments may leave resources that must be cleaned up.
- Default configurations often satisfy strict lab or enterprise policies.
- CLI behavior may vary depending on environment and version.
- Reading and interpreting Azure error messages is critical.

---

## Key DevOps Takeaways
- Azure networking is NIC-centric, not VM-centric.
- Many infrastructure changes require VM state awareness.
- Azure enforces stronger governance through policies.
- Cleanup and validation are essential parts of troubleshooting.
- Portal and CLI skills are both necessary for real-world Azure work.

---

## Summary
By Day 10, a solid foundation was established in Azure core services, networking, storage, VM management, and governance. The experience closely mirrored real enterprise Azure environments and strengthened practical DevOps troubleshooting and cloud engineering skills.
