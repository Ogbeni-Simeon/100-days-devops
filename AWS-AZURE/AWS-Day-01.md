# Day 1 – AWS Learning Journey

## Objective
The goal of Day 1 was to begin the AWS learning journey by performing a simple but important foundational task: creating an EC2 key pair. This task helps in understanding how AWS handles secure access to cloud resources and sets the groundwork for future EC2-related tasks.

---

## AWS Service / Concept Covered
- EC2 (Elastic Compute Cloud)
- Key Pairs
- AWS Regions
- Secure access using SSH keys

---

## Steps I Took

1. Logged into the AWS Management Console using the provided temporary credentials.
2. Confirmed that the selected AWS region was **us-east-1 (N. Virginia)**, as all resources were required to be created in this region.
3. Navigated to the **EC2** service from the AWS services menu.
4. From the EC2 dashboard, selected **Key Pairs** under the *Network & Security* section.
5. Clicked on **Create key pair**.
6. Entered the key pair name as **nautilus-kp**.
7. Selected **RSA** as the key pair type.
8. Left the private key file format as the default `.pem`.
9. Created the key pair and confirmed that the private key file downloaded automatically.
10. Verified that the key pair appeared in the list with the correct name and type.

---

## Issues Faced
- No errors were encountered during this task.

---

## Key Takeaways

- AWS key pairs are used for secure authentication when connecting to EC2 instances.
- AWS resources are region-specific; selecting the correct region is critical.
- RSA is a commonly used and secure key type for EC2 access.
- Even simple tasks like creating a key pair are foundational for larger cloud operations.

---

## Conclusion
Day 1 focused on understanding AWS access fundamentals and getting comfortable navigating the AWS Console. This task marks the first practical step in the AWS cloud learning journey and prepares the foundation for launching and accessing EC2 instances in future tasks.

We’ll keep building this journey one solid day at a time ☁️🚀
