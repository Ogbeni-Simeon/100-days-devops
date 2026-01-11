# Day 11 – Azure Learning Journey

## Objective
The objective of Day 11 was to resize an existing Azure Virtual Machine to optimize resource usage. This task involved changing the VM size and ensuring the virtual machine was returned to a running state after the change.

---

## Azure Services / Concepts Covered
- Azure Virtual Machines
- VM sizing and scaling
- VM lifecycle management (stop, resize, start)
- Resource optimization
- Portal-based VM management

---

## Steps I Took

1. Logged into the Azure Portal using the provided credentials.
2. Navigated to **Virtual machines** using the Azure search bar.
3. Selected the virtual machine named **devops-vm**.
4. Stopped the virtual machine and waited until its status changed to **Stopped (deallocated)**.
5. Opened the **Size** configuration section for the VM.
6. Changed the VM size from **Standard_B1s** to **Standard_B2s**.
7. Applied the resize operation and waited for it to complete.
8. Started the virtual machine after the resize.
9. Verified that the VM status was **Running** and the new size was correctly applied.

---

## Issues Faced
- No issues were encountered during the resizing process.

---

## Key Takeaways

- Azure requires virtual machines to be stopped before resizing.
- VM sizes determine available CPU, memory, and performance characteristics.
- Resizing is a common method for optimizing cost and performance.
- Always verify both VM size and running state after changes.
- Proper VM lifecycle management is essential during infrastructure optimization.

---

## Conclusion
Day 11 focused on optimizing Azure compute resources by resizing an existing virtual machine. This task reinforced how Azure handles VM resizing and highlighted the importance of verifying VM state and configuration after making infrastructure changes.
