# Day 9 – Azure Learning Journey

## Objective
The objective of Day 9 was to attach an existing Network Interface (NIC) to an existing Azure Virtual Machine. This task focused on managing VM networking and ensuring proper attachment of network interfaces after VM initialization.

---

## Azure Services / Concepts Covered
- Azure Virtual Machines
- Network Interfaces (NIC)
- VM networking configuration
- VM lifecycle states (running, stopped)
- Portal-based resource management

---

## Steps I Took

1. Logged into the Azure Portal using the provided credentials.
2. Navigated to **Virtual machines** from the Azure search bar.
3. Selected the virtual machine named **datacenter-vm**.
4. Confirmed that the VM had completed initialization and was in a running state.
5. Stopped the virtual machine to allow network interface changes.
6. Opened the **Networking** section of the VM.
7. Attached the existing network interface named **datacenter-nic**.
8. Started the virtual machine after the NIC was attached.
9. Verified that the network interface status showed **Attached** and was associated with **datacenter-vm**.

---

## Issues Faced
- No issues were encountered while attaching the network interface.

---

## Key Takeaways

- Azure requires a virtual machine to be stopped before attaching additional network interfaces.
- Network Interfaces can be managed independently and attached to VMs when needed.
- VM lifecycle states must be respected when making configuration changes.
- Verifying attachment status ensures networking changes are applied correctly.
- Portal-based workflows provide clear visibility into networking configurations.

---

## Conclusion
Day 9 focused on Azure VM networking by attaching an existing network interface to a virtual machine. This task reinforced the importance of VM state management and demonstrated how Azure handles modular networking during cloud migrations.
