---
title : "Yêu cầu và Thiết lập"
date :  2025-09-09
weight : 2 
chapter : false
pre : " <b> 5.2. </b> "
---

## Yêu cầu

### Quyền truy cập các dịch vụ AWS cần thiết

Để hoàn thành workshop này, bạn cần quyền truy cập vào các dịch vụ AWS sau:

- AWS Lambda
- Amazon API Gateway
- Amazon DynamoDB
- AWS IAM
- Amazon CloudWatch Logs

### Quyền IAM

Tài khoản AWS của bạn cần có các quyền IAM sau:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "lambda:*",
                "apigateway:*",
                "dynamodb:*",
                "iam:CreateRole",
                "iam:AttachRolePolicy",
                "iam:PutRolePolicy",
                "iam:GetRole",
                "iam:DeleteRole",
                "iam:DetachRolePolicy",
                "iam:DeleteRolePolicy",
                "logs:CreateLogGroup",
                "logs:DeleteLogGroup",
                "logs:DescribeLogGroups"
            ],
            "Resource": "*"
        }
    ]
}
```

### Yêu cầu phần mềm

- **Tài khoản AWS** với quyền phù hợp
- **Quyền truy cập AWS Console** hoặc **AWS CLI** đã được cấu hình
- Kiến thức cơ bản về **Python 3.x**
- Trình soạn thảo văn bản hoặc IDE (VS Code, PyCharm, v.v.)

### AWS Region

Chúng ta sẽ sử dụng **us-east-1 (N. Virginia)** cho workshop này. Bạn có thể chọn bất kỳ region nào, nhưng hãy đảm bảo tất cả tài nguyên được tạo trong cùng một region.

## Các bước thiết lập

### Bước 1: Xác minh quyền truy cập AWS

1. Đăng nhập vào AWS Management Console
2. Điều hướng đến dịch vụ AWS Lambda
3. Đảm bảo bạn có thể thấy bảng điều khiển Lambda

### Bước 2: Chọn Region của bạn

1. Chọn AWS region ưa thích của bạn từ góc trên bên phải
2. Ghi nhớ region này - tất cả tài nguyên sẽ được tạo ở đây

### Bước 3: Chuẩn bị môi trường của bạn

- Chuẩn bị trình soạn thảo văn bản để viết code cho hàm Lambda
- Giữ AWS Console mở trong trình duyệt
- Tùy chọn, cấu hình AWS CLI nếu bạn thích sử dụng công cụ dòng lệnh

## Chi phí ước tính

Workshop này sử dụng các dịch vụ đủ điều kiện AWS Free Tier:

- **Lambda**: 1M yêu cầu miễn phí mỗi tháng
- **API Gateway**: 1M lời gọi API mỗi tháng cho REST APIs
- **DynamoDB**: 25GB lưu trữ, 25 đơn vị dung lượng đọc/ghi

**Lưu ý**: Nếu bạn vượt quá giới hạn free tier, bạn có thể phải trả phí tối thiểu. Luôn dọn dẹp tài nguyên sau khi hoàn thành workshop.
