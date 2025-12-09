---
title: "Week 6 Worklog"
date: 2025-10-13
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

* Learn how to design and deploy **serverless architectures** using AWS services.  
* Build and test applications with **AWS Lambda**, **API Gateway**, and **DynamoDB**.  
* Automate infrastructure deployment using **AWS CloudFormation**.  
* Explore **event-driven design** and cross-service integration.  
* Apply monitoring and logging best practices for serverless environments.  

---

### Tasks to be carried out this week:

| Day | Task                                                                                                                                                                                                                                                                                                                                                       | Start Date | Completion Date | Reference Material                                   |
| --- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ---------------------------------------------------- |
| 2   | - Study **Serverless Computing** concepts and benefits.<br>- Understand when to use Lambda vs EC2.<br>- **Practice:**<br>&emsp;+ Create a simple **Lambda function** in Python.<br>&emsp;+ Test function triggers via AWS Console and CLI.<br><br>→ Gain foundational understanding of serverless execution.                                               | 13/10/2025 | 13/10/2025      | [AWS Study Group](https://000031.awsstudygroup.com/) |
| 3   | - Learn how to build APIs with **Amazon API Gateway**.<br>- **Practice:**<br>&emsp;+ Create a REST API endpoint linked to Lambda.<br>&emsp;+ Deploy API stages and test public access.<br><br>→ Understand API integration with serverless functions.                                                                                                      | 14/10/2025 | 14/10/2025      | [AWS Study Group](https://000032.awsstudygroup.com/) |
| 4   | - Work with **Amazon DynamoDB** for serverless data storage.<br>- **Practice:**<br>&emsp;+ Create a DynamoDB table and define partition/sort keys.<br>&emsp;+ Integrate Lambda to perform CRUD operations.<br>&emsp;+ Test data retrieval and updates via API Gateway.<br><br>→ Learn data-driven serverless architecture.                                 | 15/10/2025 | 15/10/2025      | [AWS Study Group](https://000033.awsstudygroup.com/) |
| 5   | - Learn **AWS CloudFormation** basics for Infrastructure as Code (IaC).<br>- **Practice:**<br>&emsp;+ Write a YAML template to deploy Lambda, API Gateway, and DynamoDB.<br>&emsp;+ Automate stack creation and deletion.<br><br>→ Automate deployment using CloudFormation templates.                                                                     | 16/10/2025 | 16/10/2025      | [AWS Study Group](https://000034.awsstudygroup.com/) |
| 6   | - Implement monitoring and automation for serverless systems.<br>- **Practice:**<br>&emsp;+ Use **CloudWatch Logs** to track Lambda execution.<br>&emsp;+ Set up **CloudWatch Alarms** for errors and throttles.<br>&emsp;+ Create a simple automation rule with **EventBridge**.<br><br>→ Maintain reliability and observability in serverless workloads. | 17/10/2025 | 17/10/2025      | [AWS Study Group](https://000035.awsstudygroup.com/) |

---

### Week 6 Achievements

#### 1. Serverless Fundamentals
- Understood the benefits of serverless design (no server management, auto-scaling, pay-per-use).  
- Created and tested basic **Lambda functions** triggered manually and via API events.  

#### 2. API Gateway Integration
- Built a **REST API** with **Amazon API Gateway** connected to **Lambda**.  
- Deployed multiple stages (dev, prod) and tested public access successfully.  

#### 3. DynamoDB Integration
- Designed a **DynamoDB** table with efficient key structure for fast access.  
- Integrated Lambda to perform **CRUD operations** directly from serverless functions.  
- Tested full API-Lambda-DynamoDB workflow end-to-end.  

#### 4. Infrastructure as Code (IaC)
- Automated deployment of serverless architecture using **CloudFormation** templates.  
- Managed stack creation, updates, and teardown in a reproducible way.  

#### 5. Monitoring and Automation
- Implemented **CloudWatch Logs and Alarms** to detect runtime issues.  
- Used **EventBridge** to trigger alerts or workflows based on Lambda events.  
- Strengthened observability, reliability, and automation in the serverless environment.  