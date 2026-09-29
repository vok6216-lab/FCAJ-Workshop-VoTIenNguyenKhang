---
title: "Worklog Tuần 2"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---


### Mục tiêu tuần 2:

* Nắm vững kiến thức về bảo mật mạng trong AWS (Security Groups, NACL).
* Hiểu về kết nối VPC và các phương thức kết nối mạng.
* Tìm hiểu về cân bằng tải với AWS ELB và các loại Load Balancer.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu về Security Groups: <br>&emsp; + Khái niệm và đặc tính stateful <br>&emsp; + Cách tạo và cấu hình rules <br>&emsp; + Áp dụng cho Elastic Network Interface | 11/08/2025 | 11/08/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - Tìm hiểu về Network ACL (NACL): <br>&emsp; + Khái niệm và đặc tính stateless <br>&emsp; + Sự khác biệt giữa NACL và Security Groups <br>&emsp; + Cơ chế đánh giá rules từ trên xuống | 12/08/2025 | 12/08/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - **Thực hành:** <br>&emsp; + Tạo Security Group cho EC2 instance <br>&emsp; + Cấu hình NACL cho subnet <br>&emsp; + So sánh hiệu quả bảo mật giữa 2 phương pháp <br> - Tìm hiểu về VPC Flow Logs | 13/08/2025 | 13/08/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Tìm hiểu về kết nối VPC: <br>&emsp; + VPC Peering và các hạn chế <br>&emsp; + Transit Gateway <br>&emsp; + Site-to-Site VPN <br>&emsp; + AWS Direct Connect | 14/08/2025 | 14/08/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Tìm hiểu về Elastic Load Balancing: <br>&emsp; + Khái niệm ELB và các loại <br>&emsp; + Application Load Balancer (ALB) <br>&emsp; + Network Load Balancer (NLB) <br>&emsp; + Sticky Session và Health Check <br> - **Thực hành:** <br>&emsp; + Tạo ALB để phân phối traffic <br>&emsp; + Cấu hình Target Groups | 15/08/2025 | 15/08/2025 | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 2:

* Đã hiểu rõ về Security Groups và NACL:

  * Security Groups là tường lửa stateful chỉ cho phép các rules "allow"

  * NACL là tường lửa stateless được áp dụng cho subnet

  * Security Groups ảnh hưởng đến từng instance, NACL ảnh hưởng đến nhiều server trong subnet

* Đã học cách sử dụng VPC Flow Logs để giám sát lưu lượng IP trong VPC mà không cần capture nội dung packet.

* Hiểu về các phương thức kết nối VPC:

  * VPC Peering để kết nối 2 VPC, không hỗ trợ transitive routing

  * Transit Gateway để kết nối nhiều VPC và mạng on-premises

  * Site-to-Site VPN với Virtual Private Gateway và Customer Gateway

  * AWS Direct Connect với độ trễ thấp (20-30ms)

* Nắm vững kiến thức về Elastic Load Balancing:

  * 4 loại: ALB, NLB, Classic LB, Gateway LB

  * ALB hoạt động ở Layer 7, hỗ trợ HTTP/HTTPS và path-based routing

  * NLB hoạt động ở Layer 4, hỗ trợ TCP/TLS và static IP

  * Các tính năng: Health Check, Sticky Session, Access Logs

* Đã hoàn thành thực hành thành công:

  * Tạo Security Groups cho EC2 với các rules phù hợp

  * Cấu hình NACL cho subnet với thứ tự rules hợp lý

  * Thiết lập Application Load Balancer với Target Groups

  * Kiểm tra hoạt động của Load Balancer và phân phối traffic

* Có khả năng so sánh và lựa chọn giải pháp bảo mật và kết nối mạng phù hợp cho các use case cụ thể.




