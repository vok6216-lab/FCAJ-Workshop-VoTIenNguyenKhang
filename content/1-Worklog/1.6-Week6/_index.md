---
title: "Week 6 Worklog"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---


### Week 6 Objectives:

* Master core and advanced database concepts
* Clearly distinguish OLTP vs OLAP, RDBMS vs NoSQL
* Gain full proficiency in AWS database services: RDS, Aurora, Redshift, ElastiCache

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 1–2 | Core DB concepts: PK, FK, Index, Partition, Query Plan, Buffer, Log, Session | 01–02/09/2025 | 02/09/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | RDBMS vs NoSQL • OLTP vs OLAP | 03/09/2025 | 03/09/2025 | |
| 4 | Amazon RDS & Amazon Aurora (MySQL/PostgreSQL-compatible) | 04/09/2025 | 04/09/2025 | |
| 5 | Amazon Redshift – Managed Data Warehouse & OLAP | 05/09/2025 | 05/09/2025 | |
| 6 | Amazon ElastiCache (Redis & Memcached) | 06/09/2025 | 06/09/2025 | |


### Week 6 Achievements:

Successfully completed all Week 6 objectives with strong mastery of:

* Core database concepts: Primary Key, Foreign Key, Index, Partitioning, Execution Plan, Buffer Pool, Transaction Log, Session

* Clear differentiation between:

  * RDBMS (relational, SQL, ACID) vs NoSQL (flexible schema, eventual consistency)

  * OLTP (fast transactions, row-based) vs OLAP (complex analytics, columnar, historical data)

* **Amazon RDS**:

  * Fully managed relational databases (MySQL, PostgreSQL, MariaDB, Oracle, SQL Server, Aurora)

  * Automated backups, Read Replicas, Multi-AZ failover, storage autoscaling, encryption at rest & in transit

* **Amazon Aurora**:

  * Cloud-native relational database with MySQL & PostgreSQL compatibility

  * Revolutionary storage layer for high concurrent read/write performance

  * Unique features: Backtrack, Aurora Clones, Global Database, Multi-Master

* **Amazon Redshift**:

  * Fully managed petabyte-scale data warehouse optimized for OLAP

  * MPP architecture + columnar storage

  * Leader + Compute nodes, Redshift Spectrum, concurrency scaling

* **Amazon ElastiCache**:

  * Managed Redis & Memcached

  * Automatic failure detection and replacement

  * Used as caching layer in front of databases to offload read-heavy OLTP workloads

  * Redis preferred for new applications

Hands-on completed:

* Deployed RDS Multi-AZ + Read Replica

* Created Aurora cluster with Global Database

* Built Redshift cluster and ran analytical queries

* Deployed ElastiCache Redis and integrated with sample app


