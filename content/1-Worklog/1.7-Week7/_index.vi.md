---

title: "Nhật ký công việc Tuần 7"
date: "2026-10-26"
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
----------------------

### Mục tiêu Tuần 7:

* Khởi động dự án Hệ thống Quản lý Nhân sự kết hợp chấm công bằng nhận diện khuôn mặt.
* Phân tích yêu cầu và lập kế hoạch cho dự án.
* Nghiên cứu và lựa chọn công nghệ phù hợp.
* Thiết lập môi trường phát triển và cấu trúc dự án.

### Các công việc cần thực hiện trong tuần:

| Ngày | Công việc                                                                                                                                                          | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------ | --------------- | ------------------ |
| 1    | - Phân tích yêu cầu dự án <br> - Xác định các tính năng và chức năng chính <br> - Nghiên cứu các lựa chọn về công nghệ                                             | 26/10/2026   | 26/10/2026      |                    |
| 2    | - Hoàn thiện công nghệ sử dụng: React 19, Vite, TailwindCSS, Flask <br> - Thiết kế kiến trúc hệ thống (tách biệt Frontend/Backend) <br> - Tạo cấu trúc dự án       | 27/10/2026   | 27/10/2026      |                    |
| 3    | - Thiết lập môi trường phát triển <br> - Khởi tạo dự án React với Vite <br> - Cấu hình TailwindCSS và các thư viện phụ thuộc cơ bản                                | 28/10/2026   | 28/10/2026      |                    |
| 4    | - Thiết lập cấu trúc Backend bằng Python Flask <br> - Cài đặt các package Python cần thiết (face_recognition, opencv, flask) <br> - Cấu hình các thư mục của dự án | 29/10/2026   | 29/10/2026      |                    |
| 5    | - Thiết kế schema cơ sở dữ liệu <br> - Thiết kế cấu trúc các API Endpoint <br> - Thiết lập quản lý phiên bản bằng Git                                              | 30/10/2026   | 30/10/2026      |                    |
| 6    | - Tài liệu hóa quá trình thiết lập và kiến trúc dự án <br> - Tạo README ban đầu với tổng quan dự án <br> - Lập kế hoạch tiến độ phát triển cho các tuần tiếp theo  | 31/10/2026   | 31/10/2026      |                    |

### Kết quả đạt được trong Tuần 7:

Đã khởi động thành công dự án Hệ thống Quản lý Nhân sự với kế hoạch phát triển toàn diện:

* Hoàn thành phân tích yêu cầu chi tiết, bao gồm:

  * Các yêu cầu của hệ thống Quản lý Nhân viên.
  * Đặc tả hệ thống Chấm công bằng Nhận diện Khuôn mặt.
  * Các chức năng Quản lý Lương.
  * Quản lý Người dùng và phân quyền dựa trên vai trò.
  * Nhu cầu về Báo cáo và Phân tích dữ liệu.

* Lựa chọn và hoàn thiện công nghệ sử dụng:

  * Frontend: React 19 kết hợp với Vite để xây dựng ứng dụng hiện đại.
  * Styling: TailwindCSS theo phương pháp Utility-first CSS.
  * Routing: React Router để điều hướng phía client.
  * Icons: Lucide React để sử dụng hệ thống biểu tượng nhất quán.
  * Animations: Framer Motion để tạo các hiệu ứng chuyển đổi giao diện mượt mà.
  * Backend: Python Flask để xây dựng RESTful API.
  * Face Recognition: Thư viện face_recognition kết hợp với OpenCV.

* Xây dựng kiến trúc dự án:

  * Tách Frontend và Backend thành các module độc lập.
  * Thiết kế cấu trúc thư mục có khả năng mở rộng cho components, pages và services.
  * Lập kế hoạch phương thức giao tiếp API giữa Frontend và Backend.

* Thiết lập hoàn chỉnh môi trường phát triển:

  * Khởi tạo dự án React với cấu hình Vite.
  * Cấu hình TailwindCSS với các thiết lập theme tùy chỉnh.
  * Cài đặt và cấu hình tất cả các thư viện phụ thuộc cần thiết.
  * Thiết lập môi trường Python Virtual Environment cho Backend.

* Xây dựng nền tảng Backend:

  * Xây dựng cấu trúc ứng dụng Flask theo mô hình module.
  * Cài đặt các thư viện và dependency phục vụ nhận diện khuôn mặt.
  * Cấu hình các thư mục của dự án (datasets, trainer, attendance, logs).
  * Thiết lập cấu hình Docker để phục vụ việc container hóa.

* Thiết kế schema cơ sở dữ liệu:

  * Các bảng thông tin nhân viên.
  * Cấu trúc lưu trữ dữ liệu chấm công.
  * Quản lý xác thực người dùng và phân quyền.
  * Schema quản lý lương và công việc.

* Thiết lập quy trình phát triển:

  * Khởi tạo Git Repository với file .gitignore phù hợp.
  * Tạo tài liệu README đầy đủ.
  * Lập kế hoạch phát triển dự án trong 6 tuần.
  * Thiết lập quản lý dự án và theo dõi công việc.

* Chuẩn bị cho phương pháp phát triển Agile với các mốc quan trọng và sản phẩm đầu ra rõ ràng cho những tuần tiếp theo.
