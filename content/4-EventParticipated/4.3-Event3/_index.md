---
title: "Event 3"
date: 2025-11-17
weight: 4
chapter: false
pre: "<b> 4.3. </b>"
---

# Summary Report: AWS Cloud Mastery Series #2 – DevOps on AWS

## Event Objectives

- Understand the core principles of DevOps culture and key performance metrics (DORA).
- Master the AWS DevOps ecosystem for building end-to-end CI/CD pipelines.
- Compare and select appropriate Infrastructure as Code (IaC) tools (CloudFormation vs. AWS CDK).
- Explore containerization strategies using Amazon ECS, EKS, and App Runner.
- Implement full-stack observability using CloudWatch and AWS X-Ray.

## Time & Venue

**Time:** 08:30 – 17:00, Monday, November 17, 2025  
**Venue:** 26th Floor, Bitexco Financial Tower, 2 Hai Trieu Street, Ben Nghe Ward, District 1, Ho Chi Minh City

## Speakers

- **Truong Quang Tinh** - DevOps Engineer, TymeX | AWS Community Builder
- **Kha Van** - Cloud Security Engineer | AWS Community Builders
- **Bao Huynh** – AWS Community Builder
- **Thinh Nguyen** – AWS Community Builder
- **Vi Tran** – AWS Community Builder

## Key Highlights

### 1. DevOps Culture & Metrics

- **Cultural Shift:** Moving from siloed development and operations to a unified culture of shared responsibility.
- **Key Metrics (DORA):** Focusing on four critical indicators to measure performance:
  - Deployment Frequency (DF)
  - Lead Time for Changes (LT)
  - Mean Time to Restore (MTTR)
  - Change Failure Rate (CFR)

### 2. AWS DevOps Services – CI/CD Pipeline

- **Source Control:** Strategies for Git management (GitFlow vs. Trunk-based development) using AWS CodeCommit.
- **Orchestration:** Automating the release process with **AWS CodePipeline**.
- **Deployment Strategies:**
  - **Blue/Green:** Reduces downtime and risk by running two identical environments.
  - **Canary:** Rolls out changes to a small subset of users first.
  - **Rolling:** Updates instances incrementally.

### 3. Infrastructure as Code (IaC)

- **AWS CloudFormation:** The declarative approach using JSON/YAML templates to define infrastructure; utilizes drift detection to maintain state consistency.
- **AWS CDK (Cloud Development Kit):** The imperative approach allowing developers to define cloud resources using familiar programming languages (TypeScript, Python, Java). CDK constructs allow for reusable infrastructure patterns.

### 4. Container Services & Observability

- **Compute Evolution:** Selection criteria between **Amazon ECS** (tight control), **Amazon EKS** (Kubernetes standard), and **AWS App Runner** (simplified for developers).
- **Observability:** Going beyond simple monitoring by integrating **CloudWatch** (Logs, Metrics, Alarms) with **AWS X-Ray** for distributed tracing, enabling root-cause analysis in microservices.

## Key Takeaways

### Design Mindset

- **Automation First:** Manual processes are error-prone; everything from testing to infrastructure provisioning should be automated.
- **Shift-Left Security:** Integrating security checks early in the CI/CD pipeline rather than at the end.
- **Measure Everything:** You cannot improve what you do not measure. DORA metrics are the compass for DevOps maturity.

### Technical Architecture

- **Immutable Infrastructure:** Servers are never modified after deployment; they are replaced.
- **Pipeline Orchestration:** A robust pipeline must include build, unit test, integration test, and approval gates before production deployment.
- **Traceability:** In distributed systems, correlating logs and traces (via X-Ray) is mandatory for debugging.

### Modernization Strategy

- **Right-sizing Compute:** Use **App Runner** for simple web apps to reduce operational overhead, and reserve **EKS** for complex, orchestrated microservices.
- **IaC Adoption:** Moving away from manual console clicks to code-defined infrastructure to ensure reproducibility and disaster recovery.

## Applying to Work

- **Adopt Trunk-based Development:** Streamline the git workflow in the team project to reduce merge conflicts and accelerate integration.
- **Implement CI/CD:** Build a pipeline using **AWS CodePipeline** that automatically deploys the student management backend upon pushing to the main branch.
- **Migrate to IaC:** Refactor the current manual setup of DynamoDB and Lambda functions into **AWS CDK** scripts for better maintainability.
- **Enhance Monitoring:** Set up **CloudWatch Alarms** for critical API errors (5xx) to proactively detect issues before the demo.

## Event Experience

Attending the **“DevOps on AWS”** workshop was instrumental in bridging the gap between coding and operations. It provided a roadmap for building reliable, scalable systems. Key experiences included:

- **Learning from practitioners:** The speakers, being active AWS Community Builders, shared "war stories" and real-world pitfalls in DevOps, not just textbook theory. I gained clarity on the **Shared Responsibility Model** within a DevOps context.
- **Hands-on technical exposure:**
  - Participated in a **live CI/CD walkthrough**, witnessing raw code transform into a deployed application via an automated pipeline in minutes.
  - Experienced the power of **AWS CDK** by deploying a VPC and ECS cluster with significantly fewer lines of code compared to raw CloudFormation templates.
  - Visualized distributed tracing with **AWS X-Ray**, understanding how to pinpoint latency bottlenecks in microservices.
- **Networking and discussions:** Engaged in discussions about the trade-offs between **GitFlow** and **Trunk-based** development for small teams and received guidance on the **AWS Certified DevOps Engineer – Professional** certification roadmap.

### Lessons learned

- **IaC is non-negotiable:** For any long-term project, infrastructure must be code.
- **Observability is crucial:** Building a system is half the battle; knowing it is healthy is the other half.
- **Culture over tools:** Tools like Jenkins or CodePipeline are useless without a culture of collaboration and continuous improvement.

## Some event photos

![Warm-up with speaker Tinh Truong](/images/4-EventParticipated/Event4_1.jpg)
![Infrastructure as Code (IaC)](/images/4-EventParticipated/Event4_2.jpg)

> Overall, the event not only provided technical skills in AWS tools but also instilled a professional DevOps mindset, preparing me to build production-grade systems efficiently.
