# Day 2 – Azure Learning Journey

## Objective
The objective of Day 2 was to create an Azure Virtual Machine (VM) with specific compute, network, and storage configurations, and to verify secure access to the VM using SSH.

---

## Azure Services / Concepts Covered
- Azure Virtual Machines
- Ubuntu Linux images
- Azure regions
- Network Security Groups (NSGs)
- OS disks and storage types
- SSH access to Azure VMs

---

## Steps I Took

1. Logged into the Azure Portal using the provided temporary credentials.
2. Navigated to the **Virtual Machines** service and started creating a new VM.
3. Selected the existing resource group for deployment.
4. Set the virtual machine name to **devops-vm**.
5. Chose **West US** as the deployment region.
6. Selected **Ubuntu Server 22.04 LTS** as the VM image.
7. Chose **Standard_B1s** as the VM size.
8. Configured authentication using an existing SSH public key.
9. Selected the previously created SSH key **nautilus-kp**.
10. Configured networking to use a default Network Security Group that allows inbound SSH on port 22.
11. Set the OS disk size to **30 GB** and selected **Standard HDD** as the disk type.
12. Left all remaining configuration options at their default values.
13. Reviewed the configuration and created the virtual machine.
14. Verified that the VM was running successfully.
15. Used SSH to connect to the VM using its public IP address.

---

## Issues Faced
- No issues were encountered during VM creation or SSH access.

---

## Key Takeaways

- Azure VMs can be created with fine-grained control over compute, networking, and storage.
- SSH is the primary method for securely accessing Linux virtual machines.
- Network Security Groups control inbound and outbound traffic at the network interface level.
- Disk type and size selection impact performance and cost.
- Verifying access after deployment is an essential validation step.

---

## Conclusion
Day 2 focused on deploying and accessing a Linux virtual machine in Azure. This task reinforced core Azure concepts and marked an important step toward running workloads securely in the Azure cloud as part of the migration process.

You’re now confidently deploying and accessing Azure compute resources — strong multi-cloud momentum ☁️💪
