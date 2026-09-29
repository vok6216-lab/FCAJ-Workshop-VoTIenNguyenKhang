---
title: "Week 5 Worklog"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---


### Week 5 Objectives:

* Master the AWS Shared Responsibility Model
* Deep understanding of identity and access management on AWS
* Gain proficiency in IAM, Organizations, Identity Center, Cognito, KMS, and Security Hub

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 1–2 | Shared Responsibility Model + IAM fundamentals (Root, Users, Groups, Policies, Roles) | 25–26/08/2025 | 26/08/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | IAM Policies (Identity-based vs Resource-based), Policy Evaluation Logic, Explicit Deny | 27/08/2025 | 27/08/2025 | |
| 4 | IAM Roles, Trust Policy, STS, AssumeRole, Cross-account access, Service roles | 28/08/2025 | 28/08/2025 | |
| 5 | AWS Organizations, OU, SCP, Consolidated Billing + AWS Identity Center | 29/08/2025 | 29/08/2025 | |
| 6 | Amazon Cognito, AWS KMS, AWS Security Hub | 30/08/2025 | 30/08/2025 | |


### Week 5 Achievements:

Successfully completed all Week 5 objectives with strong mastery of:

* **AWS Shared Responsibility Model**: AWS secures the cloud, customers secure in the cloud. Responsibility varies by service type (Infrastructure → Container → Abstracted services).

* **Root Account Protection**: MFA enabled, never used for daily tasks, credentials safely stored, IAM Administrator users created instead.

* **AWS IAM Mastery**:

  * Principals: Root, IAM Users, IAM Roles, Federated Users, AWS Services

  * Policy types and evaluation: Explicit Deny wins, then Allow, then default Deny

  * IAM Roles + Trust Policy + STS for temporary, least-privilege, cross-account access

  * Cross-account delegation and service-linked roles

* **AWS Organizations**:

  * Centralized multi-account management with OUs

  * Service Control Policies (SCP) to set permission guardrails

  * Consolidated Billing

* **AWS Identity Center (formerly AWS SSO)**:

  * Identity source integration (built-in, AWS Managed Microsoft AD, AD Connector, external IdP)

  * Permission Sets → auto-provisioned IAM Roles in member accounts

* **Amazon Cognito**:

  * User Pools for user sign-up/sign-in

  * Identity Pools for temporary AWS credential issuance

* **AWS KMS**:

  * Customer Managed Keys (CMK), FIPS 140-2 compliant

  * Data Key pattern for large-scale encryption

* **AWS Security Hub**:

  * Continuous security checking against AWS Foundational Best Practices, CIS, PCI DSS, etc.

  * Security score and prioritized findings

Hands-on completed:

* Built full AWS Organizations structure with SCPs

* Configured AWS Identity Center with Permission Sets

* Implemented Cognito authentication flow

* Encrypted resources with KMS

* Activated and analyzed Security Hub findings


