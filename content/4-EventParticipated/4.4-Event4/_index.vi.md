---
title: "Event 4"
date: 2025-11-17
weight: 4
chapter: false
pre: " <b> 4.4. </b> "
---

# Bài thu hoạch "AWS Cloud Mastery Series #2"

### Mục Đích Của Sự Kiện

Sự kiện nhằm khám phá tư duy và thực hành tốt nhất của DevOps, tập trung vào việc hiểu DevOps là gì, các nguyên tắc cốt lõi, chiến lược đo lường và cách tiếp cận thực tế để triển khai văn hóa DevOps trong các tổ chức.

### Danh Sách Diễn Giả

**Trương Quang Tịnh** - AWS Community Builder, Platform Engineer tại tymeX

### Nội Dung Nổi Bật

#### DevOps là gì?

**Định Nghĩa:**

- DevOps là một người hiểu và kết nối khoảng cách giữa Development (Dev) và Operations (Ops)

- Có nhiều công cụ khác nhau để quản lý ứng dụng

- Mọi thứ phải được tự động hóa vì code giảm rủi ro liên quan đến công việc

- Phải có hệ thống đánh giá và giám sát để có nguồn đánh giá cách ứng dụng chạy

#### Các Nguyên Tắc Cốt Lõi của DevOps

**1. Hợp Tác & Trách Nhiệm Chia Sẻ**

**Nội Dung:**

- DevOps nhấn mạnh rằng các nhóm development (Dev) và operations (Ops) phải chia sẻ trách nhiệm cho toàn bộ vòng đời sản phẩm

- Câu nói điển hình: "You build it, you run it"

**Tại sao quan trọng:**

- Giảm xung đột giữa Dev và Ops

- Tăng tính chủ động trong việc sửa lỗi và cải thiện tính năng

- Giảm thời gian triển khai và khắc phục sự cố

**Ví dụ thực tế:**

- Một nhóm Dev triển khai một microservice mới trên AWS Lambda. Khi có lỗi làm tăng độ trễ API, nhóm Dev phân tích logs từ CloudWatch và sửa nó mà không "chuyển bóng" cho Ops

- Ở các công ty như Amazon, nhóm phát triển chịu trách nhiệm 24/7 cho dịch vụ họ tạo ra

**2. Tự Động Hóa Mọi Thứ**

**Nội Dung:**

- DevOps ưu tiên tự động hóa càng nhiều càng tốt: CI/CD, test, provisioning, monitoring, rollback, security scanning...

- Nguyên tắc chính: "Manual work is technical debt"

**Lý do quan trọng:**

- Giảm lỗi con người

- Tăng tốc triển khai

- Dễ dàng lặp lại quy trình

- Cho phép mở rộng nhanh chóng

**Ví dụ thực tế:**

- Sử dụng GitHub Actions + Terraform để tự động tạo hạ tầng AWS mỗi khi pipeline chạy

- Mỗi Pull Request tự động chạy unit tests, linting và security scans sử dụng các công cụ như SonarQube, Snyk

- Triển khai ứng dụng production sử dụng ArgoCD hoặc Jenkins chỉ với 1 commit

**3. Học Tập Liên Tục & Thử Nghiệm**

**Nội Dung:**

- Văn hóa DevOps khuyến khích học hỏi điều mới, thử nghiệm và chấp nhận thất bại nhỏ

- Nguyên tắc chính: "Fail fast, learn faster" và "Experiment with new tools and practices"

**Tại sao quan trọng:**

- Công nghệ thay đổi rất nhanh—DevOps phải cập nhật

- Thử nghiệm giúp cải thiện liên tục

- Giảm nỗi sợ thất bại → tăng đổi mới

**Ví dụ thực tế:**

- Một nhóm chuyển từ Jenkins sang GitHub Actions để giảm thời gian chạy pipeline từ 15 phút xuống 5 phút

- Tổ chức game days trên AWS để thực hành crash các dịch vụ mô phỏng và kiểm tra khả năng phục hồi

- Thử nghiệm Canary Deployment hoặc Blue-Green Deployment để giảm rủi ro khi triển khai tính năng mới

**4. Đo Lường**

**Nội Dung:**

- DevOps yêu cầu đo lường liên tục và thời gian thực

- Ví dụ: logs, metrics, tracing, SLOs, SLIs

**Tại sao quan trọng:**

- Không thể cải thiện những gì không thể đo lường

