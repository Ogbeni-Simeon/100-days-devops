# Day 10 – Azure Learning Journey

## Objective
The objective of Day 10 was to attach an existing Public IP address to the Network Interface Card (NIC) of an existing Azure Virtual Machine. This task focused on configuring external connectivity for a VM by associating a static public IP.

---

## Azure Services / Concepts Covered
- Azure Virtual Machines
- Network Interfaces (NIC)
- Public IP addresses
- IP configurations
- Portal-based networking configuration

---

## Steps I Took

1. Logged into the Azure Portal using the provided credentials.
2. Navigated to **Virtual machines** using the Azure search bar.
3. Selected the virtual machine named **datacenter-vm-pip**.
4. Opened the **Networking** section of the VM.
5. Clicked on the attached Network Interface to open its settings.
6. Navigated to **IP configurations** for the NIC.
7. Edited the existing IP configuration.
8. Associated the Public IP address named **datacenter-pip** with the NIC.
9. Saved the configuration and waited for the update to complete.
10. Verified that the VM now displayed the assigned Public IP address.

---

## Issues Faced
- No issues were encountered while attaching the Public IP address.

---

## Key Takeaways

- Public IP addresses in Azure are associated with Network Interfaces, not directly with VMs.
- IP configuration changes are managed at the NIC level.
- Saving the configuration is required for changes to take effect.
- Verifying the association from both the VM and Public IP resource ensures correctness.
- Separating networking components improves flexibility and control.

---

## Conclusion
Day 10 focused on enabling external connectivity for an Azure Virtual Machine by attaching an existing Public IP address to its network interface. This task reinforced Azure’s networking model and completed the setup required for public access to the VM.
