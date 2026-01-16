# Day 15 – Azure Learning Journey

## Objective
The objective of Day 15 was to create a Network Security Group (NSG) in Azure and configure inbound security rules to allow HTTP and SSH traffic. This task focused on controlling network access to Azure resources using security rules.

---

## Azure Services / Concepts Covered
- Azure Network Security Groups (NSG)
- Inbound security rules
- Port-based traffic filtering
- CIDR notation
- Network access control

---

## Steps I Took

1. Logged into the Azure Portal using the provided credentials.
2. Navigated to **Network security groups** via the Azure search bar.
3. Created a new Network Security Group named **datacenter-nsg**.
4. Selected the existing resource group and appropriate region.
5. Opened the newly created NSG.
6. Added an inbound security rule named **Allow-HTTP**:
   - Protocol: TCP  
   - Port: 80  
   - Source: `0.0.0.0/0`  
   - Action: Allow
7. Added another inbound security rule named **Allow-SSH**:
   - Protocol: TCP  
   - Port: 22  
   - Source: `0.0.0.0/0`  
   - Action: Allow
8. Verified that both inbound rules were successfully created.

---

## Issues Faced
- No issues were encountered while creating the Network Security Group or its rules.

---

## Key Takeaways

- Network Security Groups act as virtual firewalls in Azure.
- Inbound rules control traffic entering Azure resources.
- Rule priorities determine the order in which traffic is evaluated.
- CIDR `0.0.0.0/0` allows traffic from any IPv4 address.
- NSGs can be reused and associated with subnets or network interfaces.

---

## Conclusion
Day 15 focused on implementing network-level security in Azure by creating and configuring a Network Security Group. This task reinforced how Azure controls inbound traffic and highlighted best practices for allowing only necessary services such as HTTP and SSH.
