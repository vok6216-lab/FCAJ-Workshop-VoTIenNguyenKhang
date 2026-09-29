---
title: "Bản đề xuất"
date: 2025-09-09
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Hệ thống Quản lý Nhân sự Doanh nghiệp

## Giải pháp Quản lý Nhân sự Toàn diện cho Doanh nghiệp Hiện đại

---

## 1. Tóm tắt Điều hành

**Hệ thống Quản lý Nhân sự Doanh nghiệp** là giải pháp quản lý nhân sự tích hợp được thiết kế cho các doanh nghiệp vừa tại Việt Nam, hỗ trợ **100-500 nhân viên**. Hệ thống tự động hóa toàn bộ quy trình nhân sự từ quản lý hồ sơ, theo dõi chấm công, tính lương đến đánh giá hiệu suất. Đây là **dự án nội bộ** được phát triển bởi nhóm, tập trung vào **MVP với chi phí tối ưu dưới $100/tháng** trong giai đoạn đầu (100 nhân viên), sử dụng **kiến trúc serverless AWS** với Lambda, API Gateway, DynamoDB để đảm bảo hiệu suất cao và chi phí thấp.

---

## 2. Tuyên bố Vấn đề

### Vấn đề Hiện tại

- Các doanh nghiệp Việt Nam sử dụng **Excel** hoặc phần mềm nhân sự cũ, gây lãng phí thời gian và sai sót.
- Các quy trình thủ công (chấm công, tính lương) **không được tích hợp**.
- Không có **quy trình phê duyệt tự động**.
- Khó quản lý **phân quyền chi tiết**.
- Báo cáo yếu, **không thời gian thực**.
- Chi phí cao cho các giải pháp SAP, Workday.

### Giải pháp Đề xuất

Hệ thống sử dụng **Kiến trúc Serverless AWS** để tối ưu chi phí:

- **Tính toán:** AWS Lambda (trả theo sử dụng, không có chi phí nhàn rỗi).
- **API:** API Gateway REST API.
- **Cơ sở dữ liệu:** DynamoDB (thanh toán theo nhu cầu).
- **Cache:** ElastiCache Redis (cache.t3.micro) - tùy chọn cho giai đoạn 2.
- **Xác thực:** **AWS Cognito** (miễn phí <50K MAU).
- **Lưu trữ:** S3 cho tài liệu, CloudFront CDN.
- **CI/CD:** **GitHub Actions** cho triển khai tự động.
- **Giám sát:** **CloudWatch** (miễn phí).
- **Bảo mật:** Route 53, WAF (quy tắc tối ưu chi phí), IAM Roles.

### Tính năng Chính

- **Single Sign-On** (Google, Microsoft 365).
- **RBAC chi tiết** (Admin, Manager, Employee, Payroll Officer).
- **Check-in/out với xác thực GPS**.
- **Tính lương tự động** với công thức linh hoạt.
- **Quy trình phê duyệt** (nghỉ phép, điều chỉnh lương).
- **Ứng dụng di động** (React Native) cho chấm công.
- **Bảng điều khiển báo cáo thời gian thực**.
- Nhật ký kiểm toán toàn diện.

### Lợi ích

- Tiết kiệm **70%** thời gian xử lý nhân sự thủ công.
- Giảm **90%** lỗi nhập liệu.
- Chi phí chỉ **$45-70/tháng** cho 100 nhân viên (rẻ hơn 90% so với SAP/Workday).
- **Phát triển nội bộ** - không có chi phí thuê ngoài.

---

## 3. Kiến trúc Giải pháp

Đây là sơ đồ kiến trúc đám mây của hệ thống:

![Kiến trúc Hệ thống HR](/images/2-Proposal/proposalaws1.jpg)

### Dịch vụ AWS Sử dụng

