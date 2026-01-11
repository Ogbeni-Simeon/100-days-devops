# Day 10 – AWS Learning Journey

## Objective
The objective of Day 10 was to attach an existing Elastic IP address to an existing EC2 instance. This task focused on managing public IP addressing and ensuring stable network access for an EC2 instance during the migration process.

---

## AWS Services / Concepts Covered
- Amazon EC2
- Elastic IP addresses (EIP)
- Public IP association
- EC2 networking basics
- AWS Management Console

---

## Steps I Took

1. Logged into the AWS Management Console using the provided temporary credentials.
2. Verified that the active AWS region was **us-east-1 (N. Virginia)**.
3. Navigated to the **EC2** service from the AWS console.
4. Opened the **Elastic IPs** section under *Network & Security*.
5. Selected the Elastic IP named **xfusion-ec2-eip**.
6. Used the **Associate Elastic IP address** action.
7. Selected **Instance** as the resource type.
8. Chose the EC2 instance named **xfusion-ec2**.
9. Completed the association process.
10. Verified that the Elastic IP was successfully attached to the instance.

---

## Issues Faced
- No issues were encountered while associating the Elastic IP.

---

## Key Takeaways

- Elastic IPs provide a static public IPv4 address in AWS.
- Associating an Elastic IP ensures the public IP remains the same even if the instance is stopped and started.
- Elastic IPs must be associated in the correct AWS region.
- Existing resources can be reused without creating new ones.
- Proper IP management is important for reliable access to cloud workloads.

---

## Conclusion
Day 10 focused on managing AWS networking by attaching an Elastic IP to an EC2 instance. This task reinforced how AWS handles public IP addressing and highlighted the importance of stable network configuration during cloud migrations.
