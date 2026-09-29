---
title: "Blog 3"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# Cấu hình quyền truy cập chi tiết vào các mô hình Amazon Bedrock bằng Amazon SageMaker Unified Studio

By Varun Jasti, Lijan Kuniyil, Jon Turdiev và Saptarshi Banerjee vào ngày 09 tháng 7 năm 2025 tại Advanced (300), Amazon Bedrock, Amazon Machine Learning, Amazon SageMaker Unified Studio, Artificial Intelligence, AWS Identity and Access Management (IAM), Security, Identity, & Compliance, Technical How-to Permalink  Comments  Share

Các doanh nghiệp áp dụng giải pháp AI tiên tiến nhận thức được rằng bảo mật mạnh mẽ và kiểm soát truy cập chính xác là điều cần thiết để bảo vệ dữ liệu quý giá, duy trì sự tuân thủ và giữ vững niềm tin của người dùng. Khi các tổ chức mở rộng việc sử dụng AI trên khắp các nhóm và ứng dụng, họ cần các quyền chi tiết để bảo vệ thông tin nhạy cảm và quản lý những người có thể truy cập các mô hình mạnh mẽ. Amazon SageMaker Unified Studio đáp ứng những nhu cầu này để các tổ chức có thể cấu hình các chính sách truy cập chi tiết, đảm bảo rằng chỉ những người dùng được ủy quyền mới có thể tương tác với các mô hình nền tảng (FM) đồng thời hỗ trợ đổi mới an toàn và cộng tác ở quy mô lớn.

Ra mắt năm 2025, SageMaker Unified Studio là một môi trường phát triển dữ liệu và AI duy nhất, nơi bạn có thể tìm kiếm và truy cập dữ liệu trong tổ chức của mình, đồng thời xử lý dữ liệu bằng các công cụ tốt nhất cho mọi trường hợp sử dụng. SageMaker Unified Studio kết hợp chức năng và công cụ từ các dịch vụ phân tích AWS và AI/ML hiện có, bao gồm: Amazon EMR, AWS Glue, Amazon Athena, Amazon Redshift, Amazon Bedrock, và Amazon SageMaker AI.

Amazon Bedrock trong SageMaker Unified Studio cung cấp nhiều tùy chọn để khám phá và thử nghiệm các mô hình và ứng dụng Amazon Bedrock. Ví dụ: bạn có thể sử dụng sân chơi trò chuyện để thử nghiệm với Claude của Anthropic mà không cần phải viết mã. Bạn cũng có thể tạo một ứng dụng AI tạo sinh sử dụng mô hình Amazon Bedrock và các tính năng, chẳng hạn như cơ sở kiến ​​thức hoặc lan can. Để tìm hiểu thêm, hãy tham khảo Amazon Bedrock in SageMaker Unified Studio.

Trong bài viết này, chúng tôi sẽ trình bày cách sử dụng SageMaker Unified Studio và AWS Identity and Access Management (IAM) để thiết lập một khuôn khổ phân quyền mạnh mẽ cho các mô hình Amazon Bedrock. Chúng tôi sẽ hướng dẫn quản trị viên cách quản lý chính xác người dùng và nhóm nào có quyền truy cập vào các mô hình cụ thể trong một môi trường cộng tác an toàn. Chúng tôi sẽ hướng dẫn bạn cách tạo các quyền chi tiết để kiểm soát quyền truy cập mô hình, với các ví dụ mã cho các tình huống quản trị doanh nghiệp phổ biến. Cuối cùng, bạn sẽ hiểu cách tùy chỉnh quyền truy cập vào các chức năng AI tạo sinh để đáp ứng các yêu cầu của tổ chức - giải quyết một thách thức cốt lõi trong việc áp dụng AI doanh nghiệp bằng cách cho phép nhà phát triển linh hoạt trong khi vẫn duy trì các tiêu chuẩn bảo mật mạnh mẽ.

## Tổng quan về giải pháp

Trong SageMaker Unified Studio, một miền đóng vai trò là cấu trúc tổ chức chính, cho phép bạn giám sát nhiều Vùng AWS, tài khoản và khối lượng công việc từ một giao diện duy nhất. Mỗi miền được gán một URL duy nhất và cung cấp khả năng kiểm soát tập trung đối với cấu hình studio, tài khoản người dùng và cài đặt mạng.

