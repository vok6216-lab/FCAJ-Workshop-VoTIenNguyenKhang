---

title: "Nhật ký công việc Tuần 3"
date: "2026-09-28"
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
----------------------

### Mục tiêu Tuần 3:

* Làm quen với các thành viên của First Cloud Journey.
* Hiểu các dịch vụ AWS cơ bản và thành thạo việc sử dụng AWS Management Console & AWS CLI.

### Các công việc cần thực hiện trong tuần:

| Ngày | Công việc                                                                                                                                                                                                           | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                      |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | --------------------------------------- |
| 2    | - Gặp gỡ và làm quen với các thành viên FCJ <br> - Đọc và ghi chú các quy định, nội quy của kỳ thực tập                                                                                                             | 29/09/2026   | 29/09/2026      |                                         |
| 3    | - Tổng quan về AWS và các nhóm dịch vụ của AWS (Compute, Storage, Networking, Database, v.v.)                                                                                                                       | 30/09/2026   | 30/09/2026      | https://cloudjourney.awsstudygroup.com/ |
| 4    | - Tạo tài khoản AWS Free Tier <br> - Tìm hiểu AWS Management Console & AWS CLI <br> - **Thực hành:** tạo tài khoản, cài đặt & cấu hình AWS CLI                                                                      | 01/10/2026   | 01/10/2026      | https://cloudjourney.awsstudygroup.com/ |
| 5    | - Tìm hiểu chuyên sâu về Amazon EC2 (Instance Types, AMI, EBS, Key Pairs, Instance Store, User Data, Metadata, các mô hình tính giá, Auto Scaling, v.v.) <br> - Các dịch vụ liên quan: Lightsail, EFS, FSx, AWS MGN | 02/10/2026   | 02/10/2026      | https://cloudjourney.awsstudygroup.com/ |
| 6    | - **Thực hành:** <br>  ∘ Khởi chạy các EC2 Instance <br>  ∘ Kết nối thông qua SSH/RDP <br>  ∘ Gắn EBS Volume <br>  ∘ Tạo Snapshot & Custom AMI                                                                      | 03/10/2026   | 03/10/2026      | https://cloudjourney.awsstudygroup.com/ |

### Kết quả đạt được trong Tuần 3:

Đã hoàn thành 100% các công việc được lên kế hoạch với những kiến thức và kỹ năng chính đạt được như sau:

* Hiểu toàn diện về **Amazon EC2** – các máy chủ ảo có khả năng mở rộng, có thể thay thế hoàn toàn máy chủ vật lý cho hầu hết các loại workload như lưu trữ website, ứng dụng, cơ sở dữ liệu, xác thực người dùng, v.v.

* Nắm vững cách cấu hình phần cứng thông qua **Instance Types** (CPU, bộ nhớ, mạng, lưu trữ) và các khái niệm liên quan như Hypervisor (Nitro/KVM/HVM/PV), Placement Groups và Availability Zones.

* Hiểu rõ về **AMI (Amazon Machine Image)**: bao gồm root volume, launch permissions và block device mapping; có thể sử dụng AMI do AWS cung cấp, AMI từ Marketplace hoặc AMI tùy chỉnh; thực hiện sao lưu thông qua việc tạo AMI hoặc EBS Snapshot.

* Nắm vững **Key Pairs**: sử dụng để xác thực SSH đối với Linux và giải mã mật khẩu Administrator được mã hóa đối với các Windows Instance.

* Hiểu sâu về **Amazon EBS (Elastic Block Store)**:

  * Là bộ lưu trữ dạng block có tính bền vững, độc lập với vòng đời của EC2 và được kết nối thông qua mạng EBS riêng trong cùng Availability Zone.

  * Bao gồm các dòng SSD và HDD, cung cấp độ sẵn sàng 99,99% thông qua việc sao chép dữ liệu trên nhiều node.

  * Hỗ trợ tính năng Multi-Attach trên các Instance sử dụng Nitro.

  * Hỗ trợ sao lưu thông qua Incremental Snapshot được lưu trữ trên S3.

* Hiểu về **Instance Store**: bộ lưu trữ NVMe hiệu năng cao, tạm thời và được gắn vật lý với máy chủ; dữ liệu sẽ bị mất khi thực hiện Stop Instance (nhưng được giữ lại khi Reboot); phù hợp để sử dụng cho cache, buffer, swap và dữ liệu tạm thời.

* Tìm hiểu về **User Data** sử dụng các script Bash/PowerShell và **Instance Metadata** để tự động hóa quá trình cấu hình và khởi tạo Instance.

* Tìm hiểu các mô hình tính giá EC2 và **Auto Scaling**:

  * On-Demand, Reserved Instances, Savings Plans và Spot Instances.

  * Auto Scaling Groups hỗ trợ nhiều mô hình tính giá, hoạt động trên nhiều Availability Zone và tự động đăng ký Instance với Elastic Load Balancer.

* Tìm hiểu các dịch vụ liên quan:

  * **Amazon Lightsail**: VPS đơn giản với chi phí thấp, đi kèm gói truyền dữ liệu, phù hợp cho môi trường phát triển/kiểm thử và các workload nhẹ.

  * **EFS (Elastic File System)**: hệ thống file NFS được AWS quản lý hoàn toàn dành cho Linux, tính phí dựa trên dung lượng sử dụng và hỗ trợ truy cập từ hệ thống on-premises thông qua Direct Connect/VPN.

  * **FSx**: dịch vụ File Server Windows được quản lý (SMB) và FSx for Lustre, hỗ trợ tính năng khử trùng lặp dữ liệu (deduplication), giúp tiết kiệm khoảng 30–50% dung lượng.

  * **AWS Application Migration Service (MGN)**: hỗ trợ sao chép dữ liệu liên tục để thực hiện quá trình lift-and-shift migration và Disaster Recovery từ máy chủ on-premises/vật lý/ảo sang AWS.

* Hoàn thành tốt phần thực hành: khởi chạy EC2 Instance, kết nối thông qua SSH/RDP, gắn EBS Volume, tạo Snapshot và Custom AMI.
