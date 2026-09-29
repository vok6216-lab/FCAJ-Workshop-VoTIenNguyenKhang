---
title: "Event 5"
date: 2025-11-29
weight: 5
chapter: false
pre: " <b> 4.5. </b> "
---

# Bài thu hoạch "AWS Cloud Mastery Series #3"

### Mục Đích Của Sự Kiện

Sự kiện nhằm khám phá các thực hành tốt nhất về AWS Identity and Access Management (IAM), tập trung vào các nguyên tắc bảo mật, kiểm soát truy cập dựa trên vai trò, Single Sign-On (SSO), AWS Organizations, quản lý thông tin xác thực và các tính năng IAM nâng cao cho bảo mật doanh nghiệp.

### Danh Sách Diễn Giả

1. **Huỳnh Hoàng Long**

2. **Đinh Lê Hoàng Anh**

### Nội Dung Nổi Bật

#### Hiểu về IAM (Identity and Access Management)

**Định Nghĩa:**

- IAM bao gồm các vai trò với quyền cụ thể được gán cho người dùng cụ thể

- Tăng khả năng xác thực cho hệ thống

- Cung cấp kiểm soát truy cập chi tiết đến tài nguyên AWS

**Khái Niệm Cốt Lõi:**

- Vai trò xác định các hành động có thể thực hiện

- Người dùng được gán vai trò dựa trên trách nhiệm của họ

- Tăng cường bảo mật hệ thống thông qua quản lý truy cập phù hợp

#### Thực Hành Tốt Nhất về IAM

**1. Nguyên Tắc Quyền Tối Thiểu:**

- Thực hành tốt nhất: Không cấp quá nhiều quyền cho một tài khoản

- Chỉ cấp các quyền cụ thể cần thiết cho nhiệm vụ

- Giảm rủi ro bảo mật và thiệt hại tiềm ẩn từ các tài khoản bị xâm phạm

**2. Quản Lý Root Access Key:**

- **Xóa root access keys** vì chúng có quyền cao nhất

- Nếu access keys bị mất, sẽ không gây quá nhiều tác động

- Giảm thiểu tổn thất tiềm ẩn tối đa

- Root account chỉ nên được sử dụng cho thiết lập ban đầu và các tình huống khẩn cấp

**3. Tránh Quyền Wildcard:**

- Tránh sử dụng `*` (dấu sao) có nghĩa là quyền đầy đủ cho tất cả các dịch vụ

- Sử dụng quyền dịch vụ và hành động cụ thể thay thế

- Cung cấp bảo mật và khả năng kiểm toán tốt hơn

**4. Sử dụng AWS Login (Thông Tin Xác Thực Tạm Thời):**

- Nên sử dụng AWS login vì nó reset ít nhất mỗi 15 phút và nhiều nhất mỗi 36 giờ

- Tăng cường bảo mật đáng kể

- Thông tin xác thực tạm thời giảm rủi ro phơi nhiễm lâu dài

- Tự động hết hạn, giảm bề mặt tấn công

**5. Xác Thực Đa Yếu Tố (MFA):**

- MFA là bước xác thực bổ sung giúp ngăn chặn truy cập trái phép

- Ngăn chặn đăng nhập tài khoản từ các vị trí khác

- Thêm một lớp bảo mật bổ sung ngoài mật khẩu

- Nên được bật cho tất cả các tài khoản có đặc quyền

**6. Thay Đổi Mật Khẩu Thường Xuyên:**

- Nên thường xuyên thay đổi mật khẩu tài khoản

- Tuân theo thực hành tốt nhất về bảo mật cho quản lý thông tin xác thực

- Giảm rủi ro thông tin xác thực bị xâm phạm

#### Single Sign-On (SSO)

**Định Nghĩa:**

- SSO cho phép một lần đăng nhập để truy cập nhiều hệ thống

- Người dùng xác thực một lần và có quyền truy cập vào nhiều ứng dụng

- Khi chuyển sang ứng dụng khác, không cần đăng nhập lại

**Lợi Ích Doanh Nghiệp:**

- Quản lý tốt hơn trong môi trường doanh nghiệp

- Nhiều vai trò có sẵn, mỗi vai trò có các tài khoản cụ thể

- Kiểm soát truy cập tập trung

- Trải nghiệm người dùng đơn giản hóa

**Tích Hợp AWS:**

- Khi kích hoạt SSO, đồng thời kích hoạt AWS Organizations

- Cho phép quản lý tập trung nhiều tài khoản AWS

- Cung cấp kiểm soát truy cập thống nhất trong toàn tổ chức

#### AWS Organizations và Service Control Policies (SCP)

**AWS Organizations:**

- Cho phép quản lý nhiều tài khoản AWS từ một vị trí trung tâm

- Cung cấp thanh toán hợp nhất và quản lý tài khoản

- Hoạt động cùng với SSO cho kiểm soát truy cập doanh nghiệp

**Service Control Policies (SCP):**

- Các chính sách kiểm soát dịch vụ có thể đặt giới hạn quyền tối đa trong một tài khoản