Bên trong mỗi miền, các dự án tạo điều kiện cho việc cộng tác được hợp lý hóa. Các dự án có thể trải rộng trên nhiều Vùng hoặc tài khoản khác nhau trong một Vùng, và siêu dữ liệu của chúng bao gồm các chi tiết như kho lưu trữ Git liên quan, thành viên nhóm và quyền của họ. Mỗi tài khoản mà dự án có tài nguyên được chỉ định ít nhất một vai trò dự án, vai trò này xác định các công cụ, tài nguyên tính toán, bộ dữ liệu và tài sản trí tuệ nhân tạo và học máy (AI/ML) mà các thành viên dự án có thể truy cập. Để quản lý quyền truy cập dữ liệu, bạn có thể điều chỉnh các quyền IAM được liên kết với vai trò của dự án. SageMaker Unified Studio sử dụng một số vai trò IAM. Để biết danh sách đầy đủ, hãy tham khảo Quản lý  Identity and access management for Amazon SageMaker Unified Studio.

Có hai phương pháp chính để người dùng tương tác với các mô hình Amazon Bedrock trong SageMaker Unified Studio: SageMaker Unified Studio playground và SageMaker Unified Studio projects.

Trong kịch bản sân chơi SageMaker Unified Studio, các vai trò sử dụng mô hình cung cấp quyền truy cập an toàn vào Amazon Bedrock FM. Bạn có thể chọn giữa việc tạo vai trò tự động cho từng mô hình hoặc cấu hình một vai trò duy nhất cho tất cả các mô hình. Mặc định AmazonSageMakerBedrockModelConsumptionRole đi kèm với các quyền được cấu hình sẵn để sử dụng các mô hình Amazon Bedrock, bao gồm việc gọi cấu hình suy luận ứng dụng Amazon Bedrock được tạo cho một miền SageMaker Unified Studio cụ thể. Để tinh chỉnh quyền kiểm soát truy cập, bạn có thể thêm các chính sách nội tuyến vào các vai trò này để cho phép hoặc từ chối rõ ràng quyền truy cập vào các mô hình Amazon Bedrock cụ thể.

Trong kịch bản dự án SageMaker Unified Studio, SageMaker Unified Studio sử dụng vai trò cung cấp mô hình để tạo hồ sơ suy luận cho mô hình Amazon Bedrock trong dự án. Hồ sơ suy luận là bắt buộc để dự án tương tác với mô hình. Bạn có thể cho phépSageMaker Unified Studio Tự động tạo một mô hình duy nhất vai trò cung cấp hoặc bạn có thể cung cấp vai trò cung cấp mô hình tùy chỉnh. Mặc địnhAmazonSageMakerBedrockModelManagementRole has the AWS policy AmazonDataZoneBedrockModelManagementPolicy đính kèm. Bạn có thể hạn chế quyền truy cập vào ID tài khoản cụ thể thông qua các chính sách tin cậy tùy chỉnh. Bạn cũng có thể đính kèm các chính sách nội tuyến và sử dụng câu lệnh CreateApplicationInferenceProfileUsingFoundationModels để cho phép hoặc từ chối quyền truy cập vào các mô hình Amazon Bedrock cụ thể trong dự án của bạn.

Bằng cách tùy chỉnh các chính sách được gắn với các vai trò này, bạn có thể kiểm soát hành động nào được phép hoặc bị từ chối, từ đó quản lý quyền truy cập vào các chức năng AI tạo sinh.

Để sử dụng một mô hình cụ thể từ Amazon Bedrock, SageMaker Unified Studio sử dụng ID mô hình của mô hình đã chọn làm một phần của lệnh gọi API. Tại thời điểm viết bài, SageMaker Unified Studio hỗ trợ các mô hình Amazon Bedrock sau (danh sách đầy đủ các mô hình hiện tại có thể được tìm thấy tại đây), được nhóm theo nhà cung cấp mô hình:

**Amazon:**
- Amazon Titan Text G1 – Premier: amazon.titan-text-premier-v1:0
- Amazon Nova Pro: amazon.nova-pro-v1:0
- Amazon Nova Lite: amazon.nova-lite-v1:0
- Amazon Nova Canvas: amazon.nova-canvas-v1:0

