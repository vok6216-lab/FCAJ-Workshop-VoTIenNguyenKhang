---
title: "Event 2"
date: 2025-10-03
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

# Bài thu hoạch "AWS GenAI Builders Club"

### Mục Đích Của Sự Kiện

Sự kiện nhằm khám phá AI-driven development lifecycle (AI DLC) và giới thiệu các công cụ phát triển hiện đại được hỗ trợ bởi AI, tập trung vào cách AI đang biến đổi các thực hành phát triển phần mềm và cách các nhà phát triển có thể tích hợp AI hiệu quả vào quy trình làm việc của họ.

### Danh Sách Diễn Giả

1. **Toàn Huỳnh** - Senior Specialist SA (Solutions Architect)

   - Chủ đề: AI-driven Development Lifecycle

2. **My Nguyễn** - Senior Prototyping Architect

   - Chủ đề: Kiro - The AI IDE for Prototype to Production

### Nội Dung Nổi Bật

#### AI-Driven Development Lifecycle (bởi Toàn Huỳnh)

**Sự Tiến Hóa của AI trong Phát Triển Phần Mềm:**

- 2023: AI giúp các nhà phát triển viết code nhanh hơn

- 2024: AI tạo ra các đoạn code lớn hơn và trả lời nhanh hơn

- 2025: AI hoàn thành các nhiệm vụ phát triển từ đầu đến cuối với con người trong vòng lặp

**Nguyên Tắc Chính:**

- AI DLC không chỉ là một công cụ - đó là một phương pháp luận

- AI nên được sử dụng cho pair-programming, không phải là giải pháp độc lập

- Các nhà phát triển phải là chủ sở hữu và xác thực tất cả code do AI tạo ra

- Kiểm soát chất lượng là trách nhiệm của nhà phát triển

**Thách Thức với AI ở Quy Mô Lớn:**

- Vấn đề kiểm soát chất lượng khi tạo ra lượng code lớn

- Mất kiểm soát và hiểu biết về những gì AI đang làm

- Rủi ro phải khởi động lại dự án nếu chất lượng không được duy trì

- Sử dụng token quá mức trong các dự án lớn

**Quy Trình AI DLC:**

- AI không nên đưa ra quyết định độc lập - các nhà phát triển đưa ra tất cả quyết định

- Sử dụng AI để phân tích vấn đề, xem xét yêu cầu và tạo kế hoạch

- Lưu trữ kết quả trong các file Markdown để duy trì tính liên tục

- Chia nhỏ các dự án lớn thành các đơn vị nhỏ hơn

- Xem xét và xác thực thường xuyên là điều cần thiết

- Sử dụng AI cho các tác vụ tiêu chuẩn hóa, xử lý các tác vụ suy nghĩ thủ công

**Thực Hành Tốt Nhất:**

- Bắt đầu với các yêu cầu đơn giản và chia chúng thành các đơn vị

- Sử dụng AI để nhóm các đơn vị quan trọng cho người dùng cuối

- Triển khai mỗi đơn vị như một dự án nhỏ

- Duy trì một track chung cho sự hợp tác backend và frontend

- Đối với các dự án lớn, hãy cân nhắc sử dụng Amazon Q thay vì các công cụ AI đơn giản

#### Kiro - The AI IDE (bởi My Nguyễn)

**Tổng Quan:**

- Kiro là một IDE được hỗ trợ bởi AI được thiết kế cho phát triển từ prototype đến production

- Các điểm khác biệt chính giữa Kiro và VSCode đã được thảo luận

- Tập trung vào việc tối ưu hóa quy trình phát triển từ ý tưởng đến triển khai

**Tính Năng Quy Trình Chính:**

- **Role Separation**: Tiến trình Business → Architecture → Implementation

- **AI-Enhanced**: Mỗi vai trò có ngữ cảnh và khả năng AI chuyên biệt

- **Iterative**: Vòng lặp phản hồi trong mỗi giai đoạn

- **Template-Driven**: Đầu ra tiêu chuẩn hóa sử dụng các template AIDLC

**Agent Hooks:**

- Ủy thác nhiệm vụ cho các AI agent kích hoạt trên các sự kiện như 'file save'

- Các agent tự động thực thi trong nền dựa trên các prompt được định nghĩa trước của bạn

- Agent hooks giúp bạn mở rộng quy mô công việc bằng cách tạo tài liệu, unit test hoặc tối ưu hóa hiệu suất code

**Tối Đa Hóa Ngữ Nghĩa Mỗi Token:**

- AI không 'nghĩ bằng code' – nó lý luận bằng ý nghĩa

- Đừng dump 10K dòng source; Thay vào đó, cung cấp các mô hình trung gian giàu ngữ nghĩa

- Cắt bỏ các artefact (ví dụ: user stories, component models) để trở nên ngữ nghĩa rõ ràng; không có phần thừa!

- Nhớ tỷ lệ Tokens/Semantics

### Những Gì Học Được

1. **AI như một Đối Tác, Không Phải Thay Thế:**

   - Xem AI như một đối tác hợp tác trong giải quyết vấn đề

   - Duy trì giám sát và quyền quyết định của con người

   - Đảm bảo chất lượng vẫn là trách nhiệm của con người