- Cung cấp quản trị bảo mật tập trung

- Có thể hạn chế các hành động có thể thực hiện trên các tài khoản

- Giúp thực thi các chính sách bảo mật tổ chức

#### Permission Boundaries

**Định Nghĩa:**

- Một dịch vụ IAM nâng cao xử lý các vấn đề bảo mật tập trung

- Đặt quyền tối đa mà một chính sách dựa trên danh tính có thể cấp

- Cung cấp một lớp kiểm soát bảo mật bổ sung

- Ngăn chặn leo thang đặc quyền ngay cả khi chính sách bị cấu hình sai

**Use Cases:**

- Ủy quyền cho các nhà phát triển hoặc nhóm

- Đảm bảo người dùng không thể vượt quá quyền dự định

- Quản lý bảo mật tập trung trong các tổ chức lớn

#### Credential Spectrum và Rotation

**Credential Spectrum:**

- Hiểu các loại thông tin xác thực khác nhau và ý nghĩa bảo mật của chúng

- Từ long-term access keys đến temporary credentials

- Cân bằng bảo mật với khả năng sử dụng

**Credential Rotation:**

- Về dịch vụ AWS Secrets Manager

- Quy trình: Tạo tài khoản giả với mật khẩu mới, kiểm tra xem chúng có thể sử dụng không, áp dụng cho tài khoản của bạn, và cuối cùng xóa các tài khoản cũ

- Tự động hóa việc xoay thông tin xác thực cơ sở dữ liệu, API keys và các secret khác

- Giảm rủi ro thông tin xác thực bị xâm phạm

- Đảm bảo thông tin xác thực được cập nhật thường xuyên mà không cần can thiệp thủ công

**Lợi Ích AWS Secrets Manager:**

- Xoay secret tự động

- Lưu trữ thông tin xác thực an toàn

- Tích hợp với các dịch vụ AWS

- Dấu vết kiểm toán truy cập secret

#### IAM Access Analyzer

**Tổng Quan:**

- Công cụ phân tích chính sách IAM và mẫu truy cập

- Xác định tài nguyên được chia sẻ với các thực thể bên ngoài

- Giúp phát hiện truy cập không mong muốn

- Cung cấp khuyến nghị để cải thiện tư thế bảo mật

**Tính Năng Chính:**

- Phân tích chính sách dựa trên tài nguyên

- Xác định tài nguyên có thể truy cập công khai

- Đề xuất cải thiện chính sách

- Giám sát liên tục mẫu truy cập

**Phân Tích Chính Sách:**

- Phát hiện chính sách chứa `Principal: *` (truy cập công khai)

- Cờ cảnh báo các vấn đề bảo mật ngay cả khi có điều kiện

- Giúp xác định và khắc phục rủi ro bảo mật

**Khắc Phục Tự Động:**

- Có thể tích hợp với EventBridge cho phản hồi tự động

- Các hàm Lambda có thể thêm câu lệnh deny vào IAM roles

- Thông báo SNS cho cảnh báo nhóm bảo mật

- Cho phép quản lý bảo mật chủ động

### Những Gì Học Được

1. **Nguyên Tắc Cơ Bản IAM:**

   - IAM roles và users cung cấp kiểm soát truy cập chi tiết

   - Cấu hình IAM phù hợp là điều cần thiết cho bảo mật AWS

   - Xác thực và ủy quyền là các khái niệm riêng biệt nhưng liên quan

2. **Thực Hành Bảo Mật Tốt Nhất:**

   - Tuân theo nguyên tắc quyền tối thiểu

   - Xóa root access keys

   - Tránh quyền wildcard

   - Sử dụng thông tin xác thực tạm thời (AWS login)

   - Bật MFA cho tất cả các tài khoản

   - Thay đổi mật khẩu thường xuyên

3. **Quản Lý Truy Cập Doanh Nghiệp:**

   - SSO đơn giản hóa truy cập trên nhiều hệ thống

   - AWS Organizations cho phép quản lý tài khoản tập trung

   - SCP cung cấp quản trị bảo mật toàn tổ chức

   - Permission boundaries ngăn chặn leo thang đặc quyền

4. **Quản Lý Thông Tin Xác Thực:**

   - Sử dụng AWS Secrets Manager cho xoay thông tin xác thực

   - Ưu tiên thông tin xác thực tạm thời hơn long-term access keys

   - Tự động hóa xoay thông tin xác thực khi có thể

   - Giám sát việc sử dụng và mẫu truy cập thông tin xác thực

5. **Bảo Mật Liên Tục:**

   - Sử dụng IAM Access Analyzer cho đánh giá bảo mật liên tục

   - Xem xét và kiểm toán chính sách IAM thường xuyên

   - Giám sát truy cập không mong muốn

   - Cập nhật với thực hành bảo mật AWS tốt nhất

### Ứng Dụng Vào Công Việc

1. **Triển Khai Thực Hành Tốt Nhất IAM:**

   - Xem xét và xóa root access keys

   - Bật MFA cho tất cả các tài khoản có đặc quyền

   - Thay thế quyền wildcard bằng quyền cụ thể

   - Sử dụng thông tin xác thực tạm thời thay vì long-term access keys

