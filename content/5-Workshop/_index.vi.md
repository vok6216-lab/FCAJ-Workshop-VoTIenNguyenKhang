---
title: "Workshop"
date: 2025-09-09
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Xây dựng REST API Serverless với AWS Lambda và API Gateway

#### Tổng quan

Trong workshop này, bạn sẽ học cách xây dựng một REST API serverless sử dụng **AWS Lambda** và **Amazon API Gateway**. Kiến trúc này cho phép bạn tạo các API có khả năng mở rộng, tiết kiệm chi phí mà không cần quản lý server.

Bạn sẽ xây dựng một **Task Management API** đơn giản cho phép người dùng:

- Tạo task mới
- Liệt kê tất cả các task
- Lấy thông tin một task cụ thể
- Cập nhật task
- Xóa task

API sẽ sử dụng:

- **AWS Lambda** cho các hàm tính toán serverless
- **Amazon API Gateway** cho các endpoint REST API
- **Amazon DynamoDB** để lưu trữ dữ liệu
- **AWS IAM** cho bảo mật và quyền truy cập

#### Mục tiêu học tập

Sau khi hoàn thành workshop này, bạn sẽ có thể:

- Tạo các hàm Lambda sử dụng Python
- Thiết lập REST API trong API Gateway
- Tích hợp Lambda với API Gateway
- Lưu trữ và truy xuất dữ liệu từ DynamoDB
- Hiểu các mẫu kiến trúc serverless
- Xử lý lỗi và phản hồi API một cách đúng đắn

#### Yêu cầu

- Tài khoản AWS với quyền phù hợp
- Kiến thức cơ bản về lập trình Python
- Hiểu biết về khái niệm REST API
- AWS CLI đã được cấu hình (tùy chọn nhưng khuyến nghị)

#### Nội dung

1. [Tổng quan Workshop](5.1-Workshop-overview/)
2. [Yêu cầu và Thiết lập](5.2-Prerequiste/)
3. [Tạo bảng DynamoDB](5.3-S3-vpc/)
4. [Tạo các hàm Lambda](5.4-S3-onprem/)
5. [Cấu hình API Gateway](5.5-Policy/)
6. [Kiểm thử và Dọn dẹp](5.6-Cleanup/)
