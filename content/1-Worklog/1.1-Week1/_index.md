---
title: "Week 1 Worklog"
date: 2025-09-08
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Week 1 Objectives:

* Understand and implement cost management strategies using **AWS Budgets**.
* Master core concepts of **AWS Identity and Access Management (IAM)**, including users, groups, and roles.
* Build a secure and isolated cloud network infrastructure with **Amazon VPC** and a **Site-to-Site VPN**.
* Launch, configure, and manage virtual servers using **Amazon EC2**.
* Securely grant AWS service permissions to applications running on EC2 using **IAM Roles**.

### Tasks to be carried out this week:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                         | Start Date | Completion Date | Reference Material                                   |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ---------------------------------------------------- |
| 2   | - Learn to monitor and control AWS costs with AWS Budgets.<br>- Understand different types of budgets available.<br>- **Practice:**<br>&emsp;+ Create a **Cost Budget** to track overall spending against a set amount.<br>&emsp;+ Create a **Usage Budget** to monitor specific service consumption.<br>&emsp;+ Explore **Reservation & Savings Plans Budgets** for commitment tracking.                    | 08/09/2025 | 08/09/2025      | [AWS Study Group](https://000007.awsstudygroup.com/) |
| 3   | - Learn the fundamentals of IAM: Users, Groups, Policies, and Roles.<br>- Follow security best practices for the root user.<br>- **Practice:**<br>&emsp;+ Create an **Admin Group** with AdministratorAccess policy.<br>&emsp;+ Create a new **IAM User** and add it to the Admin Group.<br>&emsp;+ Understand how to create and use an **IAM Role**.<br>&emsp;+ Practice using the **Switch Role** feature. | 09/09/2025 | 09/09/2025      | [AWS Study Group](https://000002.awsstudygroup.com/) |
| 4   | - Learn to build a secure, custom network with Amazon VPC.<br>- Understand VPC components: subnets, route tables, internet gateways.<br>- **Practice:**<br>&emsp;+ Create a VPC with public and private subnets.<br>&emsp;+ Configure **Security Groups** as a stateful firewall.<br>&emsp;+ Launch an EC2 instance within the VPC.<br>&emsp;+ Establish a **Site-to-Site VPN** connection.                  | 10/09/2025 | 10/09/2025      | [AWS Study Group](https://000003.awsstudygroup.com/) |
| 5   | - Get introduced to Amazon EC2 core concepts.<br>- Deploy applications on different operating systems.<br>- **Practice:**<br>&emsp;+ Launch a **Windows Server 2022** instance and connect via RDP.<br>&emsp;+ Launch an **Amazon Linux 2** instance and connect via SSH.<br>&emsp;+ Deploy a user management application on both instances.<br>&emsp;+ Implement cost governance for EC2 usage.             | 11/09/2025 | 11/09/2025      | [AWS Study Group](https://000004.awsstudygroup.com/) |
| 6   | - Understand why hardcoding access keys in applications is a security risk.<br>- Learn to use IAM Roles for EC2 to grant secure permissions.<br>- **Practice:**<br>&emsp;+ Prepare an S3 bucket and an EC2 instance.<br>&emsp;+ Create an **IAM Role** with S3 access permissions.<br>&emsp;+ Attach the role to the EC2 instance.<br>&emsp;+ Verify the application can access S3 without access keys.      | 12/09/2025 | 12/09/2025      | [AWS Study Group](https://000048.awsstudygroup.com/) |

### Week 1 Achievements

## Cost Management
-   Successfully created and configured **AWS Budgets** to monitor costs and usage.
-   Practiced setting up different types of budgets, including **Cost Budgets**, **Usage Budgets**, **Reservation Budgets**, and **Savings Plans Budgets**.

## Identity & Access Management (IAM)
-   Mastered the creation of **IAM users** and **groups** to manage permissions effectively.
-   Understood the principle of least privilege by creating an **Admin user/group**.
-   Learned how to create and use **IAM Roles** for secure delegation of permissions and practiced using **Switch Roles**.

## Network Infrastructure (VPC & VPN)
-   Built a complete, custom **Amazon VPC** including subnets, an internet gateway, and route tables.
-   Configured network security using **Security Groups** to act as a firewall for EC2 instances.
-   Successfully established a **Site-to-Site VPN** connection, simulating a hybrid cloud environment.

## Compute with Amazon EC2
-   Launched both **Microsoft Windows Server** and **Amazon Linux 2** instances on EC2.
-   Gained hands-on experience connecting to and performing basic administration on virtual servers.
-   Deployed a sample **user management application** on both Linux and Windows environments.
-   Implemented **cost & usage governance** strategies related to EC2.

## Secure Application Integration
-   Understood the security risks of using static access keys within applications.
-   Successfully created an **IAM Role for EC2** to grant an application temporary, secure permissions to other AWS services.
-   Verified that an application running on EC2 could access resources (like S3) without needing hardcoded credentials.