| Dịch vụ AWS                    | Chức năng Chính                                   |
| :----------------------------- | :------------------------------------------------- |
| **AWS Lambda**                 | Logic API backend (Node.js 20.x)                   |
| **API Gateway**                | Endpoint REST API, xác thực yêu cầu             |
| **Amazon DynamoDB**            | Cơ sở dữ liệu NoSQL (thanh toán theo nhu cầu)                 |
| **AWS Cognito**                | Xác thực, SSO (Google/Microsoft), JWT tokens |
| **Amazon S3**                  | Lưu trữ tài liệu (CV, hợp đồng, bảng lương)         |
| **CloudFront**                 | CDN cho tài sản tĩnh và S3                       |
| **Route 53**                   | Quản lý DNS                                     |
| **AWS WAF** (tùy chọn Giai đoạn 2) | Bảo vệ API                                     |
| **CloudWatch**                 | Logs, giám sát (miễn phí)                       |
| **Secrets Manager**            | API keys, thông tin xác thực                              |

### Thiết kế Thành phần

#### Lớp Xác thực

- Cognito User Pools với JWT (RS256).
- Lambda authorizer cho API Gateway.
- MFA tùy chọn (SMS/TOTP) - Giai đoạn 2.

#### Lớp API

- **Các hàm AWS Lambda** (Node.js) được triển khai qua GitHub Actions.
- API Gateway REST API với định tuyến dựa trên resource.
- Giới hạn tốc độ (10 yêu cầu/giây).
- CORS được cấu hình cho web/mobile.

#### Logic Nghiệp vụ (Các hàm Lambda)

- Quản lý nhân viên (CRUD, hợp đồng, kỹ năng).
- Theo dõi chấm công (check-in/out, xác thực GPS).
- Quản lý nghỉ phép (yêu cầu, phê duyệt, số dư).
- Công cụ tính lương (tính lương, thuế, bảo hiểm).
- Đánh giá hiệu suất (theo dõi KPI).
- Thông báo email (SES miễn phí).

#### Lớp Dữ liệu - Bảng DynamoDB

- **Users** - GSI trên email
- **Employees** - GSI trên department_id
- **Departments**
- **AttendanceLogs** - GSI trên employee_id + date
- **LeaveRequests** - GSI trên employee_id + status
- **PayrollRecords** - GSI trên employee_id + month
- **Approvals** - GSI trên approver_id + status

#### Lớp Lưu trữ

- S3 Standard cho tài liệu mới (<30 ngày).
- S3 Lifecycle → Glacier Deep Archive (>90 ngày).
- Presigned URLs để upload/download an toàn.
- CloudFront distribution cho static web hosting.

#### Frontend

- **Next.js 14** (React 18) + TypeScript - Static export.
- Material-UI components.
- Được lưu trữ trên **CloudFront + S3** (không có chi phí server).
- Ứng dụng di động: **React Native** (Expo) với AsyncStorage.

#### Pipeline CI/CD

- Workflow **GitHub Actions**:
  - Build các hàm Lambda → Gói ZIP
  - Triển khai lên Lambda qua AWS CLI
  - Cập nhật cấu hình API Gateway
  - Triển khai frontend lên S3
- Kiểm thử đơn vị Jest tự động.

---

## 4. Triển khai Kỹ thuật

### Giai đoạn 1: MVP Core (Tháng 1-2)

- **Tháng 1:**
  - Thiết lập AWS (Cognito, bảng DynamoDB, S3, Lambda).
  - Xác thực + UI Đăng nhập.
  - API CRUD Nhân viên + bảng điều khiển admin.
- **Tháng 2:**
  - API check-in/out chấm công với GPS.
  - MVP ứng dụng di động (React Native).
  - Quy trình yêu cầu nghỉ phép.
  - Bảng điều khiển báo cáo cơ bản.

### Giai đoạn 2: Tính lương & Tự động hóa (Tháng 3-4)

- **Tháng 3:**
  - Công cụ tính lương (Lambda).
  - Tạo bảng lương (PDF qua Lambda layer).
  - Quy trình phê duyệt.
- **Tháng 4:**
  - Thông báo email (SES).
  - Ghi nhật ký kiểm toán vào DynamoDB.
  - Xuất báo cáo (CSV).
  - Tối ưu hóa hiệu suất.

### Giai đoạn 3: Tính năng Nâng cao (Tháng 5-6)

