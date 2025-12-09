---
title: "Week 3 Worklog"
date: 2025-09-22
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:

* Learn how to design a **highly available and scalable** infrastructure on AWS.  
* Implement **Elastic Load Balancing (ELB)** and **Auto Scaling Groups (ASG)** for automatic traffic distribution and instance scaling.  
* Configure **Amazon Route 53** for domain management and DNS routing.  
* Strengthen system reliability through **data backup** and **monitoring** solutions.  
* Practice analyzing performance metrics and responding to scaling events.  

---

### Tasks to be carried out this week:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                         | Start Date | Completion Date | Reference Material                                   |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ---------------------------------------------------- |
| 2   | - Study the concept of **Elastic Load Balancing (ELB)**.<br>- Understand the types: Application, Network, and Gateway Load Balancers.<br>- **Practice:**<br>&emsp;+ Deploy two EC2 instances in separate Availability Zones.<br>&emsp;+ Create an **Application Load Balancer (ALB)** and configure target groups.<br>&emsp;+ Test load distribution using a web application.<br><br>→ Gain hands-on experience with ELB traffic management. | 22/09/2025 | 22/09/2025      | [AWS Study Group](https://000014.awsstudygroup.com/) |
| 3   | - Learn about **Auto Scaling Groups (ASG)** and scaling policies.<br>- **Practice:**<br>&emsp;+ Create a **Launch Template** for EC2 configuration.<br>&emsp;+ Configure an **ASG** to maintain a minimum and maximum instance count.<br>&emsp;+ Test scale-out and scale-in policies using CPU utilization metrics.<br><br>→ Implement dynamic scaling based on workload.                                                                   | 23/09/2025 | 23/09/2025      | [AWS Study Group](https://000015.awsstudygroup.com/) |
| 4   | - Explore **Amazon Route 53** and its DNS routing policies.<br>- **Practice:**<br>&emsp;+ Register a custom domain or use a hosted zone.<br>&emsp;+ Configure **A/AAAA** and **CNAME** records.<br>&emsp;+ Connect Route 53 to the **Load Balancer DNS**.<br><br>→ Understand domain routing and failover management.                                                                                                                        | 24/09/2025 | 24/09/2025      | [AWS Study Group](https://000016.awsstudygroup.com/) |
| 5   | - Learn backup and recovery best practices.<br>- **Practice:**<br>&emsp;+ Create **EBS snapshots** and **RDS automated backups**.<br>&emsp;+ Store backups in **Amazon S3** using **Lifecycle Policies**.<br>&emsp;+ Test recovery by restoring from snapshots.<br><br>→ Ensure system durability through automated backup strategies.                                                                                                       | 25/09/2025 | 25/09/2025      | [AWS Study Group](https://000017.awsstudygroup.com/) |
| 6   | - Enhance observability with **Amazon CloudWatch** and **AWS CloudTrail**.<br>- **Practice:**<br>&emsp;+ Set up **CloudWatch Alarms** for CPU, memory, and network metrics.<br>&emsp;+ View ASG scaling events and ELB request metrics.<br>&emsp;+ Use **CloudTrail** to track user activities and API calls.<br><br>→ Build a complete monitoring and audit solution.                                                                       | 26/09/2025 | 26/09/2025      | [AWS Study Group](https://000018.awsstudygroup.com/) |

---

### Week 3 Achievements

#### 1. Elastic Load Balancing (ELB)
- Deployed and configured an **Application Load Balancer** distributing traffic across multiple EC2 instances.  
- Validated load balancing and failover mechanisms through performance testing.  
- Understood the difference between **Application**, **Network**, and **Gateway** Load Balancers.  

#### 2. Auto Scaling Groups (ASG)
- Successfully created and tested an **Auto Scaling Group** using a **Launch Template**.  
- Implemented **target tracking** and **step scaling policies** based on CPU utilization.  
- Verified automatic scaling actions and instance replacement during health check failures.  

#### 3. Amazon Route 53
- Configured DNS routing for web applications through **Route 53 Hosted Zones**.  
- Linked **Route 53 records** with the **Load Balancer DNS name** for domain access.  
- Gained insights into **routing policies** such as Simple, Weighted, and Failover.  

#### 4. Backup and Recovery
- Created and validated **EBS snapshots** and **RDS automated backups**.  
- Implemented S3-based **backup storage and lifecycle management**.  
- Successfully restored resources from snapshots to ensure disaster recovery readiness.  

#### 5. Monitoring and Observability
- Set up **CloudWatch Alarms** to detect performance anomalies.  
- Monitored **ASG scaling events**, **ELB request metrics**, and **RDS performance** dashboards.  
- Tracked API activities and user actions using **AWS CloudTrail**, improving overall visibility and governance.  
