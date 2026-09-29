---
title: "Worklog Tuần 3"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---


### Mục tiêu tuần 3:

* Làm quen với các thành viên First Cloud Journey
* Hiểu các dịch vụ AWS cơ bản và thành thạo việc sử dụng AWS Management Console & AWS CLI

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Gặp gỡ và chào hỏi các thành viên FCJ <br> - Đọc và ghi chú các quy tắc và quy định thực tập | 11/08/2025 | 11/08/2025 | |
| 3 | - Tổng quan về AWS và các danh mục dịch vụ (Compute, Storage, Networking, Database, v.v.) | 12/08/2025 | 12/08/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Tạo AWS Free Tier account <br> - Học AWS Management Console & AWS CLI <br> - **Thực hành:** tạo tài khoản, cài đặt & cấu hình AWS CLI | 13/08/2025 | 13/08/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Tìm hiểu sâu về Amazon EC2 (Instance types, AMI, EBS, Key Pairs, Instance Store, User Data, Metadata, Mô hình định giá, Auto Scaling, v.v.) <br> - Các dịch vụ liên quan: Lightsail, EFS, FSx, AWS MGN | 14/08/2025 | 16/08/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - **Thực hành:** <br>&emsp; ∘ Khởi chạy EC2 instances <br>&emsp; ∘ Kết nối qua SSH/RDP <br>&emsp; ∘ Gắn EBS volume <br>&emsp; ∘ Tạo snapshots & custom AMIs | 15/08/2025 | 16/08/2025 | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 3:

Đã hoàn thành 100% các công việc đã lên kế hoạch với những điểm chính sau:

* Phát triển hiểu biết toàn diện về **Amazon EC2** như các máy chủ ảo có thể mở rộng có khả năng thay thế hoàn toàn máy chủ vật lý cho hầu hết mọi workload (web hosting, ứng dụng, database, xác thực, v.v.).

* Đạt được trình độ về cấu hình phần cứng thông qua **Instance Types** (CPU, memory, network, storage) và các khái niệm liên quan: Hypervisor (Nitro/KVM/HVM/PV), Placement Groups, và Availability Zones.

* Nắm được hiểu biết rõ ràng về **AMI (Amazon Machine Image)**: bao gồm root volume, launch permissions + block device mapping; có thể sử dụng AMI do AWS cung cấp, từ Marketplace, hoặc AMI tùy chỉnh; sao lưu thông qua tạo AMI hoặc EBS snapshots.

* Đạt được chuyên môn với **Key Pairs**: xác thực SSH cho Linux và giải mã mật khẩu Administrator được mã hóa cho Windows instances.

* Có kiến thức sâu về **Amazon EBS (Elastic Block Store)**:

  * Lưu trữ block bền vững độc lập với vòng đời EC2, kết nối qua mạng EBS riêng trong cùng AZ

  * Dòng SSD & HDD, độ sẵn sàng 99.99% thông qua replication trên nhiều nodes

  * Khả năng Multi-Attach trên các instances dựa trên Nitro

  * Sao lưu qua incremental snapshots được lưu trữ trong S3

* Hiểu về **Instance Store**: lưu trữ NVMe ephemeral hiệu suất cao được gắn vật lý vào host; dữ liệu mất khi Stop (nhưng được bảo toàn khi Reboot); lý tưởng cho cache, buffer, swap, dữ liệu tạm thời.

* Học về **User Data** scripts (Bash/PowerShell) và **Instance Metadata** để tự động hóa và tự cấu hình.

* Khám phá các mô hình định giá EC2 và Auto Scaling:

  * On-Demand, Reserved Instances, Savings Plans, Spot Instances

  * Auto Scaling Groups hỗ trợ nhiều mô hình định giá, hoạt động multi-AZ, và đăng ký tự động với Elastic Load Balancers

* Nghiên cứu các dịch vụ bổ sung:

  * **Amazon Lightsail**: VPS đơn giản chi phí thấp với data transfer được đóng gói, lý tưởng cho dev/test và workload nhẹ

  * **EFS (Elastic File System)**: NFS được quản lý hoàn toàn cho Linux, lưu trữ trả theo sử dụng, hỗ trợ truy cập on-premises qua DX/VPN

  * **FSx**: Windows File Server (SMB) được quản lý và FSx for Lustre, với deduplication tích hợp (tiết kiệm 30–50%)

  * **AWS Application Migration Service (MGN)**: replication liên tục cho lift-and-shift migration và DR từ on-premises/physical/virtual servers lên AWS

* Thành công thực hành: đã khởi chạy EC2 instances, kết nối qua SSH/RDP, gắn EBS volumes, tạo snapshots và custom AMIs.