- Hiểu sức khỏe hệ thống và hành vi của sản phẩm

- Giảm thời gian phát hiện lỗi (MTTD) và thời gian phục hồi (MTTR)

**Ví dụ thực tế:**

- Sử dụng Prometheus + Grafana để giám sát CPU, latency, error rate

- Thiết lập AWS CloudWatch Alarms để cảnh báo khi tỷ lệ lỗi 5xx vượt quá 2%

- Giám sát DORA metrics: Deployment Frequency, Lead Time for Changes, MTTR, Change Failure Rate

#### Mục Tiêu và Lợi Ích của DevOps

**Giám Sát Sức Khỏe Triển Khai:**

- Giám sát trạng thái triển khai: có lỗi nào không, có rollback không, mất bao lâu để triển khai

- Giúp phát hiện lỗi triển khai sớm

- Giảm rủi ro production

- Ví dụ: Sử dụng AWS CodeDeploy hoặc ArgoCD để theo dõi trạng thái mỗi triển khai và tự động rollback nếu error rate > 5%

**Cải Thiện Tính Linh Hoạt:**

- Tính linh hoạt = khả năng thay đổi nhanh chóng

- DevOps giúp doanh nghiệp phát hành nhiều hơn, nhanh hơn và tự tin hơn

- Phát hành tính năng sớm hơn đối thủ

- Rút ngắn thời gian từ ý tưởng đến sản phẩm

- Ví dụ: Một startup triển khai 20–30 lần/ngày nhờ CI/CD + microservices

**Đảm Bảo Tính Ổn Định Hệ Thống:**

- Tính ổn định = hệ thống chạy ổn định, ít downtime

- Tránh mất doanh thu

- Tăng niềm tin với khách hàng

- Ví dụ: Sử dụng AWS autoscaling + health checks để đảm bảo dịch vụ chạy mượt mà ngay cả khi traffic tăng đột biến

**Tối Ưu Trải Nghiệm Khách Hàng:**

- Quan sát metrics để cải thiện: tốc độ phản hồi, tỷ lệ lỗi, downtime → trải nghiệm tốt hơn

- Ví dụ: Giảm API latency từ 500ms xuống 120ms bằng cách tối ưu hóa hạ tầng và pipeline

**Biện Minh Đầu Tư Công Nghệ:**

- Sử dụng dữ liệu để chứng minh: DevOps giúp giảm lỗi, tăng tốc phát hành và tiết kiệm chi phí

- Ví dụ: Sử dụng DORA metrics để báo cáo với lãnh đạo rằng triển khai CI/CD giảm time to market 40%

### Những Gì Học Được

1. **DevOps là Tư Duy, Không Chỉ Công Cụ:**

   - DevOps là về việc kết nối Dev và Ops, không chỉ sử dụng công cụ cụ thể

   - Hiểu hệ thống quan trọng hơn biết công cụ

   - Tự động hóa giảm rủi ro và lỗi con người

2. **Bốn Nguyên Tắc Cốt Lõi:**

   - **Hợp Tác & Trách Nhiệm Chia Sẻ**: "You build it, you run it"

   - **Tự Động Hóa Mọi Thứ**: Manual work is technical debt

   - **Học Tập Liên Tục & Thử Nghiệm**: Fail fast, learn faster

   - **Đo Lường**: Không thể cải thiện những gì không thể đo lường

3. **Đo Lường là Quan Trọng:**

   - Sử dụng logs, metrics, tracing, SLOs, SLIs

   - Giám sát DORA metrics để cải thiện liên tục

   - Giám sát thời gian thực giúp giảm MTTD và MTTR

4. **Lợi Ích của DevOps:**

   - Cải thiện tính linh hoạt và tần suất triển khai

   - Đảm bảo tính ổn định hệ thống và giảm downtime

   - Tối ưu trải nghiệm khách hàng

   - Biện minh đầu tư công nghệ bằng dữ liệu

5. **Thực Hành Tốt Nhất:**

   - Bắt đầu với những điều cơ bản (Linux, networking, Git, cloud basics)

   - Học bằng cách xây dựng dự án thực tế

   - Tài liệu hóa mọi thứ để hợp tác tốt hơn

### Ứng Dụng Vào Công Việc

1. **Triển Khai Trách Nhiệm Chia Sẻ:**

   - Khuyến khích các nhóm Dev chịu trách nhiệm về dịch vụ của họ

   - Thiết lập trách nhiệm 24/7 cho các dịch vụ được tạo ra

   - Giảm handoff giữa các nhóm Dev và Ops