- Module đánh giá hiệu suất.
- Theo dõi đào tạo.
- Bảng điều khiển phân tích nâng cao.
- Tăng cường bảo mật.
- Kiểm thử tải & tối ưu hóa.
- Đào tạo người dùng & tài liệu.

### Tech Stack

| Thành phần                  | Công nghệ/Dịch vụ                               |
| :------------------------- | :----------------------------------------------- |
| **Backend**                | Node.js 20.x, AWS Lambda, AWS SDK v3             |
| **Cơ sở dữ liệu**               | DynamoDB (mẫu thiết kế single-table)           |
| **Frontend**               | Next.js 14, React 18, TypeScript, Material-UI v5 |
| **Mobile**                 | React Native (Expo), AsyncStorage                |
| **Infrastructure as Code** | AWS SAM / Serverless Framework                   |
| **CI/CD**                  | GitHub Actions                                   |

---

## 5. Lộ trình & Mốc

| Tháng   | Giai đoạn                | Kết quả Chính                                  |
| :------ | :------------------- | :------------------------------------------------ |
| **1-2** | MVP Core             | Xác thực, Quản lý nhân viên, Ứng dụng di động chấm công  |
| **3-4** | Tính lương & Tự động hóa | Công cụ tính lương, quy trình phê duyệt, thông báo |
| **5-6** | Nâng cao & Ra mắt    | Phân tích, đánh giá hiệu suất, UAT, go-live      |

---

## 6. Ước tính Ngân sách

### Chi phí AWS Hàng tháng (Giai đoạn 1: 100 nhân viên, ~5,000 lời gọi API/ngày)

#### Kiến trúc Serverless - Tối ưu Chi phí

| Dịch vụ                                                          | Cấu hình                                 | Chi phí/Tháng |
| :--------------------------------------------------------------- | :-------------------------------------------- | ---------: |
| **AWS Lambda**                                                   | 150K lời gọi, 512MB, 500ms trung bình            |         $0 |
| ↳ _Miễn phí: 1M yêu cầu + 400K GB-giây/tháng_               | (Trong miễn phí)                            |            |
| **API Gateway**                                                  | 150K yêu cầu REST API/tháng                  |      $0.15 |
| ↳ _$3.50 mỗi triệu sau 1M đầu tiên (miễn phí năm 1)_          |                                               |            |
| **DynamoDB**                                                     | Theo nhu cầu, 5GB lưu trữ, 1M đọc, 500K ghi |      $3.50 |
| ↳ _Lưu trữ: $1.25/GB ($6.25) + Đọc: $0.25/M + Ghi: $1.25/M_ |                                               |            |
| **S3 Storage**                                                   | 20GB tài liệu (100 người dùng)                    |      $0.46 |
| **S3 Requests**                                                  | 20K PUT, 100K GET/tháng                       |      $0.14 |
| **S3 Glacier (lưu trữ)**                                         | 10GB tài liệu cũ                            |      $0.10 |
| **CloudFront**                                                   | 10GB chuyển, 200K yêu cầu                  |      $1.00 |
| **Route 53**                                                     | 1 hosted zone + 1M truy vấn                    |      $0.90 |
| **CloudWatch Logs**                                              | 2GB logs/tháng                                |         $0 |
| ↳ _(5GB đầu tiên miễn phí)_                                             | (Trong miễn phí)                            |            |
| **Secrets Manager**                                              | 2 secrets                                     |      $0.80 |
| **SES (email)**                                                  | 500 email/tháng                              |      $0.05 |
| **Cognito**                                                      | <50K MAU                                      |         $0 |
| ↳ _(Miễn phí)_                                                 | (Trong miễn phí)                            |            |
| **Data Transfer OUT**                                            | 5GB ra internet                               |      $0.45 |
| **Dự phòng (10%)**                                            | Buffer                                        |      $0.75 |
|                                                                  |                                               |            |
| **TỔNG AWS/THÁNG (100 người dùng)**                                  |                                               | **~$8.30** |

#### Chi phí Khi Mở rộng lên 200 Người dùng (Giai đoạn 2)

