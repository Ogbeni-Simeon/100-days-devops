# Day 3 – Azure Learning Journey

## Objective
The objective of Day 3 was to create a new Azure Virtual Machine using the Azure CLI (without access to the Azure Portal). The VM needed to meet specific requirements around image, size, storage, and authentication, and it had to be in a running state after creation.

---

## Azure Services / Concepts Covered
- Azure Virtual Machines (CLI-based provisioning)
- Azure CLI (`az vm create`)
- Managed OS disks
- Azure Policy restrictions
- Resource cleanup (failed deployments)
- SSH key–based authentication

---

## Initial Approach and Issues Faced

I started by attempting to create the VM directly using the Azure CLI with all required parameters such as VM size, image, disk size, and storage settings.

However, multiple issues were encountered:

1. Disk SKU and storage configuration errors due to unsupported or restricted CLI flags.
2. Azure Policy restrictions that disallowed certain disk configurations.
3. Partial resource creation where failed deployments left behind managed OS disks, causing repeated failures.

---

## Key Realization
The main blocker was an existing, partially created OS disk from earlier failed attempts. Azure does not allow changing the storage account type of an existing managed disk, so cleanup was required before retrying.

---

## Corrective Actions Taken

### Cleanup of Failed Resources
- The failed VM was deleted.
- The leftover managed OS disk associated with the VM was also deleted.
- This ensured there were no conflicts during a fresh deployment.

---

## Final Working Solution

```bash
az vm create \
  --resource-group kml_rg_main-b686ce78a29f4097 \
  --name devops-vm \
  --image Ubuntu2204 \
  --size Standard_B2s \
  --admin-username azureuser \
  --generate-ssh-keys \
  --storage-sku Standard_LRS \
  --os-disk-size-gb 30
````

This command succeeded because:

* The VM name matched the task exactly.
* Ubuntu 22.04 was used as required.
* The VM size was correctly set.
* SSH keys were generated automatically.
* The disk size and storage type complied with Azure Policy.
* No conflicting resources existed.

---

## Verification Steps

### Verify VM Power State

```bash
az vm show \
  --resource-group kml_rg_main-b686ce78a29f4097 \
  --name devops-vm \
  --show-details \
  --output table
```

The `PowerState` column confirmed:

```
VM running
```

### Detailed Instance View

```bash
az vm get-instance-view \
  --resource-group kml_rg_main-b686ce78a29f4097 \
  --name devops-vm \
  --query instanceView.statuses \
  --output table
```

---

## Key Takeaways

* Azure CLI behavior can vary by environment and version.
* Azure Policies can block otherwise valid configurations.
* Failed deployments often leave behind orphaned resources.
* Resource cleanup is essential before retrying deployments.
* Lab environments often require strict adherence to defaults and naming.

---

## Conclusion

Day 3 provided hands-on experience with real-world Azure troubleshooting. Beyond VM creation, it highlighted Azure Policy enforcement, CLI limitations, and the importance of cleaning up failed resources before retrying deployments.
