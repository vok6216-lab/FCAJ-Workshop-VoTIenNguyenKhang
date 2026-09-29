---

title: "Nhật ký công việc Tuần 10"
date: "2026-11-09"
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
-----------------------

### Mục tiêu Tuần 10:

* Triển khai Backend cho hệ thống Nhận diện Khuôn mặt bằng Python Flask.
* Phát triển các thuật toán phát hiện và nhận diện khuôn mặt.
* Xây dựng chức năng đăng ký người dùng bằng cách chụp ảnh khuôn mặt.
* Xây dựng hệ thống chấm công bằng nhận diện khuôn mặt theo thời gian thực.

### Các công việc cần thực hiện trong tuần:

| Ngày | Công việc                                                                                                                                                                           | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| ---- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ------------------ |
| 1    | - Thiết lập Backend API cho hệ thống nhận diện khuôn mặt <br> - Triển khai phát hiện khuôn mặt bằng OpenCV <br> - Xây dựng hệ thống tạo Face Encoding                               | 09/11/2026   | 09/11/2026      |                    |
| 2    | - Xây dựng API đăng ký người dùng kèm ảnh khuôn mặt <br> - Triển khai chụp ảnh khuôn mặt từ nhiều góc độ <br> - Xây dựng hệ thống lưu trữ Face Encoding                             | 10/11/2026   | 10/11/2026      |                    |
| 3    | - Phát triển thuật toán đối chiếu khuôn mặt <br> - Triển khai hệ thống tính điểm độ tin cậy <br> - Tạo API Endpoint cho chức năng nhận diện khuôn mặt                               | 11/11/2026   | 11/11/2026      |                    |
| 4    | - Xây dựng Component Frontend nhận diện khuôn mặt theo thời gian thực <br> - Tích hợp quyền truy cập Camera và Video Stream <br> - Hiển thị quá trình phát hiện khuôn mặt trực tiếp | 12/11/2026   | 12/11/2026      |                    |
| 5    | - Kết nối hệ thống nhận diện khuôn mặt với hệ thống chấm công <br> - Triển khai tự động ghi nhận Check-in/Check-out <br> - Xây dựng cơ chế ghi log chấm công                        | 13/11/2026   | 13/11/2026      |                    |
| 6    | - Kiểm tra độ chính xác và hiệu suất nhận diện khuôn mặt <br> - Tối ưu tốc độ nhận diện <br> - Xử lý các trường hợp đặc biệt và tình huống lỗi                                      | 14/11/2026   | 14/11/2026      |                    |

### Kết quả đạt được trong Tuần 10:

Đã triển khai thành công hệ thống **Chấm công bằng Nhận diện Khuôn mặt** toàn diện:

* Xây dựng Backend nhận diện khuôn mặt:

  * Tạo các Flask API Endpoint phục vụ các chức năng nhận diện khuôn mặt.
  * Phát hiện khuôn mặt bằng thư viện OpenCV và dlib.
  * Tạo Face Encoding bằng thư viện face_recognition.
  * Xây dựng hệ thống huấn luyện mô hình nhằm cải thiện độ chính xác.
  * Xây dựng hệ thống lưu trữ và truy xuất Face Encoding.

* Xây dựng chức năng đăng ký người dùng bằng nhận diện khuôn mặt:

  * Chụp nhiều ảnh từ các góc độ khác nhau.
  * Tạo Face Encoding trong quá trình đăng ký.
  * Lưu trữ Face Encoding vào cơ sở dữ liệu.
  * Liên kết User ID và tên người dùng với dữ liệu khuôn mặt.
  * Kiểm tra dữ liệu đăng ký và xử lý lỗi.

* Triển khai nhận diện khuôn mặt theo thời gian thực:

  * Tích hợp Camera Stream trực tiếp.
  * Phát hiện và theo dõi khuôn mặt theo thời gian thực.
  * Đối chiếu khuôn mặt với danh sách người dùng đã đăng ký.
  * Tính toán và hiển thị Confidence Score.
  * Hiển thị kết quả nhận diện.

* Xây dựng hệ thống ghi nhận chấm công:

  * Tự động phát hiện Check-in/Check-out.
  * Ghi nhận lịch sử chấm công kèm thời gian.
  * Xác định và xác thực người dùng.
  * Theo dõi lịch sử chấm công.
  * Ngăn chặn việc ghi nhận chấm công trùng lặp.

* Phát triển giao diện nhận diện khuôn mặt trên Frontend:

  * Component truy cập Camera và Video Stream.
  * Hiển thị khung nhận diện khuôn mặt trực tiếp.
  * Hiển thị trạng thái nhận diện.
  * Hiển thị Confidence Score.
  * Hiển thị thông tin người dùng khi nhận diện thành công.

* Tối ưu hiệu suất hệ thống:

  * Tối ưu thuật toán so sánh Face Encoding.
  * Tăng tốc quá trình phát hiện khuôn mặt.
  * Tối ưu các truy vấn cơ sở dữ liệu phục vụ đối chiếu khuôn mặt.
  * Giảm độ trễ trong quá trình nhận diện.
  * Tối ưu bộ nhớ khi lưu trữ Face Encoding.

* Xử lý lỗi và các trường hợp đặc biệt:

  * Xử lý trường hợp không phát hiện được khuôn mặt.
  * Xử lý trường hợp có nhiều khuôn mặt trong khung hình.
  * Xử lý trường hợp Confidence Score thấp.
  * Xử lý lỗi truy cập Camera.
  * Xử lý các vấn đề về kết nối mạng.

* Thực hiện kiểm thử toàn diện:

  * Kiểm tra độ chính xác trong nhiều điều kiện ánh sáng khác nhau.
  * Đánh giá hiệu suất hệ thống.
  * Kiểm tra các trường hợp đặc biệt.
  * Kiểm tra trải nghiệm người dùng.
  * Kiểm tra độ ổn định và độ tin cậy của hệ thống.
