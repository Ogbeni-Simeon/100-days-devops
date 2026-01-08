# Day 4 – AWS Learning Journey

## Objective
The objective of Day 4 was to learn how to allocate a static public IP address in AWS by creating an Elastic IP (EIP). This task helps in understanding how AWS manages public IP addresses for cloud resources.

---

## AWS Services / Concepts Covered
- EC2 Elastic IPs
- Public IPv4 addressing
- Resource tagging
- Network management in AWS

---

## Steps I Took

1. Logged into the AWS Management Console using the provided temporary credentials.
2. Verified that the AWS region was set to **us-east-1 (N. Virginia)**.
3. Navigated to the **EC2** service from the AWS console.
4. Selected **Elastic IPs** from the *Network & Security* section.
5. Clicked on **Allocate Elastic IP address**.
6. Accepted the default settings and allocated a new Elastic IP.
7. Selected the newly created Elastic IP.
8. Added a tag with:
   - Key: `Name`
   - Value: `devops-eip`
9. Saved the tag and confirmed the Elastic IP was successfully created and named.

---

## Issues Faced
- No issues were encountered during the allocation of the Elastic IP.

---

## Key Takeaways

- Elastic IPs provide a static public IPv4 address in AWS.
- Elastic IPs are region-specific and must be created in the correct region.
- Naming AWS resources is done using tags, not direct name fields.
- Elastic IPs are commonly used to maintain consistent public access to EC2 instances.
- Unused Elastic IPs may incur charges, so they should be managed carefully.

---

## Conclusion
Day 4 focused on understanding how AWS handles public IP addressing through Elastic IPs. This task is an important networking concept and prepares the foundation for attaching static IPs to EC2 instances in future deployment steps.