| Dịch vụ                                  | Thay đổi                               |  Chi phí/Tháng |
| :--------------------------------------- | :------------------------------------ | ----------: |
| Lambda                                   | 300K lời gọi (vẫn trong miễn phí) |          $0 |
| API Gateway                              | 300K yêu cầu                         |       $0.30 |
| DynamoDB                                 | 10GB, 2M đọc, 1M ghi             |       $9.50 |
| S3 + CloudFront                          | 40GB lưu trữ, 20GB chuyển           |       $2.50 |
| Route 53, Secrets, SES, Transfer         | (tương tự)                             |       $2.20 |
| **ElastiCache Redis**                    | cache.t3.micro (tùy chọn)             |      $12.50 |
| **AWS WAF**                              | Bảo vệ cơ bản (tùy chọn)           |       $7.00 |
| Dự phòng                              |                                       |       $3.40 |
|                                          |                                       |             |
| **TỔNG (200 người dùng, có cache + WAF)**  |                                       | **~$37.40** |
| **TỔNG (200 người dùng, không cache/WAF)** |                                       | **~$17.90** |

#### Chi phí Khi Mở rộng lên 500 Người dùng (Giai đoạn 3)

| Lambda + API Gateway | 750K lời gọi | $3.50 |
| DynamoDB | 25GB, 5M đọc, 2.5M ghi | $32.50 |
| S3 + CloudFront + Transfer | 100GB lưu trữ, 50GB CDN | $7.50 |
| ElastiCache Redis | cache.t3.small | $25.00 |
| AWS WAF | 2 quy tắc | $8.00 |
| Route 53, Secrets, SES, khác | | $3.00 |
| Dự phòng | | $8.00 |
| | | |
| **TỔNG (500 người dùng)** | | **~$87.50** |

### Tóm tắt Chi phí Lưu trữ theo Giai đoạn

| Giai đoạn              | Người dùng | Chi phí/Tháng |     Chi phí/Năm |
| :----------------- | :---: | ---------: | ------------: |
| **Giai đoạn 1 MVP**    |  100  |  **$8-12** | **~$100-150** |
| **Giai đoạn 2 Tăng trưởng** |  200  | **$18-38** | **~$220-450** |
| **Giai đoạn 3 Mở rộng**  |  500  | **$88-95** |   **~$1,050** |

### Chi phí Phát triển (Nhóm nội bộ - KHÔNG có chi phí thuê ngoài)

**Giả định:** Nhóm nội bộ đã có lương cố định, chỉ tính chi phí AWS và công cụ

| Mục                                       |     Chi phí |
| :----------------------------------------- | -------: |
| Lưu trữ AWS (6 tháng dev/staging @ $5/tháng) |      $30 |
| GitHub Pro (nhóm 5 người)                     |       $0 |
| ↳ _(Có thể dùng miễn phí)_                    |          |
| Tên miền (.com)                         | $12/năm |
| Thư viện bên thứ ba (tùy chọn)           |       $0 |
| **TỔNG CHI PHÍ PHÁT TRIỂN**                 | **~$42** |

**Lưu ý:** Chi phí nhân sự KHÔNG được tính vì đây là nhóm nội bộ với lương cố định

### Chi phí Vận hành Hàng năm (sau khi ra mắt)

| Mục                                          |     Chi phí/Năm |
| :-------------------------------------------- | ------------: |
| Lưu trữ AWS (Giai đoạn 1: 100 người dùng)              |      $100-150 |
| Dịch vụ bên thứ ba (SMS cho MFA - tùy chọn) |          $100 |
| Gia hạn tên miền                                |           $12 |
| **TỔNG VẬN HÀNH/NĂM (Giai đoạn 1)**            | **~$212-262** |

### Phân tích ROI (Dự án nội bộ)

**Đầu tư Ban đầu:**

- Thiết lập + Công cụ dev: ~$42
- AWS (6 tháng dev): ~$30
- **Tổng ban đầu: ~$72**

**Chi phí Vận hành Năm Đầu:**

- Giai đoạn 1 (6 tháng, 100 người dùng): $60
- Giai đoạn 2 (6 tháng, 200 người dùng): $150
- **Tổng Năm 1: ~$210**

**Tổng Chi phí Năm 1: ~$282**

