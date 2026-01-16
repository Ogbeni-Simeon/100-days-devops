# Day 16 – Azure Learning Journey

## Objective
The objective of Day 16 was to create an Azure Storage Account and a private Blob container to support data storage needs during the ongoing infrastructure migration to Azure.

---

## Azure Services / Concepts Covered
- Azure Storage Accounts
- Azure Blob Storage
- Blob Containers
- Storage access levels
- Data security in Azure

---

## Steps I Took

1. Logged into the Azure Portal using the provided credentials.
2. Navigated to **Storage accounts** using the Azure search bar.
3. Clicked **Create** to provision a new storage account.
4. Filled in the required details:
   - Storage account name: **devopsst15012**
   - Performance: Standard
   - Redundancy: LRS
   - Used the existing resource group and default region.
5. Reviewed and created the storage account.
6. Opened the newly created storage account after deployment completed.
7. Navigated to **Data storage → Containers**.
8. Created a new Blob container with the following details:
   - Container name: **devops-blob-12916**
   - Public access level: **Private (no anonymous access)**
9. Verified that the container was successfully created and marked as private.

---

## Issues Faced
- No issues were encountered during the creation of the storage account or Blob container.

---

## Key Takeaways

- Azure Storage Accounts provide a scalable and secure foundation for data storage.
- Blob containers are used to store unstructured data such as files and backups.
- Setting the access level to **Private** ensures data is not publicly accessible.
- Storage account names must be globally unique across Azure.
- Proper storage configuration is essential during cloud migration projects.

---

## Conclusion
Day 16 focused on securely provisioning Azure storage resources by creating a storage account and a private Blob container. This task reinforced best practices around data security and storage management in Azure, which are critical components of a successful cloud migration.
