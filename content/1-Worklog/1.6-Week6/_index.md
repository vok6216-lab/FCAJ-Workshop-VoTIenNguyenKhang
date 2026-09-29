---

title: "Week 6 Worklog"
date: "2026-10-19"
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
----------------------

### Week 6 Objectives:

* Master core and advanced database concepts.
* Clearly distinguish OLTP vs OLAP, RDBMS vs NoSQL.
* Gain full proficiency in AWS database services: RDS, Aurora, Redshift, ElastiCache.

### Tasks to be carried out this week:

| Day | Task                                                                         | Start Date       | Completion Date | Reference Material                      |
| --- | ---------------------------------------------------------------------------- | ---------------- | --------------- | --------------------------------------- |
| 1–2 | Core DB concepts: PK, FK, Index, Partition, Query Plan, Buffer, Log, Session | 10/19–10/20/2026 | 10/20/2026      | https://cloudjourney.awsstudygroup.com/ |
| 3   | RDBMS vs NoSQL • OLTP vs OLAP                                                | 10/21/2026       | 10/21/2026      |                                         |
| 4   | Amazon RDS & Amazon Aurora (MySQL/PostgreSQL-compatible)                     | 10/22/2026       | 10/22/2026      |                                         |
| 5   | Amazon Redshift – Managed Data Warehouse & OLAP                              | 10/23/2026       | 10/23/2026      |                                         |
| 6   | Amazon ElastiCache (Redis & Memcached)                                       | 10/24/2026       | 10/24/2026      |                                         |

### Week 6 Achievements:

Successfully completed all Week 6 objectives with strong mastery of:

* Core database concepts: Primary Key, Foreign Key, Index, Partitioning, Execution Plan, Buffer Pool, Transaction Log, Session.

* Clear differentiation between:

  * RDBMS (relational, SQL, ACID) vs NoSQL (flexible schema, eventual consistency).

  * OLTP (fast transactions, row-based) vs OLAP (complex analytics, columnar, historical data).

* **Amazon RDS**:

  * Fully managed relational databases (MySQL, PostgreSQL, MariaDB, Oracle, SQL Server, Aurora).

  * Automated backups, Read Replicas, Multi-AZ failover, storage autoscaling, encryption at rest & in transit.

* **Amazon Aurora**:

  * Cloud-native relational database with MySQL and PostgreSQL compatibility.

  * High-performance distributed storage layer designed for high-concurrency read/write workloads.

  * Unique features: Backtrack, Aurora Clones, Global Database, Multi-Master.

* **Amazon Redshift**:

  * Fully managed petabyte-scale data warehouse optimized for OLAP.

  * MPP architecture + columnar storage.

  * Leader + Compute nodes, Redshift Spectrum, concurrency scaling.

* **Amazon ElastiCache**:

  * Managed Redis and Memcached.

  * Automatic failure detection and replacement.

  * Used as a caching layer in front of databases to offload read-heavy OLTP workloads.

  * Redis is preferred for many new application use cases.

### Hands-on practice completed:

* Deployed RDS Multi-AZ + Read Replica.

* Created an Aurora cluster with Global Database.

* Built a Redshift cluster and ran analytical queries.

* Deployed ElastiCache Redis and integrated it with a sample application.
