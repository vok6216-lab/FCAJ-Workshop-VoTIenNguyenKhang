---

title: "Week 5 Worklog"
date: "2026-10-12"
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
----------------------

### Week 5 Objectives:

* Master the AWS Shared Responsibility Model.
* Gain a deep understanding of identity and access management on AWS.
* Gain proficiency in IAM, Organizations, Identity Center, Cognito, KMS, and Security Hub.

### Tasks to be carried out this week:

| Day | Task                                                                                    | Start Date       | Completion Date | Reference Material                      |
| --- | --------------------------------------------------------------------------------------- | ---------------- | --------------- | --------------------------------------- |
| 1–2 | Shared Responsibility Model + IAM fundamentals (Root, Users, Groups, Policies, Roles)   | 10/12–10/13/2026 | 10/13/2026      | https://cloudjourney.awsstudygroup.com/ |
| 3   | IAM Policies (Identity-based vs Resource-based), Policy Evaluation Logic, Explicit Deny | 10/14/2026       | 10/14/2026      |                                         |
| 4   | IAM Roles, Trust Policy, STS, AssumeRole, Cross-account access, Service roles           | 10/15/2026       | 10/15/2026      |                                         |
| 5   | AWS Organizations, OU, SCP, Consolidated Billing + AWS Identity Center                  | 10/16/2026       | 10/16/2026      |                                         |
| 6   | Amazon Cognito, AWS KMS, AWS Security Hub                                               | 10/17/2026       | 10/17/2026      |                                         |

### Week 5 Achievements:

Successfully completed all Week 5 objectives with strong mastery of:

* **AWS Shared Responsibility Model**: AWS secures the cloud, while customers secure what they put in the cloud. Responsibility varies by service type (Infrastructure → Container → Abstracted services).

* **Root Account Protection**: MFA enabled, never used for daily tasks, credentials safely stored, and IAM Administrator users created instead.

* **AWS IAM Mastery**:

  * Principals: Root, IAM Users, IAM Roles, Federated Users, and AWS Services.

  * Policy types and evaluation: Explicit Deny takes precedence, followed by Allow, with Default Deny applying when no Allow is present.

  * IAM Roles + Trust Policy + STS for temporary, least-privilege, cross-account access.

  * Cross-account delegation and service-linked roles.

* **AWS Organizations**:

  * Centralized multi-account management with Organizational Units (OUs).

  * Service Control Policies (SCPs) to establish permission guardrails.

  * Consolidated Billing.

* **AWS Identity Center (formerly AWS SSO)**:

  * Identity source integration (built-in, AWS Managed Microsoft AD, AD Connector, and external IdP).

  * Permission Sets → automatically provisioned IAM Roles in member accounts.

* **Amazon Cognito**:

  * User Pools for user sign-up/sign-in.

  * Identity Pools for temporary AWS credential issuance.

* **AWS KMS**:

  * Customer Managed Keys (CMK), FIPS 140-2 compliant.

  * Data Key pattern for large-scale encryption.

* **AWS Security Hub**:

  * Continuous security checking against AWS Foundational Best Practices, CIS, PCI DSS, and other security standards.

  * Security score and prioritized findings.

### Hands-on practice completed:

* Built a complete AWS Organizations structure with SCPs.

* Configured AWS Identity Center with Permission Sets.

* Implemented a Cognito authentication flow.

* Encrypted resources using KMS.

* Activated and analyzed Security Hub findings.
