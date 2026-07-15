---
title: "Worklog Tuần 4"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

* Chuyển đổi tư duy thiết kế hệ thống từ kiến trúc nguyên khối sang kiến trúc Microservices và Serverless để cải thiện khả năng mở rộng và tính linh hoạt.

* Hiểu các nguyên tắc DevOps bằng cách học Tích hợp liên tục và Phân phối liên tục (CI/CD), tự động hóa cơ sở hạ tầng và các phương pháp phân phối phần mềm hiện đại.

* Tăng cường bảo mật dữ liệu và quản lý đặc quyền bằng cách sử dụng thành thạo các dịch vụ mã hóa, triển khai ranh giới quyền nghiêm ngặt và khám phá các giải pháp phát hiện mối đe dọa do AI cung cấp.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Nghiên cứu kiểm soát truy cập nâng cao bằng cách sử dụng Ranh giới quyền IAM (IAM Permission Boundaries); tìm hiểu cách Ranh giới quyền giới hạn quyền tối đa có thể được cấp cho Người dùng và Vai trò IAM, đồng thời đặt cấu hình chính sách để ngăn chặn leo thang đặc quyền bởi các quản trị viên được ủy quyền.   | 25/05/2026   | 25/05/2026     | https://000030.awsstudygroup.com/ |
| 3   | - Triển khai Amazon GuardDuty và thực hiện mô phỏng sự cố bảo mật; kích hoạt Amazon GuardDuty, mô phỏng các cuộc tấn công như nỗ lực vũ phu (brute-force) SSH, truy cập từ IP độc hại và quét cổng (port scanning), sau đó phân tích chi tiết các phát hiện bảo mật (findings) được tạo ra.    | 26/05/2026  | 26/05/2026     | https://000098.awsstudygroup.com/ |
| 4   | - Quản lý khóa mã hóa với AWS KMS và bảo mật dữ liệu lưu trữ; tạo khóa do khách hàng quản lý (CMK), cấu hình quản lý vòng đời khóa, xác định các chính sách khóa (key policies) và cho phép mã hóa tự động cho dữ liệu nhạy cảm được lưu trữ trong Amazon S3. | 27/05/2026   | 27/05/2026    | https://000033.awsstudygroup.com/ |
| 5   | - Nghiên cứu AWS Well-Architected Framework, tập trung sâu vào Trụ cột bảo mật (Security Pillar); tìm hiểu các nguyên tắc cốt lõi bao gồm quản lý danh tính, bảo vệ cơ sở hạ tầng, bảo vệ dữ liệu và các chiến lược ứng phó sự cố an ninh thông tin.  | 28/05/2026   | 28/05/2026    | https://000097.awsstudygroup.com/ |
| 6   | - Nghiên cứu các nguyên tắc cơ bản của kiến trúc Serverless; tìm hiểu cách hoạt động của hệ thống theo hướng sự kiện (event-driven) sử dụng AWS Lambda và Amazon API Gateway, tiến hành so sánh Serverless với các kiến trúc dựa trên EC2 truyền thống về các yếu tố như tối ưu hóa chi phí, mở rộng quy mô tự động và giới hạn khởi động nguội (cold start).   | 29/05/2026   | 29/05/2026    | https://000054.awsstudygroup.com/ https://000078.awsstudygroup.com/ https://000079.awsstudygroup.com/ https://000082.awsstudygroup.com/ https://000084.awsstudygroup.com/ https://000085.awsstudygroup.com/ |


### Kết quả đạt được tuần 4:

* Kiểm soát đặc quyền & Phát hiện đe dọa: Thiết lập thành công ranh giới quyền IAM Permission Boundaries giúp ngăn ngừa leo thang đặc quyền, đồng thời ứng dụng Amazon GuardDuty để phát hiện và cảnh báo thông minh các hành vi tấn công giả lập.

* Bảo mật dữ liệu tối ưu: Làm chủ dịch vụ AWS KMS thông qua việc tự khởi tạo, quản lý vòng đời khóa CMK và áp dụng mã hóa dữ liệu tự động ngay khi lưu trữ trên các bucket Amazon S3.

* Tiếp cận tư duy Serverless chuẩn hóa: Nắm vững lý thuyết thiết kế hệ thống Event-driven với AWS Lambda và API Gateway, đồng thời thấu suốt các tiêu chuẩn bảo mật hệ thống theo Khung kiến trúc tối ưu AWS Well-Architected.

### Đánh giá tuần 4:
* Trong quá trình mô phỏng sự cố bảo mật để kiểm thử Amazon GuardDuty, ban đầu tôi gặp khó khăn khi thiết lập các công cụ giả lập tấn công (như quét cổng và brute-force) từ môi trường ngoài vào hệ thống do các lớp bảo mật bảo vệ sẵn có. Sau khi cấu hình tạm thời một môi trường thử nghiệm độc lập (sandbox) và điều chỉnh lại Security Groups, GuardDuty đã ghi nhận và phân tích chính xác các mối đe dọa. Điều này giúp tôi hiểu sâu sắc cách thức hoạt động thực tế của một hệ thống giám sát an ninh thông tin chủ động.


