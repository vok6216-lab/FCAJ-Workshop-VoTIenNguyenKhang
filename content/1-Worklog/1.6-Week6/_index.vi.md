---

title: "Nhật ký công việc Tuần 6"
date: "2026-10-19"
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
----------------------

### Mục tiêu Tuần 6:

* Nắm vững các khái niệm cơ bản và nâng cao về cơ sở dữ liệu.
* Phân biệt rõ OLTP và OLAP, RDBMS và NoSQL.
* Thành thạo các dịch vụ cơ sở dữ liệu của AWS: RDS, Aurora, Redshift, ElastiCache.

### Các công việc cần thực hiện trong tuần:

| Ngày | Công việc                                                                                         | Ngày bắt đầu     | Ngày hoàn thành | Tài liệu tham khảo                      |
| ---- | ------------------------------------------------------------------------------------------------- | ---------------- | --------------- | --------------------------------------- |
| 1–2  | Các khái niệm cơ bản về cơ sở dữ liệu: PK, FK, Index, Partition, Query Plan, Buffer, Log, Session | 19/10–20/10/2026 | 20/10/2026      | https://cloudjourney.awsstudygroup.com/ |
| 3    | RDBMS và NoSQL • OLTP và OLAP                                                                     | 21/10/2026       | 21/10/2026      |                                         |
| 4    | Amazon RDS & Amazon Aurora (tương thích MySQL/PostgreSQL)                                         | 22/10/2026       | 22/10/2026      |                                         |
| 5    | Amazon Redshift – Kho dữ liệu được quản lý (Managed Data Warehouse) & OLAP                        | 23/10/2026       | 23/10/2026      |                                         |
| 6    | Amazon ElastiCache (Redis & Memcached)                                                            | 24/10/2026       | 24/10/2026      |                                         |

### Kết quả đạt được trong Tuần 6:

Đã hoàn thành tất cả các mục tiêu của Tuần 6 và đạt được những kiến thức, kỹ năng chính sau:

* Nắm vững các khái niệm cơ bản về cơ sở dữ liệu: Primary Key, Foreign Key, Index, Partitioning, Execution Plan, Buffer Pool, Transaction Log và Session.

* Phân biệt rõ:

  * **RDBMS** (cơ sở dữ liệu quan hệ, SQL, ACID) và **NoSQL** (schema linh hoạt, eventual consistency).

  * **OLTP** (giao dịch nhanh, xử lý theo từng dòng) và **OLAP** (phân tích phức tạp, lưu trữ theo cột, dữ liệu lịch sử).

* **Amazon RDS**:

  * Dịch vụ cơ sở dữ liệu quan hệ được quản lý hoàn toàn, hỗ trợ MySQL, PostgreSQL, MariaDB, Oracle, SQL Server và Aurora.

  * Hỗ trợ Automated Backups, Read Replicas, Multi-AZ Failover, tự động mở rộng dung lượng lưu trữ và mã hóa dữ liệu khi lưu trữ cũng như khi truyền tải.

* **Amazon Aurora**:

  * Cơ sở dữ liệu quan hệ Cloud-native tương thích với MySQL và PostgreSQL.

  * Sử dụng lớp lưu trữ phân tán hiệu năng cao, được thiết kế để xử lý workload đọc/ghi đồng thời lớn.

  * Các tính năng nổi bật: Backtrack, Aurora Clones, Global Database và Multi-Master.

* **Amazon Redshift**:

  * Kho dữ liệu được quản lý hoàn toàn ở quy mô Petabyte, được tối ưu cho OLAP.

  * Sử dụng kiến trúc MPP kết hợp với Columnar Storage.

  * Bao gồm Leader Node và Compute Nodes, cùng các tính năng Redshift Spectrum và Concurrency Scaling.

* **Amazon ElastiCache**:

  * Dịch vụ Redis và Memcached được AWS quản lý.

  * Hỗ trợ tự động phát hiện và thay thế khi xảy ra lỗi.

  * Được sử dụng như một lớp Cache phía trước Database nhằm giảm tải cho các workload OLTP có nhiều thao tác đọc.

  * Redis được ưu tiên sử dụng cho nhiều trường hợp ứng dụng mới.

### Hoàn thành phần thực hành:

* Triển khai RDS Multi-AZ + Read Replica.

* Tạo Aurora Cluster với Global Database.

* Xây dựng Redshift Cluster và thực hiện các truy vấn phân tích.

* Triển khai ElastiCache Redis và tích hợp với ứng dụng mẫu.