**Stability AI:**
- SDXL 1.0: stability.stable-diffusion-xl-v1

**AI21 Labs:**
- Jamba-Instruct: ai21.jamba-instruct-v1:0
- Jamba 1.5 Large: ai21.jamba-1-5-large-v1:0
- Jamba 1.5 Mini: ai21.jamba-1-5-mini-v1:0

**Anthropic:**
- Claude 3.7 Sonnet: anthropic.claude-3-7-sonnet-20250219-v1:0

**Cohere:**
- Command R+: cohere.command-r-plus-v1:0
- Command Light: cohere.command-light-text-v14
- Embed Multilingual: cohere.embed-multilingual-v3

**DeepSeek:**
- DeepSeek-R1: deepseek.r1-v1:0

**Meta:**
- Llama 3.3 70B Instruct: meta.llama3-3-70b-instruct-v1:0
- Llama 4 Scout 17B Instruct: meta.llama4-scout-17b-instruct-v1:0
- Llama 4 Maverick 17B Instruct: meta.llama4-maverick-17b-instruct-v1:0

**Mistral AI:**
- Mistral 7B Instruct: mistral.mistral-7b-instruct-v0:2
- Pixtral Large (25.02): mistral.pixtral-large-2502-v1:0

## Tạo vai trò tiêu thụ mô hình cho kịch bản sân chơi

Trong các bước sau, bạn sẽ tạo vai trò IAM với chính sách tin cậy, thêm hai chính sách nội tuyến và đính kèm chúng vào vai trò.

### Tạo vai trò IAM với chính sách tin cậy

Hoàn thành các bước sau để tạo vai trò IAM với chính sách tin cậy:

1. Trên bảng điều khiển IAM, trong ngăn điều hướng, chọn Vai trò, sau đó chọn Tạo vai trò.
2. Đối với Loại thực thể đáng tin cậy, chọn Chính sách tin cậy tùy chỉnh.
3. Xóa chính sách mặc định trong trình soạn thảo và nhập chính sách tin cậy sau (replace account-id for the aws:SourceAccount field with your AWS account ID):

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Service": "datazone.amazonaws.com"
            },
            "Action": [
                "sts:AssumeRole",
                "sts:SetContext"
            ],
            "Condition": {
                "StringEquals": {
                    "aws:SourceAccount": "[account-id]"
                }
            }
        }
    ]
}
```

4. Chọn Tiếp theo.
5. Bỏ qua trang Thêm quyền bằng cách chọn Tiếp theo.
6. Nhập tên cho vai trò (for example, DataZoneBedrock-Role) và một mô tả tùy chọn.
7. Chọn Tạo vai trò.

### Thêm chính sách nội tuyến đầu tiên

Thực hiện các bước sau để thêm chính sách nội tuyến:

1. Trên bảng điều khiển IAM, hãy mở trang chi tiết vai trò mới tạo.
2. Trên tab Quyền, chọn Thêm quyền rồi chọn Tạo chính sách nội tuyến.
3. Trên tab JSON, xóa chính sách mặc định và nhập chính sách nội tuyến đầu tiên:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "InvokeDomainInferenceProfiles",
            "Effect": "Allow",
            "Action": [
                "bedrock:InvokeModel",
                "bedrock:InvokeModelWithResponseStream"
            ],
            "Resource": "arn:aws:bedrock:*:*:application-inference-profile/*",
            "Condition": {
                "StringEquals": {
                    "aws:ResourceTag/AmazonDataZoneDomain": "${datazone:domainId}",
                    "aws:ResourceAccount": "${aws:PrincipalAccount}"
                },
                "Null": {
                    "aws:ResourceTag/AmazonDataZoneProject": "true"
                }
            }
        }
    ]
}
```

4. Chọn Chính sách đánh giá.
5. Đặt tên cho chính sách (for example, DataZoneDomainInferencePolicy) và chọn Create policy.

### Thêm chính sách nội tuyến thứ hai

Hoàn thành các bước sau để thêm chính sách nội tuyến khác:

1. Trên tab Quyền của vai trò, chọn Thêm quyền rồi chọn Tạo chính sách nội tuyến.
2. On the JSON tab, delete the default policy and enter the second inline policy (replace account-id in the bedrock:InferenceProfileArn field with your account ID):

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowInferenceProfileToInvokeFoundationModels",
            "Effect": "Allow",
            "Action": [
                "bedrock:InvokeModel",
                "bedrock:InvokeModelWithResponseStream"
            ],
            "Resource": [
                "arn:aws:bedrock:us-east-1::foundation-model/anthropic.claude-3-5-haiku-20241022-v1:0",
                "arn:aws:bedrock:us-east-2::foundation-model/anthropic.claude-3-5-haiku-20241022-v1:0",
                "arn:aws:bedrock:us-west-2::foundation-model/anthropic.claude-3-5-haiku-20241022-v1:0"
            ],
            "Condition": {
                "ArnLike": {
                    "bedrock:InferenceProfileArn": "arn:aws:bedrock:*:[account-id]:application-inference-profile/*"
                }
            }
        }
    ]
}
```

3. Chọn Chính sách đánh giá.
4. Đặt tên cho chính sách (for example, BedrockFoundationModelAccessPolicy) và chọn Tạo chính sách.

### Giải thích về các chính sách

Trong phần này, chúng tôi thảo luận chi tiết về các chính sách.

#### Giải thích chính sách tin cậy

Chính sách tin cậy này xác định ai có thể đảm nhận vai trò IAM:

- It allows the Amazon DataZone service (datazone.amazonaws.com) to assume this role
- The service can perform sts:AssumeRole and sts:SetContext actions
- Một điều kiện hạn chế điều này chỉ khi tài khoản AWS bạn chỉ định là tài khoản AWS của bạn

Điều này đảm bảo rằng chỉ Amazon DataZone từ tài khoản bạn chỉ định mới có thể đảm nhận vai trò này.

#### Giải thích chính sách nội tuyến đầu tiên

Chính sách này kiểm soát quyền truy cập vào hồ sơ suy luận Amazon Bedrock:

- It allows invoking Amazon Bedrock models (bedrock:InvokeModel and bedrock:InvokeModelWithResponseStream), but only for resources that are application inference profiles (arn:aws:bedrock:::application-inference-profile/*)
- It has three important conditions:
  - The profile must be tagged with AmazonDataZoneDomain matching the domain ID of the caller
  - The resource must be in the same AWS account as the principal making the request
  - The resource must not have an AmazonDataZoneProject tag set to "true"

Điều này thực sự hạn chế quyền truy cập vào những hồ sơ suy luận chỉ thuộc về cùng miền Amazon DataZone với người gọi và không liên kết với một dự án cụ thể.

#### Giải thích chính sách nội tuyến thứ hai

Chính sách này kiểm soát các FM cụ thể nào có thể được truy cập:

- Nó cho phép các hành động gọi mô hình Amazon Bedrock giống nhau, nhưng chỉ dành cho các mô hình Anthropic Claude 3.5 Haiku cụ thể trong ba Vùng:
  - us-east-1
  - us-east-2
  - us-west-2
- Nó có một điều kiện bổ sung: bedrock:InferenceProfileArn phải khớp với ARN của hồ sơ suy luận ứng dụng trong tài khoản của bạn

### Hiệu ứng kết hợp trên sân chơi AI tạo sinh miền SageMaker Unified Studio

Cùng nhau, các chính sách này tạo ra một môi trường an toàn và được kiểm soát để sử dụng các mô hình Amazon Bedrock trong miền SageMaker Unified Studio thông qua các phương pháp sau:

- **Giới hạn quyền truy cập mô hình** – Chỉ có thể sử dụng mô hình Anthropic Claude 3.5 Haiku được chỉ định, không sử dụng các mô hình Amazon Bedrock khác
- **Thực thi quyền truy cập thông qua hồ sơ suy luận** – Chỉ có thể truy cập mô hình thông qua hồ sơ suy luận ứng dụng được cấu hình đúng cách
- **Duy trì tính cô lập miền** – Quyền truy cập bị hạn chế đối với các hồ sơ suy luận được gắn thẻ với miền Amazon DataZone của người dùng
- **Giúp ngăn chặn truy cập chéo tài khoản** – Tài nguyên phải nằm trong cùng một tài khoản với tài khoản chính
- **Hạn chế khu vực** – Chỉ được phép truy cập mô hình trong ba Khu vực AWS cụ thể

Việc triển khai này tuân theo nguyên tắc đặc quyền tối thiểu bằng cách chỉ cung cấp các quyền tối thiểu cần thiết cho trường hợp sử dụng dự định, đồng thời duy trì ranh giới bảo mật phù hợp giữa các miền và dự án khác nhau.

## Tạo vai trò cung cấp mô hình cho kịch bản dự án

Trong phần này, chúng tôi sẽ hướng dẫn các bước để tạo vai trò IAM với chính sách tin cậy và thêm chính sách nội tuyến cần thiết để đảm bảo rằng các mô hình chỉ giới hạn ở những mô hình đã được chấp thuận.

### Tạo vai trò IAM với chính sách tin cậy

Hoàn thành các bước sau để tạo vai trò IAM với chính sách tin cậy:

1. Trên bảng điều khiển IAM, trong ngăn điều hướng, chọn Vai trò, sau đó chọn Tạo vai trò.
2. Đối với Loại thực thể đáng tin cậy, chọn Chính sách tin cậy tùy chỉnh.
3. Xóa chính sách mặc định trong trình soạn thảo và nhập chính sách tin cậy sau (replace account-id for the aws:SourceAccount field with your account ID):

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Service": "datazone.amazonaws.com"
            },
            "Action": [
                "sts:AssumeRole",
                "sts:SetContext"
            ],
            "Condition": {
                "StringEquals": {
                    "aws:SourceAccount": "[account-id]"
                }
            }
        }
    ]
}
```

