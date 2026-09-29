---

title: "Nhật ký công việc Tuần 4"
date: "2026-10-05"
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
----------------------

### Mục tiêu Tuần 4:

* Nắm vững Amazon Simple Storage Service (S3) và hệ sinh thái liên quan.
* Hiểu các khái niệm về lưu trữ đối tượng, các lớp lưu trữ, quản lý vòng đời, bảo mật và tối ưu hiệu suất.
* Tìm hiểu AWS Snow Family và các giải pháp lưu trữ hybrid.
* Tìm hiểu các khái niệm về Disaster Recovery (RTO/RPO) và các chiến lược sao lưu.

### Các công việc cần thực hiện trong tuần:

| Ngày | Công việc                                                                                                                                                                                                                              | Ngày bắt đầu     | Ngày hoàn thành | Tài liệu tham khảo                      |
| ---- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- | --------------- | --------------------------------------- |
| 1–2  | Tìm hiểu chuyên sâu về Amazon S3: kiến trúc, độ bền dữ liệu, tính sẵn sàng, các lớp lưu trữ, chính sách vòng đời, versioning, lưu trữ website tĩnh, CORS, kiểm soát quyền truy cập (ACL, Bucket Policy, IAM), Access Points, Endpoints | 05/10–06/10/2026 | 06/10/2026      | https://cloudjourney.awsstudygroup.com/ |
| 3    | Tối ưu hiệu suất S3, Multipart Upload, thiết kế Prefix, Event Notifications, Replication (CRR/SRR)                                                                                                                                     | 07/10/2026       | 07/10/2026      |                                         |
| 4    | Amazon S3 Glacier (Instant Retrieval, Flexible Retrieval, Deep Archive), các tùy chọn truy xuất dữ liệu (Expedited, Standard, Bulk)                                                                                                    | 08/10/2026       | 08/10/2026      |                                         |
| 5    | AWS Snow Family (Snowball, Snowball Edge, Snowmobile) và AWS Storage Gateway (File, Volume, Tape)                                                                                                                                      | 09/10/2026       | 09/10/2026      |                                         |
| 6    | Các khái niệm về Disaster Recovery (RTO, RPO), 4 chiến lược DR trên AWS, dịch vụ AWS Backup                                                                                                                                            | 10/10/2026       | 10/10/2026      |                                         |

### Kết quả đạt được trong Tuần 4:

Đã hoàn thành tất cả các mục tiêu của Tuần 4 với những kiến thức chính đạt được như sau:

* Nắm vững các kiến thức cơ bản về **Amazon S3**:

  * Là dịch vụ lưu trữ đối tượng (Object Storage), không phải Block Storage hoặc File Storage; sử dụng mô hình write-once-read-many (WORM), tổng dung lượng lưu trữ không giới hạn và kích thước tối đa 5 TB cho mỗi object.

  * Được thiết kế với độ bền dữ liệu đạt 99,999999999% (11×9s) và tính sẵn sàng đạt 99,99%.

  * Dữ liệu được tự động sao chép trên tối thiểu 3 Availability Zone trong một Region.

  * Hỗ trợ Multipart Upload, Event Notifications, Static Website Hosting và cấu hình CORS.

* Hiểu về **S3 Storage Classes** và tối ưu chi phí:

  * S3 Standard, Standard-IA, One Zone-IA, Intelligent-Tiering, Glacier Instant Retrieval, Glacier Flexible Retrieval và Glacier Deep Archive.

  * Sử dụng Lifecycle Policies để tự động chuyển đổi object giữa các lớp lưu trữ hoặc tự động xóa object khi hết thời hạn.

* Hiểu về **bảo mật và kiểm soát quyền truy cập**:

  * S3 Bucket Policies, IAM Policies, S3 Access Control Lists (ACL - cơ chế cũ), S3 Access Points.

  * Block Public Access và VPC Endpoints để thiết lập kết nối riêng tư.

* Tìm hiểu các tính năng nâng cao:

  * Versioning giúp bảo vệ dữ liệu khỏi việc vô tình xóa hoặc ghi đè và hỗ trợ giảm tác động của ransomware.

  * Cross-Region Replication (CRR) và Same-Region Replication (SRR).

  * Tối ưu hiệu suất S3 bằng cách sử dụng các Prefix ngẫu nhiên để phân phối object trên nhiều partition.

* Hiểu toàn diện về **Amazon S3 Glacier**:

  * Dịch vụ lưu trữ dữ liệu lưu trữ dài hạn với chi phí thấp, cung cấp ba tùy chọn truy xuất dữ liệu:

    * Expedited (1–5 phút)

    * Standard (3–5 giờ)

    * Bulk (5–12 giờ)

* Tìm hiểu **AWS Snow Family** phục vụ việc di chuyển dữ liệu quy mô lớn:

  * Snowball (80 TB), Snowball Edge (100 TB + khả năng tính toán), Snowmobile (lên đến 100 PB trên mỗi xe).

* Nắm vững **AWS Storage Gateway** – giải pháp lưu trữ hybrid:

  * File Gateway → S3 (NFS/SMB).

  * Volume Gateway → S3 (iSCSI, chế độ cached hoặc stored, snapshot sang EBS).

  * Tape Gateway → Virtual Tape Library (S3/Glacier).

* Hiểu các khái niệm về **Disaster Recovery**:

  * RTO (Recovery Time Objective) – thời gian ngừng hoạt động tối đa có thể chấp nhận.

  * RPO (Recovery Point Objective) – lượng dữ liệu tối đa có thể chấp nhận bị mất.

  * Bốn chiến lược AWS DR: Backup & Restore, Pilot Light, Warm Standby, Multi-Site Active/Active.

  * AWS Backup – quản lý sao lưu tập trung cho EBS, EC2, RDS, DynamoDB, EFS và Storage Gateway.

### Hoàn thành phần thực hành:

* Tạo S3 Bucket với Versioning, Lifecycle Policies và Static Website Hosting.

* Cấu hình Bucket Policies, CORS và VPC Endpoints.

* Thực hành Multipart Upload và Event Triggers.

* Tìm hiểu AWS Backup Console và tạo Backup Plans.