**Tiết kiệm so với Giải pháp Thay thế:**

- SAP SuccessFactors: $8-15/người dùng/tháng = $9,600-18,000/năm
- BambooHR: $6-10/người dùng/tháng = $7,200-12,000/năm
- Excel thủ công: 1 FTE HR admin = $12,000/năm

**Tiết kiệm Năm 1: $6,918 - $17,718**

**ROI Năm 1: 2,454% - 6,281%** 🚀

---

## 7. Đánh giá Rủi ro & Giảm thiểu

| Rủi ro                    | Tác động | Xác suất | Giảm thiểu                                            |
| :---------------------- | :----- | :---------- | :---------------------------------------------------- |
| Chi phí DynamoDB tăng đột biến    | Trung bình | Thấp         | Thanh toán theo nhu cầu, cảnh báo CloudWatch ở ngưỡng $30 |
| Lambda cold starts      | Thấp    | Trung bình      | Giữ hàm ấm, tối ưu kích thước bundle <1MB        |
| Giới hạn tốc độ API Gateway | Trung bình | Thấp         | Mặc định 10K req/s đủ, triển khai caching       |
| Phụ thuộc nhà cung cấp (AWS)    | Trung bình | Cao        | Sử dụng Serverless Framework để dễ di chuyển              |
| Đường cong học tập nhóm     | Thấp    | Trung bình      | Bắt đầu với 1-2 hàm Lambda, mở rộng dần dần     |

### Thực hành Tối ưu Chi phí Tốt nhất

- **Lambda:** Kích thước bundle <1MB, tái sử dụng kết nối, tránh cold starts.
- **DynamoDB:** Thiết kế single-table, sử dụng GSI cẩn thận, thanh toán theo nhu cầu.
- **S3:** Chính sách lifecycle đến Glacier, presigned URLs, CloudFront caching.
- **API Gateway:** Response caching (30-60s), throttling.
- **CloudWatch:** Giữ log 7 ngày, lọc log không cần thiết.

---

## 8. Kết quả Mong đợi

### Cải tiến Kỹ thuật

- **85%** quy trình nhân sự được tự động hóa.
- Bảng điều khiển thời gian thực với dữ liệu < 5 giây.
- **< 1s** thời gian phản hồi API (P95) với Lambda.
- **70%** nhân viên sử dụng ứng dụng di động.
- Không cần bảo trì server.
- **Khả năng mở rộng vô hạn** với serverless.

### Giá trị Kinh doanh

- Nhóm nhân sự giảm **60%** khối lượng công việc thủ công.
- Sự hài lòng nhân viên tăng **40%** (tự phục vụ).
- **100%** dấu vết kiểm toán cho tuân thủ.
- Độ chính xác tính lương **99.5%**.
- **Tiết kiệm chi phí $6,900-17,700/năm** so với giải pháp thay thế.
- Chi phí vận hành **chỉ $8-12/tháng** cho 100 người dùng.

### Tầm nhìn Dài hạn

- Mở rộng lên 500 người dùng với chi phí ~$88/tháng.
- Tích hợp AI/ML (AWS Bedrock) cho phân tích dự đoán.
- Hoạt động đa chi nhánh.
- Sản phẩm SaaS tiềm năng.

---

## 9. Kết luận

Hệ thống Quản lý Nhân sự với **Kiến trúc Serverless** cung cấp:

✅ **Chi phí cực thấp:** Chỉ $8-12/tháng cho 100 người dùng Giai đoạn 1  

✅ **Không có chi phí trước:** ~$72 thiết lập, không có chi phí thuê ngoài  

✅ **ROI lớn:** Tiết kiệm $6,900-17,700/năm so với giải pháp thay thế  

✅ **Có thể mở rộng:** Trả theo sử dụng, tự động mở rộng lên 500+ người dùng  

✅ **Không cần bảo trì:** Serverless = không quản lý server  

✅ **Phát triển nhanh:** 6 tháng MVP → sản xuất

Đây là **giải pháp lý tưởng cho startup/SME** với nhóm nội bộ muốn xây dựng hệ thống nhân sự hiện đại mà không cần đầu tư lớn.