2. **Quy Trình AI Có Cấu Trúc:**

   - Định nghĩa vai trò và trách nhiệm rõ ràng trong prompts

   - Sử dụng file Markdown để theo dõi tiến độ và duy trì ngữ cảnh

   - Chia nhỏ các dự án phức tạp thành các đơn vị có thể quản lý

   - Triển khai các chu kỳ xem xét thường xuyên

3. **Kiểm Soát Chất Lượng:**

   - Không bao giờ ủy thác hoàn toàn nhiệm vụ cho AI mà không xác thực

   - Xem xét code và kế hoạch do AI tạo ra thường xuyên

   - Xây dựng tài liệu (file Markdown) để tránh đi lệch hướng

   - Sử dụng AI cho các tác vụ tiêu chuẩn hóa, không phải tư duy phản biện

4. **Quản Lý Dự Án:**

   - Bắt đầu với các yêu cầu đơn giản và thu hẹp phạm vi

   - Sử dụng AI để nhóm các đơn vị quan trọng cho người dùng cuối

   - Xử lý mỗi đơn vị như một dự án nhỏ riêng biệt

   - Duy trì các kênh giao tiếp chung cho sự hợp tác nhóm

5. **Lựa Chọn Công Cụ:**

   - Đối với các dự án lớn, hãy cân nhắc các giải pháp doanh nghiệp như Amazon Q

   - Các công cụ AI đơn giản phù hợp cho các tác vụ nhỏ, được xác định rõ

   - Chọn công cụ dựa trên độ phức tạp và yêu cầu của dự án

### Ứng Dụng Vào Công Việc

1. **Triển Khai Phương Pháp Luận AI DLC:**

   - Áp dụng cách tiếp cận có cấu trúc cho phát triển được hỗ trợ bởi AI

   - Tạo tài liệu Markdown cho lập kế hoạch và theo dõi dự án

   - Thiết lập quy trình làm việc rõ ràng cho sự hợp tác AI

2. **Đảm Bảo Chất Lượng:**

   - Luôn xem xét và xác thực code do AI tạo ra

   - Triển khai các điểm kiểm tra thường xuyên trong quy trình phát triển

   - Duy trì quyền sở hữu tất cả các sản phẩm giao hàng

3. **Chia Nhỏ Dự Án:**

   - Chia các dự án lớn thành các đơn vị nhỏ, có thể quản lý

   - Sử dụng AI để giúp xác định và nhóm các thành phần quan trọng

   - Theo dõi tiến độ bằng cách sử dụng checkbox trong tài liệu lập kế hoạch

4. **Hợp Tác Nhóm:**

   - Thiết lập các track chung cho các nhóm backend và frontend

   - Sử dụng AI để tạo điều kiện giao tiếp và lập kế hoạch

   - Duy trì tài liệu rõ ràng cho sự liên kết nhóm

5. **Đánh Giá Công Cụ:**

   - Đánh giá công cụ AI dựa trên nhu cầu dự án

   - Cân nhắc các giải pháp doanh nghiệp cho các dự án quy mô lớn

   - Sử dụng công cụ phù hợp cho các giai đoạn phát triển khác nhau

### Trải nghiệm trong event

Sự kiện cung cấp những hiểu biết có giá trị về việc áp dụng thực tế của AI trong phát triển phần mềm. Các diễn giả nhấn mạnh tầm quan trọng của việc duy trì kiểm soát và giám sát của con người trong khi tận dụng khả năng của AI. Cuộc thảo luận về phương pháp luận AI DLC đặc biệt mang tính giáo dục, cho thấy cách cấu trúc sự hợp tác AI một cách hiệu quả.

Bài trình bày về Kiro đã cung cấp cái nhìn về các công cụ phát triển thế hệ tiếp theo tích hợp AI trực tiếp vào IDE, có khả năng tối ưu hóa quy trình phát triển từ prototype đến production.

Bài học chính được học là AI nên nâng cao khả năng của nhà phát triển thay vì thay thế các quy trình tư duy phản biện và ra quyết định. Tích hợp AI thành công đòi hỏi lập kế hoạch cẩn thận, xem xét thường xuyên và duy trì quyền sở hữu rõ ràng của quy trình phát triển.

#### Một số hình ảnh khi tham gia sự kiện

![Key Workflow Features](/images/4-EventParticipated/4.2-Event2/key-workflow-features.jpg)

![Agent Hooks](/images/4-EventParticipated/4.2-Event2/agent-hooks.jpg)

![Maximize Semantics per Token](/images/4-EventParticipated/4.2-Event2/maximize-semantics.jpg)

![AI-Driven Development Lifecycle](/images/4-EventParticipated/4.2-Event2/ai-dlc.jpg)

> Tổng thể, sự kiện không chỉ cung cấp kiến thức kỹ thuật mà còn giúp em thay đổi cách tư duy về AI-driven development lifecycle và cách tích hợp hiệu quả các công cụ AI vào quy trình phát triển trong khi duy trì chất lượng và kiểm soát.
