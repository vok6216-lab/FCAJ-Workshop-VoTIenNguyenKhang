---
title: "Worklog Tuần 5"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---


### Mục tiêu tuần 5:

* Nắm vững AWS Shared Responsibility Model
* Hiểu sâu về quản lý danh tính và truy cập trên AWS
* Thành thạo IAM, Organizations, Identity Center, Cognito, KMS, và Security Hub

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 1–2 | Shared Responsibility Model + IAM cơ bản (Root, Users, Groups, Policies, Roles) | 25–26/08/2025 | 26/08/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | IAM Policies (Identity-based vs Resource-based), Logic đánh giá Policy, Explicit Deny | 27/08/2025 | 27/08/2025 | |
| 4 | IAM Roles, Trust Policy, STS, AssumeRole, Cross-account access, Service roles | 28/08/2025 | 28/08/2025 | |
| 5 | AWS Organizations, OU, SCP, Consolidated Billing + AWS Identity Center | 29/08/2025 | 29/08/2025 | |
| 6 | Amazon Cognito, AWS KMS, AWS Security Hub | 30/08/2025 | 30/08/2025 | |


### Kết quả đạt được tuần 5:

Đã hoàn thành tất cả mục tiêu tuần 5 với trình độ vững chắc về:

* **AWS Shared Responsibility Model**: AWS bảo mật cloud, khách hàng bảo mật trong cloud. Trách nhiệm thay đổi theo loại dịch vụ (Infrastructure → Container → Abstracted services).

* **Bảo vệ Root Account**: Bật MFA, không bao giờ sử dụng cho công việc hàng ngày, lưu trữ credentials an toàn, tạo IAM Administrator users thay thế.

* **Thành thạo AWS IAM**:

  * Principals: Root, IAM Users, IAM Roles, Federated Users, AWS Services

  * Loại Policy và đánh giá: Explicit Deny thắng, sau đó Allow, sau đó default Deny

  * IAM Roles + Trust Policy + STS cho truy cập tạm thời, least-privilege, cross-account

  * Cross-account delegation và service-linked roles

* **AWS Organizations**:

  * Quản lý multi-account tập trung với OUs

  * Service Control Policies (SCP) để thiết lập guardrails quyền

  * Consolidated Billing

* **AWS Identity Center (trước đây là AWS SSO)**:

  * Tích hợp nguồn danh tính (built-in, AWS Managed Microsoft AD, AD Connector, external IdP)

  * Permission Sets → IAM Roles được tự động cung cấp trong member accounts

* **Amazon Cognito**:

  * User Pools cho đăng ký/đăng nhập người dùng

  * Identity Pools cho phát hành AWS credentials tạm thời

* **AWS KMS**:

  * Customer Managed Keys (CMK), tuân thủ FIPS 140-2

  * Data Key pattern cho mã hóa quy mô lớn

* **AWS Security Hub**:

  * Kiểm tra bảo mật liên tục chống lại AWS Foundational Best Practices, CIS, PCI DSS, v.v.

  * Security score và findings được ưu tiên

Đã hoàn thành thực hành:

* Xây dựng cấu trúc AWS Organizations đầy đủ với SCPs

* Cấu hình AWS Identity Center với Permission Sets

* Triển khai luồng xác thực Cognito

* Mã hóa tài nguyên với KMS

* Kích hoạt và phân tích findings từ Security Hub




