# Day 11 – AWS Learning Journey

## Objective
The objective of Day 11 was to attach an existing Elastic Network Interface (ENI) to an existing EC2 instance. This task focused on advanced EC2 networking by managing and attaching additional network interfaces to a running instance.

---

## AWS Services / Concepts Covered
- Amazon EC2
- Elastic Network Interfaces (ENI)
- EC2 instance status checks
- Network interface attachment
- AWS Management Console

---

## Steps I Took

1. Logged into the AWS Management Console using the provided temporary credentials.
2. Verified that the AWS region was set to **us-east-1 (N. Virginia)**.
3. Navigated to the **EC2** service and opened the **Instances** page.
4. Selected the EC2 instance named **xfusion-ec2**.
5. Confirmed that the instance was in a **running** state and that **2/2 status checks** had passed.
6. Navigated to **Network Interfaces** under the *Network & Security* section.
7. Selected the network interface named **xfusion-eni** and confirmed its status was **Available**.
8. Used the **Attach** action to attach the ENI to the **xfusion-ec2** instance.
9. Left the device index as the default value.
10. Verified that the network interface status changed to **Attached**.

---

## Issues Faced
- No issues were encountered while attaching the network interface.

---

## Key Takeaways

- Elastic Network Interfaces can be created and managed independently of EC2 instances.
- An EC2 instance must finish initialization before attaching additional network interfaces.
- ENIs allow more flexible and advanced networking configurations.
- Verifying attachment status is essential before considering the task complete.
- Proper sequencing of actions helps avoid networking errors.

---

## Conclusion
Day 11 focused on advanced EC2 networking by attaching an Elastic Network Interface to a running instance. This task reinforced the importance of instance readiness checks and demonstrated how AWS allows modular management of networking components during cloud migrations.
