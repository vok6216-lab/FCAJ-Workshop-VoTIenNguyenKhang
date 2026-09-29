---

title: "Nhật ký công việc Tuần 8"
date: "2026-11-02"
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
----------------------

### Mục tiêu Tuần 8:

* Xây dựng nền tảng Frontend với React 19 và Vite.
* Triển khai cấu trúc định tuyến và các thành phần Layout.
* Xây dựng các UI Component có khả năng tái sử dụng bằng TailwindCSS.
* Thiết lập tầng dịch vụ API để giao tiếp với Backend.

### Các công việc cần thực hiện trong tuần:

| Ngày | Công việc                                                                                                                                                                                           | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ------------------ |
| 1    | - Thiết lập React Router để điều hướng <br> - Tạo các thành phần Layout chính (Header, Sidebar, Footer) <br> - Triển khai cấu trúc thiết kế Responsive                                              | 02/11/2026   | 02/11/2026      |                    |
| 2    | - Xây dựng các UI Component có thể tái sử dụng (Button, Input, Card, Modal) <br> - Triển khai chức năng chuyển đổi giao diện sáng/tối <br> - Tạo các Component hiển thị trạng thái Loading và Error | 03/11/2026   | 03/11/2026      |                    |
| 3    | - Thiết lập tầng dịch vụ API bằng axios/fetch <br> - Tạo cấu hình các API Endpoint <br> - Triển khai xử lý lỗi và Response Interceptors                                                             | 04/11/2026   | 04/11/2026      |                    |
| 4    | - Xây dựng trang Dashboard với các Widget tổng quan <br> - Tạo cấu trúc Menu điều hướng <br> - Triển khai định tuyến trang và Protected Routes                                                      | 05/11/2026   | 05/11/2026      |                    |
| 5    | - Thêm hiệu ứng Framer Motion vào các Component <br> - Tích hợp biểu tượng Lucide React trên toàn bộ giao diện <br> - Hoàn thiện UI/UX với các hiệu ứng chuyển đổi mượt mà                          | 06/11/2026   | 06/11/2026      |                    |
| 6    | - Kiểm tra thiết kế Responsive trên nhiều thiết bị <br> - Tối ưu hiệu suất Component <br> - Tài liệu hóa cách sử dụng Component và Props                                                            | 07/11/2026   | 07/11/2026      |                    |

### Kết quả đạt được trong Tuần 8:

Đã xây dựng thành công nền tảng Frontend với kiến trúc React hiện đại:

* Triển khai hệ thống định tuyến toàn diện:

  * Cấu hình React Router với các Nested Routes.
  * Tạo Protected Route Component để kiểm soát xác thực người dùng.
  * Thiết lập Navigation Guard và hiệu ứng chuyển đổi giữa các Route.
  * Triển khai Dynamic Route Parameters.

* Xây dựng hoàn chỉnh cấu trúc Layout:

  * Component Header Responsive với User Menu.
  * Sidebar điều hướng có thể thu gọn và hiển thị trạng thái Active.
  * Component Footer hiển thị thông tin hệ thống.
  * Thiết kế Responsive cho thiết bị di động với Hamburger Menu.

* Phát triển thư viện UI Component có khả năng tái sử dụng:

  * Button Component với nhiều biến thể (primary, secondary, danger).
  * Input Component với các trạng thái Validation.
  * Card Component dùng để hiển thị nội dung.
  * Modal/Dialog Component cho các lớp Overlay.
  * Loading Spinner và Skeleton Screen.
  * Error Boundary và Component hiển thị lỗi.

* Thiết lập tầng giao tiếp API:

  * Tạo API Service tập trung sử dụng axios.
  * Triển khai Request/Response Interceptors.
  * Thiết lập cấu hình Environment Variables.
  * Xây dựng cơ chế xử lý lỗi và Retry.
  * Tạo các hằng số và kiểu dữ liệu cho API Endpoint.

* Thiết kế và triển khai Dashboard:

  * Các Widget tổng quan hiển thị những chỉ số quan trọng.
  * Các Card truy cập nhanh đến những chức năng chính.
  * Feed hiển thị hoạt động gần đây.
  * Tạo các khu vực hiển thị dữ liệu thống kê.

* Tích hợp các cải tiến giao diện hiện đại:

  * Sử dụng Framer Motion để tạo hiệu ứng chuyển trang mượt mà.
  * Tích hợp Lucide React Icons trên toàn bộ ứng dụng.
  * Triển khai chức năng chuyển đổi giao diện Dark/Light.
  * Thiết lập Responsive Breakpoints cho Mobile, Tablet và Desktop.

* Tối ưu hiệu suất ứng dụng:

  * Code Splitting bằng React.lazy().
  * Sử dụng Component Memoization khi phù hợp.
  * Tối ưu kích thước Bundle với Vite.
  * Triển khai Loading State nhằm cải thiện trải nghiệm người dùng.

* Tạo tài liệu hướng dẫn đầy đủ:

  * Hướng dẫn sử dụng các Component.
  * Quy chuẩn tích hợp API.
  * Quy ước Styling với TailwindCSS.
  * Tài liệu hóa quy trình phát triển.