4. Choose Next.
5. Skip the Add permissions page by choosing Next.
6. Enter a name for the role (for example, SageMakerModelManagementRole) and an optional description, such as Role for managing Bedrock model access in SageMaker Unified Studio.
7. Choose Create role.

### Thêm chính sách nội tuyến

Complete the following steps to add an inline policy:

1. On the IAM console, open the details page of the newly created role.
2. On the Permissions tab, choose Add permissions and then Create inline policy.
3. On the JSON tab, delete the default policy and enter the following inline policy:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ManageApplicationInferenceProfile",
            "Effect": "Allow",
            "Action": [
                "bedrock:CreateInferenceProfile",
                "bedrock:TagResource"
            ],
            "Resource": [
                "arn:aws:bedrock:*:*:application-inference-profile/*"
            ],
            "Condition": {
                "StringEquals": {
                    "aws:ResourceAccount": "${aws:PrincipalAccount}"
                },
                "ForAnyValue:StringEquals": {
                    "aws:TagKeys": [
                        "AmazonDataZoneProject"
                    ]
                },
                "Null": {
                    "aws:ResourceTag/AmazonDataZoneProject": "false",
                    "aws:RequestTag/AmazonDataZoneProject": "false"
                }
            }
        },
        {
            "Sid": "DeleteApplicationInferenceProfile",
            "Effect": "Allow",
            "Action": [
                "bedrock:DeleteInferenceProfile"
            ],
            "Resource": [
                "arn:aws:bedrock:*:*:application-inference-profile/*"
            ],
            "Condition": {
                "StringEquals": {
                    "aws:ResourceAccount": "${aws:PrincipalAccount}"
                },
                "Null": {
                    "aws:ResourceTag/AmazonDataZoneProject": "false"
                }
            }
        },
        {
            "Sid": "CreateApplicationInferenceProfileUsingFoundationModels",
            "Effect": "Allow",
            "Action": [
                "bedrock:CreateInferenceProfile"
            ],
            "Resource": [
                "arn:aws:bedrock:*::foundation-model/anthropic.claude-3-5-haiku-20241022-v1:0"
            ]
        },
        {
            "Sid": "CreateApplicationInferenceProfileUsingBedrockModels",
            "Effect": "Allow",
            "Action": [
                "bedrock:CreateInferenceProfile"
            ],
            "Resource": [
                "arn:aws:bedrock:*:*:inference-profile/*"
            ],
            "Condition": {
                "StringEquals": {
                    "aws:ResourceAccount": "${aws:PrincipalAccount}"
                }
            }
        }
    ]
}
```

4. Choose Review policy.
5. Name the policy (for example, BedrockModelManagementPolicy) and choose Create policy.

### Giải thích về các chính sách

Trong phần này, chúng tôi thảo luận chi tiết về các chính sách.

#### Giải thích chính sách tin cậy

Chính sách tin cậy này xác định ai có thể đảm nhận vai trò IAM:

- It allows the Amazon DataZone service to assume this role
- The service can perform sts:AssumeRole and sts:SetContext actions
- A condition restricts this to only when the source AWS account is your AWS account

Điều này đảm bảo rằng chỉ Amazon DataZone từ tài khoản cụ thể của bạn mới có thể đảm nhận vai trò này.

#### Giải thích chính sách nội tuyến

Chính sách này kiểm soát quyền truy cập vào các mô hình và hồ sơ suy luận của Amazon Bedrock:

- Nó cho phép tạo và quản lý các hồ sơ suy luận ứng dụng (bedrock:CreateInferenceProfile, bedrock:TagResource, bedrock:DeleteInferenceProfile)
- Nó đặc biệt cho phép tạo hồ sơ suy luận chỉ dành cho anthropic.claude-3-5-haiku-20241022-v1:0 model
- Access is controlled through several conditions:
  - Resources must be in the same AWS account as the principal making the request
  - Operations are restricted based on the AmazonDataZoneProject tag
  - Creating profiles requires proper tagging with AmazonDataZoneProject
  - Deleting profiles is only allowed for resources with the appropriate AmazonDataZoneProject tag

### Hiệu ứng kết hợp trên dự án miền SageMaker Unified Studio

Cùng nhau, các chính sách này tạo ra một môi trường an toàn và được kiểm soát để sử dụng các mô hình Amazon Bedrock trong các dự án miền SageMaker Unified Studio thông qua các phương pháp sau:

- **Giới hạn quyền truy cập mô hình** – Chỉ có thể sử dụng mô hình Anthropic Claude 3.5 Haiku được chỉ định
- **Thực thi gắn thẻ đúng cách** – Tài nguyên phải được gắn thẻ đúng cách AmazonDataZoneProject các định danh
- **Duy trì tính cô lập tài khoản** – Tài nguyên phải nằm trong cùng một tài khoản với tài khoản chính
- **Triển khai đặc quyền tối thiểu** – Chỉ các hành động cụ thể (tạo, gắn thẻ, xóa) mới được phép trên hồ sơ suy luận
- **Cung cấp tính cô lập ở cấp độ dự án** – Quyền truy cập bị hạn chế đối với các hồ sơ suy luận được gắn thẻ với mã định danh dự án phù hợp

This implementation follows the principle of least privilege by providing only the minimum permissions needed for project-specific use cases, while maintaining proper security boundaries between different projects and making sure that only approved FMs can be accessed.

## Cấu hình miền SageMaker Unified Studio để sử dụng các vai trò

Hoàn thành các bước sau để tạo miền SageMaker Unified Studio và cấu hình miền đó để sử dụng các vai trò bạn đã tạo:

1. Trên bảng điều khiển SageMaker, chọn Vùng phù hợp.
2. Chọn Tạo miền Unified Studio rồi chọn Thiết lập nhanh.
3. Đối với Tên, hãy nhập tên miền có ý nghĩa.
4. Cuộn xuống Tài nguyên AI Tạo sinh.
5. Trong Vai trò cung cấp mô hình, hãy chọn vai trò quản lý mô hình đã tạo ở phần trước.
6. Trong Vai trò tiêu thụ mô hình, hãy chọn Sử dụng một vai trò hiện có duy nhất cho tất cả các mô hình và chọn vai trò tiêu thụ mô hình đã tạo ở phần trước.
7. Hoàn tất các bước còn lại theo cấu hình AWS IAM Identity Center của bạn và tạo tên miền của bạn.

## Dọn dẹp

Để tránh phát sinh các khoản phí trong tương lai liên quan đến nhiều dịch vụ khác nhau được sử dụng trong SageMaker Unified Studio, hãy đăng xuất khỏi miền SageMaker Unified Studio và delete the domain trong SageMaker Unified Studio.

## Phần kết luận

Trong bài viết này, chúng tôi đã trình bày cách sân chơi SageMaker Unified Studio và các dự án SageMaker Unified Studio gọi các mô hình ngôn ngữ lớn được hỗ trợ bởi Amazon Bedrock, và cách doanh nghiệp có thể quản lý quyền truy cập vào các mô hình này, cho dù bạn muốn giới hạn quyền truy cập vào các mô hình cụ thể hay vào mọi mô hình từ dịch vụ. Bạn có thể kết hợp các chính sách IAM được trình bày trong bài viết này trong cùng một vai trò IAM để cung cấp khả năng kiểm soát hoàn toàn. Bằng cách tuân thủ các hướng dẫn này, doanh nghiệp có thể đảm bảo việc sử dụng các mô hình AI tạo sinh của họ vừa an toàn vừa phù hợp với chính sách của tổ chức. Cách tiếp cận này không chỉ bảo vệ dữ liệu nhạy cảm mà còn trao quyền cho các nhà phân tích kinh doanh và nhà khoa học dữ liệu khai thác toàn bộ tiềm năng của AI trong một môi trường được kiểm soát.

Bây giờ môi trường của bạn đã được cấu hình với các chính sách dựa trên danh tính mạnh mẽ, chúng tôi khuyên bạn nên đọc các bài đăng sau để tìm hiểu cách Amazon SageMaker Unified Studio cho phép bạn đổi mới nhanh chóng và an toàn trên quy mô lớn với AI tạo sinh:

- An integrated experience for all your data and AI with Amazon SageMaker Unified Studio
- Unified scheduling for visual ETL flows and query books in Amazon SageMaker Unified Studio
- Foundational blocks of Amazon SageMaker Unified Studio: An admin's guide to implement unified access to all your data, analytics, and AI

## Về các tác giả

**Varun Jasti** là Kiến trúc sư Giải pháp tại Amazon Web Services, làm việc với các Đối tác AWS để thiết kế và mở rộng các giải pháp trí tuệ nhân tạo cho các trường hợp sử dụng trong khu vực công nhằm đáp ứng các tiêu chuẩn tuân thủ. Với nền tảng về Khoa học Máy tính, công việc của anh bao gồm nhiều trường hợp sử dụng ML, chủ yếu tập trung vào đào tạo/suy luận LLM và thị giác máy tính. Trong thời gian rảnh rỗi, anh thích chơi tennis và bơi lội.

**Saptarshi Banarjee** là Kiến trúc sư Giải pháp Cấp cao tại AWS, hợp tác chặt chẽ với các Đối tác AWS để thiết kế và kiến ​​trúc các giải pháp quan trọng. Với chuyên môn về AI tạo sinh, AI/ML, kiến ​​trúc không máy chủ, các công cụ Trải nghiệm Nhà phát triển Thế hệ Tiếp theo và các giải pháp dựa trên đám mây, Saptarshi tận tâm nâng cao hiệu suất, đổi mới, khả năng mở rộng và hiệu quả chi phí cho các Đối tác AWS trong hệ sinh thái đám mây.

**Jon Turdiev** là Kiến trúc sư Giải pháp Cấp cao tại Amazon Web Services, nơi anh hỗ trợ các khách hàng khởi nghiệp xây dựng các sản phẩm được thiết kế tốt trên nền tảng đám mây. Với hơn 20 năm kinh nghiệm tạo ra các giải pháp tiên tiến trong lĩnh vực an ninh mạng, AI/ML, chăm sóc sức khỏe và Internet vạn vật (IoT), Jon mang đến chuyên môn kỹ thuật sâu rộng cho vai trò của mình. Trước đây, Jon đã thành lập Zehntec, một công ty tư vấn công nghệ và phát triển các thiết bị đầu cuối y tế từng đoạt giải thưởng, được triển khai tại các bệnh viện trên toàn thế giới. Jon có bằng Thạc sĩ Khoa học Máy tính và chia sẻ kiến ​​thức của mình thông qua các hội thảo trực tuyến, hội thảo chuyên đề và với tư cách là giám khảo tại các cuộc thi hackathon.

**Lijan Kuniyil** là Quản lý Khách hàng Kỹ thuật Cấp cao tại AWS. Lijan rất tâm huyết với việc giúp các khách hàng doanh nghiệp của AWS xây dựng các hệ thống có độ tin cậy cao, hiệu quả về chi phí và vận hành xuất sắc. Lijan có hơn 25 năm kinh nghiệm phát triển giải pháp cho các công ty tài chính, chăm sóc sức khỏe và tư vấn.
