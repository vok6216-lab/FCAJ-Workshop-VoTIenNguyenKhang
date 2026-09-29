---
title : "Tạo bảng DynamoDB"
date : 2025-09-09
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

## Tạo bảng DynamoDB

DynamoDB là cơ sở dữ liệu NoSQL sẽ lưu trữ các task của chúng ta. Hãy tạo một bảng để lưu trữ dữ liệu task.

### Bước 1: Điều hướng đến DynamoDB

1. Vào AWS Console
2. Tìm kiếm "DynamoDB" trong thanh tìm kiếm dịch vụ
3. Nhấp vào **DynamoDB**

### Bước 2: Tạo bảng

1. Nhấp vào nút **Create table**
2. Cấu hình bảng:
   - **Table name**: `tasks`
   - **Partition key**: `id` (type: String)
   - **Table settings**: Sử dụng cài đặt mặc định
   - **Capacity mode**: On-demand (được khuyến nghị cho workshop này)

### Bước 3: Tạo bảng

1. Cuộn xuống và nhấp **Create table**
2. Chờ bảng được tạo (thường mất vài giây)

### Cấu trúc bảng

Bảng DynamoDB của chúng ta sẽ có cấu trúc sau:

- **id** (String) - Khóa chính - Định danh duy nhất cho mỗi task
- **title** (String) - Tiêu đề task
- **description** (String) - Mô tả task  
- **status** (String) - Trạng thái task (ví dụ: "pending", "completed")
- **createdAt** (String) - Timestamp khi task được tạo
- **updatedAt** (String) - Timestamp khi task được cập nhật lần cuối

### Các bước tiếp theo

Sau khi bảng được tạo, chúng ta sẽ tiếp tục tạo các hàm Lambda sẽ tương tác với bảng này.