2. **Thiết Lập SSO:**

   - Đánh giá triển khai SSO cho tổ chức của bạn

   - Cấu hình AWS Organizations nếu quản lý nhiều tài khoản

   - Triển khai kiểm soát truy cập dựa trên vai trò

   - Tập trung quản lý người dùng

3. **Triển Khai Permission Boundaries:**

   - Sử dụng permission boundaries cho truy cập được ủy quyền

   - Đặt giới hạn quyền tối đa cho các nhóm

   - Ngăn chặn leo thang đặc quyền

   - Tập trung chính sách bảo mật

4. **Xoay Thông Tin Xác Thực:**

   - Sử dụng AWS Secrets Manager cho thông tin xác thực cơ sở dữ liệu

   - Tự động hóa xoay API keys và secrets

   - Thiết lập lịch xoay

   - Kiểm tra quy trình xoay trước khi production

5. **Giám Sát Bảo Mật:**

   - Bật IAM Access Analyzer

   - Xem xét mẫu truy cập thường xuyên

   - Xác định và khắc phục truy cập không mong muốn

   - Sử dụng CloudTrail cho audit logging

6. **Kiểm Toán Bảo Mật Thường Xuyên:**

   - Tiến hành xem xét chính sách IAM định kỳ

   - Xóa thông tin xác thực và vai trò không sử dụng

   - Cập nhật chính sách dựa trên yêu cầu thay đổi

   - Tài liệu hóa yêu cầu truy cập và lý do

### Trải nghiệm trong event

Sự kiện cung cấp những hiểu biết toàn diện về thực hành bảo mật AWS IAM tốt nhất, bao gồm mọi thứ từ nguyên tắc cơ bản đến các tính năng doanh nghiệp nâng cao. Các diễn giả đã chia sẻ kinh nghiệm thực tế và các tình huống thực tế nhấn mạnh tầm quan trọng của cấu hình IAM phù hợp.

#### Hiểu Nguyên Tắc Cơ Bản IAM

- Học được rằng IAM là về các vai trò với quyền cụ thể được gán cho người dùng

- Hiểu cách cấu hình IAM phù hợp tăng cường xác thực hệ thống

- Nhận ra tầm quan trọng của kiểm soát truy cập chi tiết

#### Thực Hành Bảo Mật Tốt Nhất

- **Quyền Tối Thiểu**: Nhận ra tầm quan trọng của việc chỉ cấp quyền cần thiết

- **Root Access**: Hiểu tại sao root access keys nên được xóa

- **Tránh Wildcard**: Học cách tránh quyền `*` để bảo mật tốt hơn

- **Thông Tin Xác Thực Tạm Thời**: Đánh giá cao lợi ích bảo mật của AWS login với xoay tự động

- **MFA**: Nhận ra MFA là điều cần thiết để ngăn chặn truy cập trái phép

- **Quản Lý Mật Khẩu**: Hiểu nhu cầu thay đổi mật khẩu thường xuyên

#### Tính Năng Doanh Nghiệp

- **SSO**: Học cách Single Sign-On đơn giản hóa truy cập trên nhiều hệ thống

- **AWS Organizations**: Hiểu cách nó hoạt động với SSO cho quản lý tập trung

- **SCP**: Khám phá cách Service Control Policies thực thi bảo mật toàn tổ chức

- **Permission Boundaries**: Nhận ra vai trò của chúng trong việc ngăn chặn leo thang đặc quyền

#### Quản Lý Thông Tin Xác Thực

- **Xoay Thông Tin Xác Thực**: Học về AWS Secrets Manager và xoay tự động

- **Credential Spectrum**: Hiểu các loại thông tin xác thực khác nhau và ý nghĩa bảo mật của chúng

- **Thực Hành Tốt Nhất**: Khám phá quy trình xoay thông tin xác thực và kiểm tra

#### Công Cụ Bảo Mật

- **IAM Access Analyzer**: Học cách sử dụng nó cho đánh giá bảo mật liên tục

- **Giám Sát**: Hiểu tầm quan trọng của phân tích mẫu truy cập liên tục

- **Khắc Phục**: Khám phá cách xác định và sửa các vấn đề bảo mật

#### Một số hình ảnh khi tham gia sự kiện

![IAM Access Analyzer](/images/4-EventParticipated/4.5-Event5/iam-access-analyzer.jpg)

![Credentials Spectrum](/images/4-EventParticipated/4.5-Event5/credentials-spectrum.jpg)

![Multi-Factor Authentication (MFA)](/images/4-EventParticipated/4.5-Event5/mfa-comparison.jpg)

> Tổng thể, sự kiện đã thành công trong việc chứng minh rằng IAM là nền tảng của bảo mật AWS. Sự nhấn mạnh vào thực hành tốt nhất, tính năng doanh nghiệp và giám sát bảo mật liên tục cung cấp cách tiếp cận toàn diện để quản lý truy cập và bảo vệ tài nguyên AWS hiệu quả.

