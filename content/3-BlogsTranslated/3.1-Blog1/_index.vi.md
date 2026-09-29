---
title: "Blog 1"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Điều phối xử lý tài liệu với AWS AppSync Events và Amazon Bedrock

bởi Mehdi Amrane vào ngày 09 tháng 7 năm 2025 trong Advanced (300), Amazon Bedrock, Amazon Cognito, AWS Amplify, AWS AppSync, AWS Lambda, AWS Step Functions, Serverless, Technical How-to Permalink Share

Nhiều tổ chức triển khai các quy trình xử lý tài liệu thông minh để trích xuất thông tin chi tiết có ý nghĩa từ khối lượng nội dung phi cấu trúc ngày càng tăng (chẳng hạn như yêu cầu bảo hiểm, đơn xin vay vốn, v.v.). Theo truyền thống, các quy trình này đòi hỏi nhiều nỗ lực kỹ thuật, vì việc triển khai thường liên quan đến việc sử dụng một số mô hình học máy (ML) và điều phối các quy trình làm việc phức tạp.

Khi các tổ chức tích hợp các kênh này vào các ứng dụng hướng đến khách hàng (chẳng hạn như ứng dụng web để khách hàng tải lên các tài liệu như yêu cầu bảo hiểm, tài liệu phê duyệt khoản vay, v.v.), họ đặt mục tiêu cung cấp thông tin chi tiết theo thời gian thực để nâng cao trải nghiệm của khách hàng cuối. Các tổ chức này cũng đặt mục tiêu vận hành và mở rộng quy mô khối lượng công việc này với chi phí vận hành tối thiểu và tối ưu hóa chi phí. Ngoài ra, các tổ chức này cần triển khai các biện pháp bảo mật phổ biến như quản lý danh tính và truy cập, để đảm bảo rằng chỉ những người dùng được ủy quyền và xác thực mới được phép thực hiện các hành động cụ thể hoặc truy cập các tài nguyên cụ thể.

Trong bài viết này, chúng tôi sẽ giới thiệu một giải pháp giúp đơn giản hóa việc tạo quy trình xử lý tài liệu thông minh, với một ứng dụng web cho phép khách hàng tải lên các tệp (tài liệu và hình ảnh) và thu thập thông tin chi tiết từ đó (tóm tắt, trích xuất trường và phân loại). Giải pháp này chủ yếu sử dụng công nghệ serverless, bao gồm một websocket để nhận thông tin chi tiết theo thời gian thực và mang lại nhiều lợi ích, chẳng hạn như tự động mở rộng quy mô, tính khả dụng cao tích hợp sẵn và mô hình thanh toán theo mức sử dụng để tối ưu hóa chi phí. Giải pháp cũng bao gồm một lớp xác thực và một lớp ủy quyền để quản lý danh tính và quyền.

## Tổng quan giải pháp

Trong bài đăng này, chúng tôi cung cấp tổng quan về hoạt động của giải pháp và sau đó mô tả cách thiết lập giải pháp với các dịch vụ sau:

- Amazon Bedrock and Amazon Bedrock Data Automation để tóm tắt nội dung của các tệp đã tải lên (tài liệu hoặc hình ảnh) và tạo ra thông tin chi tiết từ đó.
- AWS Step Functions and AWS Lambda để điều phối các hoạt động tóm tắt và trích xuất, sử dụng Amazon Bedrock và Amazon Bedrock Data Automation.
- AWS AppSync Events để tạo một websocket không có máy chủ để ứng dụng web nhận được thông tin tóm tắt và trích xuất theo thời gian thực.
- AWS Amplify để tạo và triển khai ứng dụng web
- Amazon Event Bridge để kích hoạt quy trình phối hợp (sử dụng AWS Step Functions và AWS Lambda) khi tải lên một tập tin mới
- Amazon Cognito để triển khai một nền tảng nhận dạng (quản lý thư mục người dùng và ủy quyền) cho ứng dụng web.
- Amazon Simple Storage Service (Amazon S3) để lưu trữ các tệp đã tải lên (để xử lý bởi đường ống xử lý) và các tài sản liên quan đến ứng dụng web.

Kiến trúc giải pháp được minh họa trong sơ đồ sau:

**Bước 1:** Người dùng xác thực với ứng dụng web (được lưu trữ trên AWS Amplify).

**Bước 2:** Amazon Cognito xác thực thông tin xác thực. Sau đó, người dùng đã đăng nhập vào ứng dụng web.

**Bước 3a và 3b:**
- **Bước 3a:** Ứng dụng web (AWS Amplify) đăng ký vào websocket AWS AppSync Events.
- **Bước 3b:** Websocket AWS AppSync Events gọi trình xác thực AWS Lambda để xác nhận rằng người dùng được phép đăng ký vào web socket.

**Bước 4:** Người dùng tải tệp (tài liệu hoặc hình ảnh) lên bằng ứng dụng web.

**Bước 5:** Ứng dụng web (được lưu trữ trên AWS Amplify) sẽ gọi Amazon Cognito (nhóm danh tính) để xác nhận rằng người dùng được phép tải tệp lên.

**Bước 6:** Tệp được tải lên thùng Amazon S3.

**Bước 7a và 7b:** Khi nhận được sự kiện tải lên Amazon S3 (thông báo rằng tệp đã được tải lên thùng Amazon S3) trong bus Amazon Event Bridge mặc định, một quy tắc bus Amazon Event Bridge sẽ kích hoạt việc thực thi máy trạng thái AWS Step Functions để bắt đầu quy trình điều phối.

**Bước 8 (Bước trích xuất các trường từ tệp và phân loại tệp):**
- **Bước 8a:** Hàm AWS Lambda đầu tiên khởi động một tác vụ Amazon Bedrock Automation mới (tác vụ này trích xuất các trường cụ thể từ tệp đã tải lên và phân loại nó).
- **Bước 8b:** Sau khi tác vụ hoàn tất, kết quả được lưu trữ trong một thùng Amazon S3.
- **Bước 8c và 8d:** Khi nhận được sự kiện Amazon S3 (thông báo rằng kết quả đã được lưu trữ trong thùng Amazon S3) trên Amazon Event Bridge mặc định, một quy tắc bus Amazon Event Bridge sẽ kích hoạt việc thực thi một hàm AWS Lambda.
- **Bước 8e:** Một hàm AWS Lambda sẽ xuất bản kết quả lên web socket.

**Bước 9a và 9b:** Hàm AWS Lambda thứ hai gửi lời nhắc đến mô hình nền tảng Amazon Bedrock (Sonnet 3) để yêu cầu tóm tắt trong luồng tệp đã tải lên. Hàm AWS Lambda xuất bản dữ liệu luồng lên web socket.

Sau Bước 8e và Bước 9b, người dùng giờ đây có thể xem kết quả tóm tắt và thông tin chi tiết về trích xuất tệp đã tải lên trong ứng dụng web.

## Điều kiện tiên quyết

Để thực hiện và thiết lập giải pháp này, bạn phải có những điều sau:

- Tài khoản AWS
- Thiết bị có quyền truy cập vào tài khoản AWS của bạn với những thông tin sau:
  - Python 3.12 installed (including pip)
  - Node.js 20.12.0 installed
- Cho phép Model Access đến mô hình Claude 3 Sonnet trong Amazon Bedrock

**Lưu ý:** Việc triển khai giải pháp này sẽ phát sinh chi phí. Vui lòng xem lại trang giá của từng dịch vụ AWS được sử dụng trong bài viết này để biết chi tiết về chi phí. Chi phí vận hành giải pháp này chủ yếu phụ thuộc vào:
- Số lượng tài liệu (và kích thước của mỗi tài liệu)
- Số lượng người dùng đang hoạt động

## Thiết lập tự động hóa dữ liệu Amazon Bedrock

Trong phần này, chúng tôi thiết lập một Amazon Bedrock Data Automation project và Amazon Bedrock blueprint.

Một dự án bao gồm một danh sách các bản thiết kế, và mỗi bản thiết kế xác định các trường để trích xuất từ các loại tệp khác nhau (chẳng hạn như tài liệu hoặc hình ảnh). Trong bài viết này, chúng tôi sẽ xác định bản thiết kế cho giấy phép lái xe.

Hãy hoàn thành các bước sau để tạo một dự án Amazon Bedrock Data Automation và một bản thiết kế giấy phép lái xe:

1. Clone the GitHub repository:
   ```
   git clone https://github.com/aws-samples/sample-create-idp-with-appsyncevents-and-amazonbedrock.git
   ```

2. Đi tới `sample-create-idp-with-appsyncevents-and-amazonbedrock` folder:
   ```
   cd sample-create-idp-with-appsyncevents-and-amazonbedrock
   ```

3. Khởi tạo môi trường (chuẩn bị các tệp tập lệnh shell từ kho lưu trữ GitHub để sử dụng):
   ```
   chmod +x ./init-env.sh && source ./init-env.sh
   ```

4. Run the script `setup-bda-project.sh` để tạo một dự án Tự động hóa dữ liệu Amazon Bedrock và bản thiết kế mẫu giấy phép lái xe:
   ```
   ./setup-bda-project.sh
   ```

## Tạo websocket và backend phối hợp

Trong phần này, chúng tôi tạo các tài nguyên sau:

- Một thư mục người dùng để xác thực và ủy quyền web, được tạo bằng Amazon Cognito user pool. An Amazon Cognito identity pool cũng được tạo ra để xác thực rằng người dùng được phép tải tệp lên thông qua ứng dụng web.
- A websocket using AWS AppSync Events. Điều này cho phép ứng dụng web của chúng tôi nhận được các bản cập nhật theo thời gian thực để tóm tắt và trích xuất kết quả. Một lớp ủy quyền cũng được tạo ra để bảo vệ websocket khỏi những người dùng trái phép. Lớp này được triển khai với hàm ủy quyền Lambda để xác thực rằng các yêu cầu đến bao gồm thông tin ủy quyền hợp lệ.
- Một máy trạng thái sử dụng AWS Step Functions và AWS Lambda để điều phối các hoạt động tóm tắt và trích xuất từ nội dung phi cấu trúc
- Amazon S3 để lưu trữ và mã hóa chức năng AWS Lambda.

Hoàn thành các bước sau để tạo websocket và phần phụ trợ phối hợp của giải pháp, sử dụng AWS CloudFormation:

1. Tạo các thùng Amazon S3 được giải pháp sử dụng bằng cách chạy tập lệnh sau. Các thùng này sẽ lưu trữ các tệp do người dùng tải lên và các tệp mã của các hàm AWS Lambda được sử dụng trong giải pháp này.
   ```
   cd $CURRENT_DIR/s3; ./create-s3-buckets.sh
   ```

2. Tạo nhóm người dùng Amazon Cognito và nhóm danh tính bằng cách chạy `create-cognito-userpool.sh` script:
   ```
   cd $CURRENT_DIR/cognito; ./create-cognito-userpool.sh
   ```

3. Tạo web socket Sự kiện AWS AppSync bằng cách chạy tập lệnh sau:
   ```
   cd $CURRENT_DIR/appsync/; ./create-appsync-api.sh
   ```

4. Tạo máy trạng thái AWS Step Functions (bao gồm các hàm AWS Lambda) bằng cách chạy các tập lệnh sau:
   ```
   cd $CURRENT_DIR/orchestration/; ./create-orchestration.sh
   ```

## Cấu hình nhóm người dùng Amazon Cognito

Trong phần này, chúng ta sẽ tạo một người dùng trong nhóm người dùng Amazon Cognito. Người dùng này sẽ đăng nhập vào ứng dụng web của chúng ta.

Chạy lệnh script `create-cognito-testuser.sh` để tạo người dùng (đảm bảo cung cấp địa chỉ email của bạn):
```
cd $CURRENT_DIR/cognito; ./create-cognito-testuser.sh #your-email-address#
```

Sau khi bạn tạo người dùng, bạn sẽ nhận được email có mật khẩu tạm thời theo định dạng này: "Your username is #your-email-address# and temporary password is #temporary-password#."

Hãy ghi lại những thông tin đăng nhập này (địa chỉ email và mật khẩu tạm thời) để sử dụng sau này khi kiểm tra ứng dụng web.

## Tạo ứng dụng web

Trong phần này, chúng tôi xây dựng một ứng dụng web bằng AWS Amplify và phát hành ứng dụng đó để có thể truy cập thông qua URL điểm cuối.

Hoàn thành các bước sau để tạo ứng dụng web:

1. Chạy tập lệnh `create-webapp.sh` để tạo ứng dụng web với AWS Amplify:
   ```
   cd $CURRENT_DIR/amplify/; ./create-webapp.sh
   ```

2. Chạy tập lệnh `deploy.sh` để triển khai ứng dụng web:
   ```
   cd $CURRENT_DIR/amplify/amplify-idp; ./deploy.sh
   ```

Ứng dụng web hiện đã có sẵn để thử nghiệm và một URL sẽ được hiển thị, như trong ảnh chụp màn hình bên dưới. Hãy lưu ý URL để sử dụng trong phần sau.

## Kiểm tra ứng dụng web

Trong phần này, chúng tôi sẽ kiểm tra ứng dụng web và tải lên một tệp để xử lý:

1. Mở URL của ứng dụng AWS Amplify trong trình duyệt web của bạn.
2. Nhập thông tin đăng nhập (email và mật khẩu tạm thời bạn đã nhận trước đó khi cấu hình nhóm người dùng trong Amazon Cognito) và chọn Đăng nhập.
3. Khi được nhắc, hãy nhập mật khẩu mới và chọn Đổi mật khẩu.
4. Bây giờ bạn có thể thấy giao diện web.
5. Tải xuống mẫu giấy phép lái xe tại địa điểm này và tải lên thông qua ứng dụng web bằng máy ảnh hoặc tệp trong thiết bị cục bộ của bạn, như minh họa.
6. Sau khi tệp được tải lên, bạn sẽ bắt đầu nhận được phản hồi trong ứng dụng web. Khi tất cả các thao tác hoàn tất, bạn sẽ thấy kết quả tương đương với hình ảnh chụp màn hình sau:

**Lưu ý:** Nếu bạn dự định sử dụng các hình ảnh mẫu giấy phép lái xe khác với các định dạng khác, bạn có thể phải cập nhật bản thiết kế Bedrock Data Automation blueprint hiện có mà chúng tôi đã tạo trước đó hoặc xác định một bản thiết kế mới trong Bedrock Data Automation project mà chúng tôi đã tạo trước đó để các hình ảnh mới này hoạt động. Để biết thêm thông tin, vui lòng xem Bedrock Data Automation documentation.

## Dọn dẹp

Để đảm bảo không phát sinh thêm chi phí, hãy xóa các tài nguyên đã được cung cấp trong tài khoản của bạn. Hãy đảm bảo bạn đang sử dụng đúng tài khoản AWS trước khi xóa các tài nguyên sau.

**Lưu ý quan trọng:** Bạn nên thận trọng khi thực hiện các bước trên. Đảm bảo bạn đang xóa tài nguyên trong đúng tài khoản AWS.

Bạn có thể điều hướng đến bảng điều khiển AWS CloudFormation để xóa các ngăn xếp CloudFormation được liên kết với các tài nguyên đã cung cấp hoặc sử dụng tập lệnh trợ giúp dọn dẹp `cleanup.sh` có sẵn ở gốc thư mục `sample-create-idp-with-appsyncevents-and-amazonbedrock`:
```
./cleanup.sh #region#
```

## Phần kết luận

Trong bài viết này, chúng tôi đã giới thiệu giải pháp tạo đường dẫn xử lý tài liệu, với một ứng dụng web sử dụng các dịch vụ không máy chủ. Thông qua ứng dụng web, chúng tôi có thể tải tệp lên và nhận phản hồi theo thời gian thực cho các loại thao tác khác nhau (tóm tắt, trích xuất các trường cụ thể và phân loại). Đầu tiên, chúng tôi tạo một dự án Amazon Bedrock Data Automation (với bản thiết kế giấy phép lái xe). Sau đó, chúng tôi tạo một web socket cùng với giải pháp điều phối bằng cách sử dụng máy trạng thái (các hàm AWS Step và hàm AWS Lambda). Chúng tôi cũng đã cấu hình một nhóm người dùng để cấp quyền truy cập cho người dùng vào ứng dụng web. Cuối cùng, chúng tôi đã tạo giao diện người dùng (frontend) của ứng dụng web trên AWS Amplify.

Để đi sâu hơn vào giải pháp này, a self-paced workshop is available trong AWS Workshop Studio.
