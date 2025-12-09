---
title: "Week 2 Worklog"
date: 2025-09-15
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:

* Deepen understanding of **Amazon EC2** and related storage services (**EBS**).  
* Learn how to store and retrieve data securely using **Amazon S3**.  
* Understand database deployment and connectivity through **Amazon RDS**.  
* Integrate EC2 applications with S3 and RDS to form a complete backend stack.  
* Practice monitoring and cost optimization for compute and storage resources.

---

### Tasks to be carried out this week:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                | Start Date | Completion Date | Reference Material                                   |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ---------------------------------------------------- |
| 2   | - Learn about Amazon Elastic Block Store (**EBS**) and its volume types.<br>- **Practice:**<br>&emsp;+ Create and attach an EBS volume to an existing EC2 instance.<br>&emsp;+ Format and mount the volume on Linux and Windows.<br>&emsp;+ Snapshot and restore EBS volumes for backup testing.                                                                    | 15/09/2025 | 15/09/2025      | [AWS Study Group](https://000009.awsstudygroup.com/) |
| 3   | - Explore **Amazon S3** as an object storage service.<br>- Understand buckets, objects, versioning, and lifecycle management.<br>- **Practice:**<br>&emsp;+ Create an S3 bucket and upload various file types.<br>&emsp;+ Enable **bucket versioning** and **object lifecycle policies**.<br>&emsp;+ Configure **bucket policies** and **ACLs** for access control. | 16/09/2025 | 16/09/2025      | [AWS Study Group](https://000010.awsstudygroup.com/) |
| 4   | - Learn to connect EC2 applications to **S3**.<br>- **Practice:**<br>&emsp;+ Write a simple Python or Node.js script on EC2 that uploads and retrieves data from S3.<br>&emsp;+ Use **IAM Roles** for secure authentication (no access keys).<br>&emsp;+ Test file access via AWS CLI and SDK.                                                                      | 17/09/2025 | 17/09/2025      | [AWS Study Group](https://000011.awsstudygroup.com/) |
| 5   | - Study **Amazon RDS** fundamentals (engine types, Multi-AZ, backups).<br>- **Practice:**<br>&emsp;+ Launch a MySQL RDS instance.<br>&emsp;+ Connect EC2 to RDS using private endpoints within the same VPC.<br>&emsp;+ Create, query, and manage sample databases.                                                                                                 | 18/09/2025 | 18/09/2025      | [AWS Study Group](https://000012.awsstudygroup.com/) |
| 6   | - Review and optimize compute and storage usage.<br>- **Practice:**<br>&emsp;+ Monitor EC2 and RDS metrics in **Amazon CloudWatch**.<br>&emsp;+ Analyze S3 and EBS usage in **AWS Cost Explorer**.<br>&emsp;+ Implement simple lifecycle policies for automatic cleanup of unused resources.                                                                        | 19/09/2025 | 19/09/2025      | [AWS Study Group](https://000013.awsstudygroup.com/) |

---

### Week 2 Achievements

### Compute & Storage Mastery
- Successfully created and attached **EBS volumes** to EC2 instances across different operating systems.  
- Practiced **snapshotting** and restoring volumes for backup and recovery scenarios.  
- Understood volume lifecycle management and pricing models.

### Object Storage with Amazon S3
- Deployed multiple **S3 buckets** with access control and versioning enabled.  
- Configured **Lifecycle Policies** to transition objects between storage tiers automatically.  
- Learned to enforce data security using **Bucket Policies** and **ACLs**.

### Database Integration (Amazon RDS)
- Launched and configured a **MySQL RDS instance** within a private subnet.  
- Connected EC2 applications securely to RDS using VPC routing and IAM-based access.  
- Practiced database administration: table creation, queries, and snapshots.

### Application Integration
- Wrote and executed scripts to upload/download files between EC2 and S3 using **IAM Roles** instead of static credentials.  
- Verified the end-to-end data flow between **EC2 → S3 → RDS**, forming a functional backend stack.

### Cost & Performance Optimization
- Monitored usage metrics with **Amazon CloudWatch** and **AWS Cost Explorer**.  
- Identified idle resources and optimized EBS/S3 configurations for efficiency.  
- Improved overall awareness of cost management strategies for compute and storage layers.