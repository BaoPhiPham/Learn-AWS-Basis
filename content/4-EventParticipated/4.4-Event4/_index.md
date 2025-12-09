---
title: "Event 4"
date: 2025-11-29
weight: 5
chapter: false
pre: "<b> 4.4. </b>"
---

# Summary Report: AWS Cloud Mastery Series #3 - ​Theo AWS Well-Architected Security Pillar

## Event Objectives

- Deeply understand the **Security Pillar** within the AWS Well-Architected Framework.
- Master the core principles: **Least Privilege**, **Zero Trust**, and **Defense in Depth**.
- Learn how to implement security controls across 5 key areas: IAM, Detection, Infrastructure Protection, Data Protection, and Incident Response.
- Identify top security threats in the cloud environment specifically for the Vietnamese market.

## Time & Venue

**Time:** 08:30 – 12:00, Saturday, November 29, 2025  
**Venue:** 26th Floor, Bitexco Financial Tower, 2 Hai Trieu Street, Ben Nghe Ward, District 1, Ho Chi Minh City

## Speakers

- **Le Vu Xuan An** - Software & Cloud Engineer | AWS Cloud Club Captain HCMUTE
- **Tran Doan Cong Ly** - DevOps Engineer | AWS FCAJ Ambassador | AWS Cloud Club Captain PTIT
- **Danh Hoang Hieu Nghi** – AI Engineer, Renova Cloud | AWS First Cloud AI Journey | AWS Cloud Club Captain HUFLIT
- **Tran Duc Anh** - Cloud Security Engineer Trainee | First Cloud AI Journey | AWS Cloud Club Captain SGU
- **Nguyen Tuan Thinh** - Cloud Engineer Trainee | First Cloud AI Journey
- **Nguyen Do Thanh Dat** - Cloud Engineer Trainee | First Cloud AI Journey
- **Đinh Le Hoang Anh** – Cloud Engineer Trainee | First Cloud AI Journey
- **Kha Van** - Cloud Security Engineer | AWS Community Builders

**Special Guest:**

- **Mendel Grabski** - Cloud Security & Solution Architect | Enabling Secure-by-Design Solutions
- **Truong Quang Tinh** - DevOps Engineer, TymeX | AWS Community Builder

## Key Highlights

### 1. Security Foundations & Identity (IAM)

- **Core Principles:** Moved beyond perimeter security to a **Zero Trust** model where every request must be authenticated and authorized.
- **Modern IAM:**
  - Transition from long-term credentials (IAM Users with Access Keys) to temporary credentials via **IAM Roles** and **Identity Center (SSO)**.
  - Enforcing **Least Privilege** using Access Analyzer to validate policies.
  - **Multi-Account Strategy:** Using SCPs (Service Control Policies) to set permission boundaries across the organization.

### 2. Detection & Continuous Monitoring

- **Centralized Visibility:** utilizing **Security Hub** to aggregate alerts from GuardDuty, Inspector, and Macie.
- **Logging Strategy:** Enabling logs at all layers is non-negotiable (VPC Flow Logs for network, CloudTrail for API calls, S3 Server Access Logs).
- **Detection-as-Code:** Defining alert rules as code to ensure consistent monitoring across environments.

### 3. Infrastructure & Data Protection

- **Network Security:** Implementing **Defense in Depth** with VPC segmentation (Public/Private subnets), Security Groups (stateful), and WAF/Shield for edge protection.
- **Encryption:**
  - **At-rest:** Using KMS with automatic key rotation for EBS, RDS, and S3.
  - **In-transit:** Enforcing TLS 1.2+ for all data movement.
- **Secrets Management:** replacing hardcoded credentials in code with **AWS Secrets Manager** or **Parameter Store**.

### 4. Incident Response (IR) Automation

- **IR Lifecycle:** Preparation → Detection & Analysis → Containment, Eradication & Recovery → Post-Incident Activity.
- **Playbooks:** Detailed walkthroughs for handling common scenarios like compromised IAM keys or public S3 buckets.
- **Automation:** Using **Lambda** and **Step Functions** to auto-remediate issues (e.g., automatically revoking a compromised user's session).

## Key Takeaways

### Security Mindset

- **Security is everyone's responsibility:** It is not just for the security team; developers must practice "Security by Design".
- **Assume Breach:** Always design systems assuming that a component might be compromised, limiting the "blast radius".

### Technical Architecture

- **Identity as the new perimeter:** In a cloud-native world, IAM is more critical than the network firewall.
- **Immutable Infrastructure:** Patching servers in place is risky; prefer replacing them with new, patched images to prevent malware persistence.

### Applying to Work

- **Refactor IAM:** Immediately review the group project's IAM policies. Remove any `*:*` permissions and replace hardcoded Access Keys with IAM Roles for EC2/Lambda.
- **Secure Secrets:** Migrate database credentials from `.env` files to **AWS Systems Manager Parameter Store**.
- **Enable GuardDuty:** Activate GuardDuty in the project account to detect anomalies (cryptojacking, unauthorized access) during the development phase.
- **Encryption:** Enable default encryption (SSE-S3) for all S3 buckets used in the Student Management System project.

## Event Experience

The workshop provided a concentrated, high-intensity dive into cloud security. Unlike general overviews, this session focused on **actionable patterns**:

- **Interactive Learning:** The mini-demo on validating IAM Policies and simulating access helped visualize how easily permissions can be misconfigured.
- **Real-world relevance:** Discussing "Top threats in Vietnam" made the content highly relatable, emphasizing the need to protect against common misconfigurations and credential leaks.
- **Practical Automation:** Seeing an automated IR playbook triggered by EventBridge and executed by Lambda changed my perspective on how to handle security incidents at scale.

## Some Event Photos

![All members participated](/images/4-EventParticipated/Event5_1.jpg)
![Identity & Access Management](/images/4-EventParticipated/Event5_2.jpg)
![The Badging Journey](/images/4-EventParticipated/Event5_3.jpg)
![Multi Layer Security against Attack Vectors](/images/4-EventParticipated/Event5_4.jpg)
![Special Guest](/images/4-EventParticipated/Event5_5.jpg)

> This event shifted my perspective from "building it fast" to "building it secure." I now have a clear roadmap to harden our applications before they reach production.
