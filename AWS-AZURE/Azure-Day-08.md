# Day 8 – Azure Learning Journey

## Objective
The objective of Day 8 was to attach an existing managed data disk to an existing Azure Virtual Machine. This task focused on managing Azure storage and correctly associating data disks with running virtual machines.

---

## Azure Services / Concepts Covered
- Azure Virtual Machines
- Azure Managed Disks
- Data disk attachment
- VM initialization and state checks
- Portal-based resource management

---

## Steps I Took

1. Logged into the Azure Portal using the provided credentials.
2. Navigated to **Virtual machines** using the Azure search bar.
3. Selected the virtual machine named **datacenter-vm**.
4. Confirmed that the VM was in a **running** state and fully initialized.
5. Opened the **Disks** section from the VM’s settings menu.
6. Under **Data disks**, clicked **Add data disk**.
7. Selected the existing managed disk named **datacenter-disk**.
8. Left the LUN and other disk settings as default.
9. Saved the configuration to apply the changes.
10. Verified that the disk was successfully attached to the VM.

---

## Issues Faced
- No issues were encountered while attaching the managed data disk.

---

## Key Takeaways

- Azure allows managed disks to be created and attached independently of virtual machines.
- Data disks must be attached only after the VM has completed initialization.
- Changes to VM disk configuration must be explicitly saved.
- Proper disk attachment is essential for extending VM storage capacity.
- Verifying disk attachment ensures the configuration is applied correctly.

---

## Conclusion
Day 8 focused on managing Azure storage by attaching an existing managed data disk to a virtual machine. This task reinforced how Azure separates compute and storage resources and highlighted best practices for safely modifying VM configurations during a cloud migration.
