---
title: "Nhật ký công việc Tuần 2"
date: 2026-09-21
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu Tuần 2:

- Nắm vững kiến thức về bảo mật mạng trong AWS (Security Groups, NACL).
- Hiểu về kết nối VPC và các phương thức kết nối mạng.
- Tìm hiểu về cân bằng tải với AWS ELB và các loại Load Balancer.

### Các công việc được thực hiện trong tuần:

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | ---------- | --------------- | ----------------------------------------- |
| 2   | - Tìm hiểu về Security Groups: <br>&emsp; + Khái niệm và đặc điểm stateful <br>&emsp; + Cách tạo và cấu hình các rule <br>&emsp; + Áp dụng cho Elastic Network Interface | 21/09/2026 | 21/09/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Tìm hiểu về Network ACL (NACL): <br>&emsp; + Khái niệm và đặc điểm stateless <br>&emsp; + Sự khác nhau giữa NACL và Security Groups <br>&emsp; + Cơ chế đánh giá rule từ trên xuống dưới | 22/09/2026 | 22/09/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - **Thực hành:** <br>&emsp; + Tạo Security Group cho EC2 instance <br>&emsp; + Cấu hình NACL cho subnet <br>&emsp; + So sánh hiệu quả bảo mật giữa 2 phương pháp <br> - Tìm hiểu về VPC Flow Logs | 23/09/2026 | 23/09/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Tìm hiểu về kết nối VPC: <br>&emsp; + VPC Peering và các giới hạn <br>&emsp; + Transit Gateway <br>&emsp; + Site-to-Site VPN <br>&emsp; + AWS Direct Connect | 24/09/2026 | 24/09/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Tìm hiểu về Elastic Load Balancing: <br>&emsp; + Khái niệm và các loại ELB <br>&emsp; + Application Load Balancer (ALB) <br>&emsp; + Network Load Balancer (NLB) <br>&emsp; + Sticky Session và Health Check <br> - **Thực hành:** <br>&emsp; + Tạo ALB để phân phối traffic <br>&emsp; + Cấu hình Target Groups | 25/09/2026 | 25/09/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được trong Tuần 2:

- Hiểu rõ về Security Groups và NACL:

  - Security Groups là firewall stateful, chỉ sử dụng các rule "allow"
  - NACL là firewall stateless được áp dụng cho subnet
  - Security Groups tác động đến từng instance, trong khi NACL tác động đến nhiều server trong một subnet

- Biết cách sử dụng VPC Flow Logs để theo dõi lưu lượng IP trong VPC mà không cần ghi lại nội dung của các packet.

- Hiểu các phương thức kết nối VPC:

  - VPC Peering dùng để kết nối 2 VPC và không hỗ trợ transitive routing
  - Transit Gateway dùng để kết nối nhiều VPC và mạng on-premises
  - Site-to-Site VPN sử dụng Virtual Private Gateway và Customer Gateway
  - AWS Direct Connect cung cấp kết nối với độ trễ thấp (20-30ms)

- Nắm được kiến thức về Elastic Load Balancing:

  - Có 4 loại: ALB, NLB, Classic LB, Gateway LB
  - ALB hoạt động ở Layer 7, hỗ trợ HTTP/HTTPS và path-based routing
  - NLB hoạt động ở Layer 4, hỗ trợ TCP/TLS và static IP
  - Các tính năng: Health Check, Sticky Session, Access Logs

- Hoàn thành các bài thực hành:

  - Tạo Security Groups cho EC2 với các rule phù hợp
  - Cấu hình NACL cho subnet với thứ tự rule hợp lý
  - Thiết lập Application Load Balancer với Target Groups
  - Kiểm tra hoạt động của Load Balancer và khả năng phân phối traffic

- Có khả năng so sánh và lựa chọn giải pháp bảo mật cũng như phương thức kết nối mạng phù hợp với từng trường hợp sử dụng.