2. **Tự Động Hóa Mọi Thứ:**

   - Thiết lập CI/CD pipelines sử dụng GitHub Actions hoặc Jenkins

   - Tự động hóa provisioning hạ tầng với Terraform

   - Triển khai automated testing, linting và security scanning

   - Sử dụng các công cụ như ArgoCD cho triển khai tự động

3. **Thiết Lập Hệ Thống Đo Lường:**

   - Thiết lập monitoring với Prometheus + Grafana hoặc AWS CloudWatch

   - Theo dõi DORA metrics (Deployment Frequency, Lead Time, MTTR, Change Failure Rate)

   - Cấu hình cảnh báo cho error rates và sức khỏe hệ thống

   - Giám sát sức khỏe triển khai và triển khai rollback tự động

4. **Thúc Đẩy Học Tập Liên Tục:**

   - Tổ chức game days để thực hành kiểm tra khả năng phục hồi

   - Thử nghiệm chiến lược triển khai (Canary, Blue-Green)

   - Cập nhật với công cụ và thực hành mới

   - Khuyến khích thử nghiệm và học hỏi từ thất bại

5. **Bắt Đầu với Những Điều Cơ Bản:**

   - Xây dựng nền tảng vững chắc về Linux, networking, Git và cloud basics

   - Học bằng cách xây dựng dự án thực tế (Docker + Nginx, CI/CD pipelines, monitoring)

   - Tài liệu hóa mọi thứ: các bước, lỗi và giải pháp

### Trải nghiệm trong event

Sự kiện cung cấp những hiểu biết toàn diện về tư duy và văn hóa DevOps, vượt ra ngoài chỉ công cụ và tập trung vào các nguyên tắc cơ bản thúc đẩy triển khai DevOps thành công.

#### Hiểu Văn Hóa DevOps

- Học được rằng DevOps về cơ bản là về việc kết nối Dev và Ops, không chỉ sử dụng công cụ cụ thể

- Hiểu tầm quan trọng của trách nhiệm chia sẻ và hợp tác

- Nhận ra rằng tự động hóa là điều cần thiết để giảm rủi ro và lỗi con người

#### Các Nguyên Tắc Cốt Lõi trong Thực Tế

- **Hợp Tác**: Nhận ra cách "You build it, you run it" thay đổi động lực nhóm và trách nhiệm

- **Tự Động Hóa**: Hiểu tại sao "Manual work is technical debt" và cách tự động hóa tăng tốc mọi thứ

- **Học Tập**: Đánh giá cao giá trị của tư duy "Fail fast, learn faster" trong việc thúc đẩy đổi mới

- **Đo Lường**: Nhận ra rằng đo lường là nền tảng cho cải thiện liên tục

#### Ứng Dụng Thực Tế

- Học về các ví dụ thực tế từ các công ty như Amazon

- Hiểu cách triển khai hệ thống monitoring và đo lường

- Có được hiểu biết về chiến lược triển khai và công cụ tự động hóa

- Khám phá tầm quan trọng của DORA metrics để theo dõi thành công DevOps

#### Hiểu Biết Chính

- DevOps là sự thay đổi văn hóa, không chỉ là một bộ công cụ

- Đo lường và giám sát là quan trọng cho thành công

- Tự động hóa giảm rủi ro và cho phép mở rộng nhanh chóng

- Học tập liên tục và thử nghiệm thúc đẩy đổi mới

#### Một số hình ảnh khi tham gia sự kiện

![The Problem Before DevOps](/images/4-EventParticipated/4.4-Event4/problem-before-devops.jpg)

![Next-Generation DevOps](/images/4-EventParticipated/4.4-Event4/next-generation-devops.jpg)

![Your DevOps Journey](/images/4-EventParticipated/4.4-Event4/devops-journey.jpg)

![Measuring Success: DevOps Metrics](/images/4-EventParticipated/4.4-Event4/devops-metrics.jpg)

> Tổng thể, sự kiện đã thành công trong việc truyền đạt rằng DevOps về cơ bản là về văn hóa, hợp tác và cải thiện liên tục. Sự nhấn mạnh vào đo lường, tự động hóa và trách nhiệm chia sẻ cung cấp nền tảng vững chắc cho việc triển khai các thực hành DevOps mang lại giá trị kinh doanh thực sự.

