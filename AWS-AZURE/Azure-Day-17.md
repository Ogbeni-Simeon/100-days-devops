# Day 17 – Azure Learning Journey

## Objective
The objective of Day 17 was to create an Azure Storage Account and configure a public Blob container that allows anonymous read access for both containers and blobs.

---

## Azure Services / Concepts Covered
- Azure Storage Accounts
- Azure Blob Storage
- Blob Containers
- Public vs Private access levels
- Anonymous access configuration

---

## Steps I Took

1. Logged into the Azure Portal using the provided credentials.
2. Navigated to **Storage accounts** via the Azure search bar.
3. Clicked **Create** to provision a new storage account.
4. Entered the required details:
   - Storage account name: **nautilusst7390**
   - Performance: Standard
   - Redundancy: LRS
   - Used the existing resource group and appropriate region.
5. Created the storage account and waited for deployment to complete.
6. Opened the storage account and navigated to **Settings → Configuration**.
7. Enabled **Allow Blob public access** and saved the changes.
8. Navigated to **Data storage → Containers**.
9. Created a new Blob container with:
   - Container name: **nautilus-blob-16498**
   - Public access level: **Blob (anonymous read access for containers and blobs)**
10. Verified that the container was publicly accessible.

---

## Issues Faced
- No issues were encountered during the task.

---

## Key Takeaways

- Azure disables public Blob access by default for security reasons.
- Public containers require enabling public access at the storage account level.
- The **Blob** access level allows anonymous read access to both containers and blobs.
- Storage account names must be globally unique.
- Public Blob storage is useful for hosting static content.

---

## Conclusion
Day 17 focused on configuring Azure Blob Storage for public access. This task reinforced how Azure balances security and accessibility and demonstrated how to intentionally expose data when required for application or migration needs.
