---
title: "Week 4 Worklog"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---


### Week 4 Objectives:

* Master Amazon Simple Storage Service (S3) and its ecosystem
* Understand object storage concepts, storage classes, lifecycle management, security, and performance optimization
* Explore the AWS Snow Family and hybrid storage solutions
* Learn disaster recovery concepts (RTO/RPO) and backup strategies

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 1–2 | Deep dive into Amazon S3: architecture, durability, availability, storage classes, lifecycle policies, versioning, static website hosting, CORS, access control (ACL, Bucket Policy, IAM), Access Points, endpoints | 08/18–08/19 | 08/19/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | S3 performance optimization, multipart upload, prefix design, event notifications, replication (CRR/SRR) | 08/20/2025 | 08/20/2025 | |
| 4 | Amazon S3 Glacier (Instant Retrieval, Flexible Retrieval, Deep Archive), retrieval options (Expedited, Standard, Bulk) | 08/21/2025 | 08/21/2025 | |
| 5 | AWS Snow Family (Snowball, Snowball Edge, Snowmobile) and AWS Storage Gateway (File, Volume, Tape) | 08/22/2025 | 08/22/2025 | |
| 6 | Disaster recovery concepts (RTO, RPO), 4 DR strategies on AWS, AWS Backup service | 08/23/2025 | 08/23/2025 | |


### Week 4 Achievements:

Successfully completed all Week 4 objectives with the following key learnings:

* Attained proficiency in **Amazon S3** fundamentals:

  * Object storage (not block/file), write-once-read-many (WORM) model, unlimited total capacity, max 5 TB per object

  * Designed for 99.999999999% (11×9s) durability and 99.99% availability

  * Data automatically replicated across minimum 3 Availability Zones in a region

  * Supports multipart upload, event notifications, static website hosting, and CORS configuration

* Understood **S3 Storage Classes** and cost optimization:

  * S3 Standard, Standard-IA, One Zone-IA, Intelligent-Tiering, Glacier Instant Retrieval, Glacier Flexible Retrieval, Glacier Deep Archive

  * Lifecycle policies to automatically transition or expire objects

* Security & access control:

  * S3 Bucket Policies, IAM Policies, S3 Access Control Lists (legacy), S3 Access Points

  * Block Public Access, VPC Endpoints for private connectivity

* Advanced features:

  * Versioning (protects against accidental deletion/overwrites and ransomware)

  * Cross-Region Replication (CRR) & Same-Region Replication (SRR)

  * S3 performance optimization using random prefixes to distribute objects across partitions

* Developed comprehensive understanding of **Amazon S3 Glacier**:

  * Low-cost archival storage with three retrieval options:

    * Expedited (1–5 min)

    * Standard (3–5 hours)

    * Bulk (5–12 hours)

* Learned **AWS Snow Family** for large-scale data migration:

  * Snowball (80 TB), Snowball Edge (100 TB + compute), Snowmobile (up to 100 PB per truck)

* Mastered **AWS Storage Gateway** – hybrid storage:

  * File Gateway → S3 (NFS/SMB)

  * Volume Gateway → S3 (iSCSI, cached or stored mode, snapshot to EBS)

  * Tape Gateway → Virtual Tape Library (S3/Glacier)

* Disaster Recovery concepts:

  * RTO (Recovery Time Objective) – maximum acceptable downtime

  * RPO (Recovery Point Objective) – maximum acceptable data loss

  * Four AWS DR strategies: Backup & Restore, Pilot Light, Warm Standby, Multi-Site Active/Active

  * AWS Backup – centralized backup management across EBS, EC2, RDS, DynamoDB, EFS, Storage Gateway

Hands-on practice completed:

* Created S3 buckets with versioning, lifecycle policies, static website hosting

* Configured bucket policies, CORS, and VPC endpoints

* Tested multipart upload and event triggers

* Explored AWS Backup console and created backup plans


