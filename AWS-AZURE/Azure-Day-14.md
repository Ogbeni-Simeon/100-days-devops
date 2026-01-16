# Day 14 – Azure Learning Journey

## Objective
The objective of Day 14 was to create a managed disk in Azure with specific storage and size requirements. This task focused on understanding Azure managed disks and storage redundancy options.

---

## Azure Services / Concepts Covered
- Azure Managed Disks
- Disk SKUs and performance tiers
- Azure storage redundancy options
- Portal-based storage provisioning
- Resource management

---

## Steps I Took

1. Logged into the Azure Portal using the provided credentials.
2. Used the Azure search bar to navigate to **Disks**.
3. Clicked **Create** to start creating a new managed disk.
4. Selected the existing resource group.
5. Set the disk name to **xfusion-disk**.
6. Chose the appropriate region (same as the resource group).
7. Selected **None (empty disk)** as the source type.
8. Set the disk size to **2 GiB**.
9. Selected the disk type as **Standard HDD (Standard_LRS)**.
10. Reviewed the configuration and created the disk.
11. Verified that the disk was created successfully and remained unattached.

---

## Issues Faced
- No issues were encountered during disk creation.

---

## What Does LRS Mean?

**LRS** stands for **Locally Redundant Storage**.

- It means Azure stores **multiple copies of the data within a single datacenter** in the same region.
- Typically, **three copies** of the data are maintained.
- LRS protects against **local hardware failures** such as disk or server issues.
- It does **not** protect against datacenter-wide outages.

**Why LRS is used here:**
- It is cost-effective.
- Suitable for development, testing, and non-critical workloads.
- Commonly used for basic managed disks unless higher availability is required.

---

## Key Takeaways

- Managed disks are standalone Azure storage resources.
- Disk size and type must match exact task requirements.
- **Standard_LRS** provides local redundancy at a lower cost.
- Disks do not need to be attached to a VM immediately after creation.
- Proper verification ensures the disk is ready for future use.

---

## Conclusion
Day 14 focused on creating an Azure managed disk with a specific redundancy and size configuration. This task reinforced the importance of understanding Azure storage options, especially redundancy types like **LRS**, and prepared the environment for future VM storage expansion.
