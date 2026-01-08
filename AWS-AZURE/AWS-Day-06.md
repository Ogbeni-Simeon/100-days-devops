# Day 6 – AWS Learning Journey

## Objective
The objective of Day 6 was to launch an EC2 instance in AWS. This task brought together multiple foundational concepts such as compute, security, key pairs, and networking into a single hands-on activity.

---

## AWS Services / Concepts Covered
- Amazon EC2
- Amazon Linux AMI
- EC2 instance types
- Key pairs for secure access
- Default VPC and security group

---

## Steps I Took

1. Logged into the AWS Management Console using the provided temporary credentials.
2. Verified that the AWS region was set to **us-east-1 (N. Virginia)**.
3. Navigated to the **EC2** service from the AWS console.
4. Clicked on **Launch instance** to begin instance creation.
5. Set the instance name to **devops-ec2**.
6. Selected **Amazon Linux** as the operating system image.
7. Chose **t2.micro** as the instance type.
8. Created a new RSA key pair named **devops-kp** and downloaded the private key file.
9. Used the **default security group** and default VPC for networking.
10. Left storage settings as default.
11. Launched the instance and confirmed that it entered the **running** state.

---

## Issues Faced
- No issues were encountered while launching the EC2 instance.

---

## Key Takeaways

- EC2 instances provide scalable compute power in AWS.
- Instance types define the CPU and memory resources available.
- Key pairs are required for secure SSH access to Linux instances.
- Default VPC and security groups simplify initial deployments.
- Combining compute, networking, and security is central to AWS infrastructure.

---

## Conclusion
Day 6 marked a major milestone by launching the first EC2 instance. This task combined several AWS fundamentals and demonstrated how individual cloud components work together to support real-world workloads.
