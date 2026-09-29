---
title: "Worklog Tuần 4"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---


### Mục tiêu tuần 4:

* Nắm vững Amazon Simple Storage Service (S3) và hệ sinh thái của nó
* Hiểu các khái niệm object storage, storage classes, lifecycle management, bảo mật, và tối ưu hiệu suất
* Khám phá AWS Snow Family và các giải pháp hybrid storage
* Học các khái niệm disaster recovery (RTO/RPO) và chiến lược backup

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 1–2 | Tìm hiểu sâu về Amazon S3: kiến trúc, độ bền, độ sẵn sàng, storage classes, lifecycle policies, versioning, static website hosting, CORS, kiểm soát truy cập (ACL, Bucket Policy, IAM), Access Points, endpoints | 18–19/08 | 19/08/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | Tối ưu hiệu suất S3, multipart upload, thiết kế prefix, event notifications, replication (CRR/SRR) | 20/08/2025 | 20/08/2025 | |
| 4 | Amazon S3 Glacier (Instant Retrieval, Flexible Retrieval, Deep Archive), các tùy chọn retrieval (Expedited, Standard, Bulk) | 21/08/2025 | 21/08/2025 | |
| 5 | AWS Snow Family (Snowball, Snowball Edge, Snowmobile) và AWS Storage Gateway (File, Volume, Tape) | 22/08/2025 | 22/08/2025 | |
| 6 | Khái niệm disaster recovery (RTO, RPO), 4 chiến lược DR trên AWS, dịch vụ AWS Backup | 23/08/2025 | 23/08/2025 | |


### Kết quả đạt được tuần 4:

Đã hoàn thành tất cả mục tiêu tuần 4 với những kiến thức chính sau:

* Đạt được trình độ về **Amazon S3** cơ bản:

  * Object storage (không phải block/file), mô hình write-once-read-many (WORM), dung lượng tổng không giới hạn, tối đa 5 TB mỗi object

  * Được thiết kế cho độ bền 99.999999999% (11×9s) và độ sẵn sàng 99.99%

  * Dữ liệu tự động được replicate qua tối thiểu 3 Availability Zones trong một region

  * Hỗ trợ multipart upload, event notifications, static website hosting, và cấu hình CORS

* Hiểu về **S3 Storage Classes** và tối ưu chi phí:

  * S3 Standard, Standard-IA, One Zone-IA, Intelligent-Tiering, Glacier Instant Retrieval, Glacier Flexible Retrieval, Glacier Deep Archive

  * Lifecycle policies để tự động chuyển đổi hoặc hết hạn objects

* Bảo mật & kiểm soát truy cập:

  * S3 Bucket Policies, IAM Policies, S3 Access Control Lists (legacy), S3 Access Points

  * Block Public Access, VPC Endpoints cho kết nối riêng tư

* Tính năng nâng cao:

  * Versioning (bảo vệ khỏi xóa/ghi đè nhầm và ransomware)

  * Cross-Region Replication (CRR) & Same-Region Replication (SRR)

  * Tối ưu hiệu suất S3 sử dụng random prefixes để phân phối objects qua các partitions

* Phát triển hiểu biết sâu về **Amazon S3 Glacier**:

  * Lưu trữ archive chi phí thấp với ba tùy chọn retrieval:

    * Expedited (1–5 phút)

    * Standard (3–5 giờ)

    * Bulk (5–12 giờ)

* Học về **AWS Snow Family** cho di chuyển dữ liệu quy mô lớn:

  * Snowball (80 TB), Snowball Edge (100 TB + compute), Snowmobile (lên đến 100 PB mỗi xe)

* Nắm vững **AWS Storage Gateway** – hybrid storage:

  * File Gateway → S3 (NFS/SMB)

  * Volume Gateway → S3 (iSCSI, cached hoặc stored mode, snapshot to EBS)

  * Tape Gateway → Virtual Tape Library (S3/Glacier)

* Khái niệm Disaster Recovery:

  * RTO (Recovery Time Objective) – thời gian downtime tối đa chấp nhận được

  * RPO (Recovery Point Objective) – mất dữ liệu tối đa chấp nhận được

  * Bốn chiến lược DR trên AWS: Backup & Restore, Pilot Light, Warm Standby, Multi-Site Active/Active

  * AWS Backup – quản lý backup tập trung trên EBS, EC2, RDS, DynamoDB, EFS, Storage Gateway

Đã hoàn thành thực hành:

* Tạo S3 buckets với versioning, lifecycle policies, static website hosting

* Cấu hình bucket policies, CORS, và VPC endpoints

* Kiểm thử multipart upload và event triggers

* Khám phá AWS Backup console và tạo backup plans




