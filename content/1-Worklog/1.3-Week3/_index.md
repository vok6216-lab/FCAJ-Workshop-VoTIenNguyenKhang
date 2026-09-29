---
title: "Week 3 Worklog"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---


### Week 3 Objectives:

* Get to know First Cloud Journey members
* Understand fundamental AWS services and master the use of AWS Management Console & AWS CLI

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Meet and greet FCJ members <br> - Read and take notes on internship rules and regulations | 08/11/2025 | 08/11/2025 | |
| 3 | - Overview of AWS and its service categories (Compute, Storage, Networking, Database, etc.) | 08/12/2025 | 08/12/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Create AWS Free Tier account <br> - Learn AWS Management Console & AWS CLI <br> - **Hands-on:** account creation, install & configure AWS CLI | 08/13/2025 | 08/13/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Deep dive into Amazon EC2 (Instance types, AMI, EBS, Key Pairs, Instance Store, User Data, Metadata, Pricing models, Auto Scaling, etc.) <br> - Related services: Lightsail, EFS, FSx, AWS MGN | 08/14/2025 | 08/16/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - **Hands-on practice:** <br>&emsp; ∘ Launch EC2 instances <br>&emsp; ∘ Connect via SSH/RDP <br>&emsp; ∘ Attach EBS volume <br>&emsp; ∘ Create snapshots & custom AMIs | 08/15/2025 | 08/16/2025 | <https://cloudjourney.awsstudygroup.com/> |


### Week 3 Achievements:

Successfully completed 100% of the planned tasks with the following key takeaways:

* Developed comprehensive understanding of **Amazon EC2** as scalable virtual servers capable of fully replacing physical servers for nearly any workload (web hosting, applications, databases, authentication, etc.).

* Acquired proficiency in hardware configuration through **Instance Types** (CPU, memory, network, storage) and related concepts: Hypervisor (Nitro/KVM/HVM/PV), Placement Groups, and Availability Zones.

* Gained clear comprehension of **AMI (Amazon Machine Image)**: includes root volume, launch permissions + block device mapping; can utilize AWS-provided, Marketplace, or custom AMIs; backup through AMI creation or EBS snapshots.

* Achieved expertise with **Key Pairs**: SSH authentication for Linux and encrypted Administrator password decryption for Windows instances.

* Attained thorough knowledge of **Amazon EBS (Elastic Block Store)**:

  * Persistent block storage independent of EC2 lifecycle, connected via private EBS network within the same AZ

  * SSD & HDD families, 99.99% availability through replication across multiple nodes

  * Multi-Attach capability on Nitro-based instances

  * Backup via incremental snapshots stored in S3

* Understood **Instance Store**: high-performance ephemeral NVMe storage physically attached to the host; data lost on Stop (but preserved on Reboot); ideal for cache, buffer, swap, temporary data.

* Learned **User Data** scripts (Bash/PowerShell) and **Instance Metadata** for automation and self-configuration.

* Explored EC2 pricing models and Auto Scaling:

  * On-Demand, Reserved Instances, Savings Plans, Spot Instances

  * Auto Scaling Groups support multiple pricing models, multi-AZ operation, and automatic registration with Elastic Load Balancers

* Studied complementary services:

  * **Amazon Lightsail**: low-cost, simplified VPS with bundled data transfer, ideal for dev/test and light workloads

  * **EFS (Elastic File System)**: fully managed NFS for Linux, pay-for-use storage, supports on-premises access via DX/VPN

  * **FSx**: managed Windows File Server (SMB) and FSx for Lustre, with built-in deduplication (30–50% savings)

  * **AWS Application Migration Service (MGN)**: continuous replication for lift-and-shift migration and DR from on-premises/physical/virtual servers to AWS

* Hands-on success: launched EC2 instances, connected via SSH/RDP, attached EBS volumes, created snapshots and custom AMIs.


