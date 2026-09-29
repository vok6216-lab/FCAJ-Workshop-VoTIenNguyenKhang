---

title: "Nhật ký công việc Tuần 5"
date: "2026-10-12"
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
----------------------

### Mục tiêu Tuần 5:

* Nắm vững Mô hình Trách nhiệm Chung của AWS (AWS Shared Responsibility Model).
* Hiểu sâu về quản lý danh tính và quyền truy cập trên AWS.
* Thành thạo các dịch vụ IAM, Organizations, Identity Center, Cognito, KMS và Security Hub.

### Các công việc cần thực hiện trong tuần:

| Ngày | Công việc                                                                                  | Ngày bắt đầu     | Ngày hoàn thành | Tài liệu tham khảo                      |
| ---- | ------------------------------------------------------------------------------------------ | ---------------- | --------------- | --------------------------------------- |
| 1–2  | Mô hình Trách nhiệm Chung + kiến thức cơ bản về IAM (Root, Users, Groups, Policies, Roles) | 12/10–13/10/2026 | 13/10/2026      | https://cloudjourney.awsstudygroup.com/ |
| 3    | IAM Policies (Identity-based và Resource-based), cơ chế đánh giá Policy, Explicit Deny     | 14/10/2026       | 14/10/2026      |                                         |
| 4    | IAM Roles, Trust Policy, STS, AssumeRole, truy cập Cross-account, Service Roles            | 15/10/2026       | 15/10/2026      |                                         |
| 5    | AWS Organizations, OU, SCP, Consolidated Billing + AWS Identity Center                     | 16/10/2026       | 16/10/2026      |                                         |
| 6    | Amazon Cognito, AWS KMS, AWS Security Hub                                                  | 17/10/2026       | 17/10/2026      |                                         |

### Kết quả đạt được trong Tuần 5:

Đã hoàn thành tất cả các mục tiêu của Tuần 5 và đạt được những kiến thức, kỹ năng chính sau:

* **AWS Shared Responsibility Model**: AWS chịu trách nhiệm bảo mật cơ sở hạ tầng của đám mây, trong khi khách hàng chịu trách nhiệm bảo mật những gì họ triển khai trên đám mây. Mức độ trách nhiệm thay đổi tùy theo loại dịch vụ (Infrastructure → Container → Abstracted Services).

* **Bảo vệ Root Account**: Đã kích hoạt MFA, không sử dụng Root Account cho các tác vụ hằng ngày, lưu trữ thông tin xác thực an toàn và tạo IAM Administrator User để sử dụng thay thế.

* **Nắm vững AWS IAM**:

  * Các loại Principal: Root, IAM Users, IAM Roles, Federated Users và AWS Services.

  * Các loại Policy và cơ chế đánh giá: Explicit Deny được ưu tiên cao nhất, tiếp theo là Allow; nếu không có Allow thì mặc định là Deny.

  * Sử dụng IAM Roles + Trust Policy + STS để cung cấp quyền truy cập tạm thời, theo nguyên tắc Least Privilege và hỗ trợ truy cập Cross-account.

  * Tìm hiểu Cross-account Delegation và Service-linked Roles.

* **AWS Organizations**:

  * Quản lý tập trung nhiều AWS Account thông qua Organizational Units (OUs).

  * Sử dụng Service Control Policies (SCPs) để thiết lập các giới hạn và nguyên tắc về quyền truy cập.

  * Quản lý Consolidated Billing để tổng hợp chi phí của nhiều tài khoản.

* **AWS Identity Center (trước đây là AWS SSO)**:

  * Tích hợp các nguồn danh tính (Built-in, AWS Managed Microsoft AD, AD Connector và External IdP).

  * Permission Sets → tự động tạo và cấp phát IAM Roles trong các Member Account.

* **Amazon Cognito**:

  * User Pools dùng cho chức năng đăng ký và đăng nhập người dùng.

  * Identity Pools dùng để cấp phát AWS Credentials tạm thời.

* **AWS KMS**:

  * Tìm hiểu Customer Managed Keys (CMK), tuân thủ tiêu chuẩn FIPS 140-2.

  * Sử dụng mô hình Data Key để mã hóa dữ liệu quy mô lớn.

* **AWS Security Hub**:

  * Kiểm tra bảo mật liên tục dựa trên AWS Foundational Security Best Practices, CIS, PCI DSS và các tiêu chuẩn bảo mật khác.

  * Theo dõi Security Score và các Security Findings được ưu tiên xử lý.

### Hoàn thành phần thực hành:

* Xây dựng cấu trúc AWS Organizations hoàn chỉnh với SCPs.

* Cấu hình AWS Identity Center với Permission Sets.

* Triển khai quy trình xác thực người dùng bằng Amazon Cognito.

* Sử dụng KMS để mã hóa các tài nguyên.

* Kích hoạt và phân tích các Security Findings trong Security Hub.
