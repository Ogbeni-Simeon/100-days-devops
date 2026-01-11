# Day 6 – Azure Learning Journey

## Objective
The objective of Day 6 was to create an Azure Virtual Network (VNet) along with a subnet using the Azure Portal. This task focused on setting up basic networking components required to support Azure workloads.

---

## Azure Services / Concepts Covered
- Azure Virtual Networks (VNet)
- Subnets
- IPv4 CIDR addressing
- Azure regions
- Portal-based networking configuration

---

## Steps I Took

1. Logged into the Azure Portal using the provided credentials.
2. Navigated to **Virtual networks** via the Azure search bar.
3. Clicked on **Create** to start creating a new Virtual Network.
4. Selected the existing resource group.
5. Set the VNet name to **xfusion-vnet**.
6. Chose **East US** as the deployment region.
7. Configured the IPv4 address space as **10.0.0.0/16**.
8. Created a subnet named **xfusion-subnet** within the VNet.
9. Assigned a valid subnet CIDR range within the VNet address space.
10. Reviewed the configuration and created the Virtual Network.
11. Verified that both the VNet and subnet were created successfully.

---

## Issues Faced
- No issues were encountered during the creation of the Virtual Network and subnet.

---

## Key Takeaways

- Virtual Networks are the foundation of Azure networking.
- Subnets help segment a VNet into smaller, manageable network ranges.
- CIDR blocks define IP address allocation and must be planned carefully.
- Subnet ranges must fall within the VNet address space.
- Azure Portal provides a guided and user-friendly way to configure networking.

---

## Conclusion
Day 6 focused on Azure networking fundamentals by creating a Virtual Network and a subnet. This task reinforced the importance of proper network planning and prepared the environment for deploying and connecting Azure resources during the migration process.
