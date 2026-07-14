---
title: "Worklog Tuần 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


### Mục tiêu tuần 2:

* Làm quen và thực hành cấu hình các dịch vụ cơ sở dữ liệu quan hệ (Amazon RDS) và phi quan hệ (Amazon DynamoDB) trên AWS.
* Triển khai ứng dụng web đơn giản lên Amazon Lightsail và cấu hình hệ thống có khả năng tự động co giãn, cân bằng tải (Auto Scaling Group & Elastic Load Balancer).
* Tiếp cận công nghệ container, thực hành viết Dockerfile để đóng gói ứng dụng và chạy thử nghiệm trên máy chủ ảo Amazon EC2.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Cài đặt và cấu hình AWS CLI trên máy tính cá nhân bằng Access Key/Secret Access Key, thực hành các lệnh CLI cơ bản để quản lý các tài nguyên EC2, S3, và Key Pair.  | 11/05/2026   | 11/05/2026      | https://000011.awsstudygroup.com/ |
| 3   | - Nghiên cứu dịch vụ cơ sở dữ liệu quản lý Amazon RDS (MySQL), cấu hình Nhóm bảo mật, Điểm cuối (Endpoint) và kết nối thành công từ ứng dụng phụ trợ để truy vấn dữ liệu. | 12/05/2026   | 12/05/2026      | https://000005.awsstudygroup.com/ |
| 4   | - Tìm hiểu cơ sở dữ liệu NoSQL Amazon DynamoDB, thiết kế lược đồ bảng với Phím phân vùng (Partition Key) / Khóa sắp xếp (Sort Key) và thực hiện các thao tác CRUD dữ liệu cơ bản. | 13/05/2026   | 13/05/2026      | https://000060.awsstudygroup.com/ https://000039.awsstudygroup.com/ https://0000133.awsstudygroup.com/ |
| 5   | - Khám phá Amazon Lightsail, thực hiện triển khai nhanh một phiên bản WordPress, cấu hình DNS cơ bản và so sánh hiệu quả giữa Lightsail và EC2 cho các ứng dụng nhỏ. | 14/05/2026   | 114/05/2026      | https://000045.awsstudygroup.com/ https://000046.awsstudygroup.com/ |
| 6   | - Nghiên cứu kiến trúc mở rộng và tính khả dụng cao bằng cách cấu hình Launch Template, Nhóm Auto Scaling (chính sách Scale In/Scale Out theo CPU) tích hợp với Elastic Load Balancer (ELB). | 15/05/2026   | 15/05/2026      | https://000006.awsstudygroup.com/ |


### Kết quả đạt được tuần 2:

* Quản trị hệ thống linh hoạt: Cấu hình thành công AWS CLI trên máy tính cá nhân, thực hiện trơn tru các lệnh quản trị tài nguyên trực tiếp bằng dòng lệnh thay vì giao diện Console.

* Làm chủ hai mô hình cơ sở dữ liệu: Triển khai và kết nối thành công cơ sở dữ liệu quan hệ Amazon RDS (MySQL) và phi quan hệ Amazon DynamoDB, thực hiện mượt mà các truy vấn và thao tác CRUD dữ liệu.

* Tối ưu hóa khả năng co giãn: Triển khai nhanh website WordPress trên Amazon Lightsail và xây dựng thành công hệ thống tự động co giãn Auto Scaling Group kết hợp Load Balancer giúp tối ưu hóa hiệu năng hệ thống dưới khối lượng công việc giả lập.

### Đánh giá tuần 2:
* Trong quá trình cấu hình kiểm tra quy mô tự động (Auto Scaling) kết hợp Elastic Load Balancer, tôi từng gặp khó khăn khi thiết lập các ngưỡng kích hoạt chính sách Scale Out và Scale In dựa trên CPU, dẫn đến việc hệ thống phản hồi co giãn chưa thực sự tối ưu trong lần kiểm thử đầu tiên. Sau khi hiệu chỉnh lại thông số thời gian chờ (cooldown period) và ngưỡng CPU, hệ thống đã tự động tăng giảm số lượng máy chủ chính xác theo đúng kịch bản tải thực tế.

