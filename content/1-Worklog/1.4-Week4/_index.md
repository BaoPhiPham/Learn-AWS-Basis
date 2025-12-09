---
title: "Week 4 Worklog"
date: 2025-09-29
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

* Learn how to deploy, manage, and secure **relational databases** using **Amazon RDS**.  
* Understand the fundamentals of **Amazon S3** for object storage and lifecycle management.  
* Explore **Elastic File System (EFS)** for shared storage between multiple EC2 instances.  
* Implement **data backup, versioning, and encryption** strategies for durability and compliance.  
* Strengthen access control through **IAM policies**, **bucket policies**, and **database authentication**.

---

### Tasks to be carried out this week:

| Day | Task                                                                                                                                                                                                                                                                                                                                                              | Start Date | Completion Date | Reference Material                                   |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ---------------------------------------------------- |
| 2   | - Learn about **Amazon RDS** concepts: DB Instances, Multi-AZ, Read Replicas.<br>- **Practice:**<br>&emsp;+ Launch a MySQL RDS instance.<br>&emsp;+ Configure parameter groups and security groups.<br>&emsp;+ Connect via EC2 and test basic CRUD operations.<br><br>→ Gain hands-on experience in database provisioning.                                        | 29/09/2025 | 29/09/2025      | [AWS Study Group](https://000019.awsstudygroup.com/) |
| 3   | - Explore **Amazon S3** object storage.<br>- Understand **storage classes** and **lifecycle policies**.<br>- **Practice:**<br>&emsp;+ Create an S3 bucket with versioning enabled.<br>&emsp;+ Upload, download, and delete objects.<br>&emsp;+ Implement lifecycle rules for data archiving to Glacier.<br><br>→ Learn efficient and cost-effective data storage. | 30/09/2025 | 30/09/2025      | [AWS Study Group](https://000020.awsstudygroup.com/) |
| 4   | - Study **Amazon EFS** for scalable file storage.<br>- **Practice:**<br>&emsp;+ Create an EFS file system.<br>&emsp;+ Mount it on two EC2 instances.<br>&emsp;+ Test shared access and file synchronization.<br><br>→ Understand shared file systems for distributed environments.                                                                                | 01/10/2025 | 01/10/2025      | [AWS Study Group](https://000021.awsstudygroup.com/) |
| 5   | - Strengthen **data protection and backup strategies**.<br>- **Practice:**<br>&emsp;+ Enable **automated backups** and **snapshot scheduling** for RDS.<br>&emsp;+ Use **S3 versioning** and **cross-region replication (CRR)**.<br>&emsp;+ Encrypt data at rest using **KMS**.<br><br>→ Implement secure and redundant data management practices.                | 02/10/2025 | 02/10/2025      | [AWS Study Group](https://000022.awsstudygroup.com/) |
| 6   | - Learn to control access and security.<br>- **Practice:**<br>&emsp;+ Configure **IAM policies** and **bucket policies** for least privilege access.<br>&emsp;+ Implement **IAM database authentication** for RDS.<br>&emsp;+ Audit access logs via **CloudTrail**.<br><br>→ Strengthen data governance and compliance.                                           | 03/10/2025 | 03/10/2025      | [AWS Study Group](https://000023.awsstudygroup.com/) |

---

### Week 4 Achievements

#### 1. Amazon RDS
- Launched and configured a **MySQL RDS instance** with Multi-AZ deployment.  
- Tested **read/write operations** and **security group connectivity** from EC2.  
- Understood automated backups, snapshots, and parameter group configuration.  

#### 2. Amazon S3
- Created an **S3 bucket** with **versioning** and **lifecycle management**.  
- Practiced **object operations** (upload, delete, restore) and archiving to **Glacier**.  
- Learned **storage class optimization** for cost efficiency.  

#### 3. Amazon EFS
- Set up an **EFS file system** and mounted it on multiple EC2 instances.  
- Verified **shared access and data consistency**.  
- Compared EFS with S3 and EBS for different workloads.  

#### 4. Data Backup and Security
- Implemented **RDS automated backups** and **snapshot scheduling**.  
- Applied **encryption at rest (KMS)** and **cross-region replication (CRR)** for S3.  
- Ensured compliance with AWS **Well-Architected Security Pillar** guidelines.  

#### 5. Access Control and Governance
- Designed **IAM and bucket policies** following least-privilege principles.  
- Integrated **IAM database authentication** for user access control.  
- Audited activities with **CloudTrail logs** to maintain accountability.  
