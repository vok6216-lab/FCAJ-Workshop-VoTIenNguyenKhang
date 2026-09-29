---
title: "Worklog Tuần 6"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---


### Mục tiêu tuần 6:

* Nắm vững các khái niệm database cơ bản và nâng cao
* Phân biệt rõ ràng OLTP vs OLAP, RDBMS vs NoSQL
* Thành thạo các dịch vụ database AWS: RDS, Aurora, Redshift, ElastiCache

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 1–2 | Khái niệm DB cơ bản: PK, FK, Index, Partition, Query Plan, Buffer, Log, Session | 01–02/09/2025 | 02/09/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | RDBMS vs NoSQL • OLTP vs OLAP | 03/09/2025 | 03/09/2025 | |
| 4 | Amazon RDS & Amazon Aurora (tương thích MySQL/PostgreSQL) | 04/09/2025 | 04/09/2025 | |
| 5 | Amazon Redshift – Managed Data Warehouse & OLAP | 05/09/2025 | 05/09/2025 | |
| 6 | Amazon ElastiCache (Redis & Memcached) | 06/09/2025 | 06/09/2025 | |


### Kết quả đạt được tuần 6:

Đã hoàn thành tất cả mục tiêu tuần 6 với trình độ vững chắc về:

* Khái niệm database cơ bản: Primary Key, Foreign Key, Index, Partitioning, Execution Plan, Buffer Pool, Transaction Log, Session

* Phân biệt rõ ràng giữa:

  * RDBMS (quan hệ, SQL, ACID) vs NoSQL (schema linh hoạt, eventual consistency)

  * OLTP (giao dịch nhanh, row-based) vs OLAP (phân tích phức tạp, columnar, dữ liệu lịch sử)

* **Amazon RDS**:

  * Database quan hệ được quản lý hoàn toàn (MySQL, PostgreSQL, MariaDB, Oracle, SQL Server, Aurora)

  * Backup tự động, Read Replicas, Multi-AZ failover, storage autoscaling, mã hóa at rest & in transit

* **Amazon Aurora**:

  * Database quan hệ cloud-native với tương thích MySQL & PostgreSQL

  * Lớp lưu trữ cách mạng cho hiệu suất đọc/ghi đồng thời cao

  * Tính năng độc đáo: Backtrack, Aurora Clones, Global Database, Multi-Master

* **Amazon Redshift**:

  * Data warehouse quy mô petabyte được quản lý hoàn toàn tối ưu cho OLAP

  * Kiến trúc MPP + lưu trữ columnar

  * Leader + Compute nodes, Redshift Spectrum, concurrency scaling

* **Amazon ElastiCache**:

  * Redis & Memcached được quản lý

  * Phát hiện và thay thế lỗi tự động

  * Được sử dụng như lớp cache phía trước database để giảm tải workload OLTP đọc nhiều

  * Redis được ưa chuộng cho ứng dụng mới

Đã hoàn thành thực hành:

* Triển khai RDS Multi-AZ + Read Replica

* Tạo Aurora cluster với Global Database

* Xây dựng Redshift cluster và chạy các truy vấn phân tích

* Triển khai ElastiCache Redis và tích hợp với ứng dụng mẫu




