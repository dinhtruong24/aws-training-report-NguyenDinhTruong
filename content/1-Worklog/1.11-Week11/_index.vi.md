---
title: "Worklog Tuần 11"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu tuần 11:

* Tăng cường an ninh mạng bằng cách rà soát kiến trúc Amazon VPC và áp dụng chiến lược tường lửa phân lớp nhằm bảo vệ tối đa hạ tầng đám mây của doanh nghiệp.
* Nâng cao hiệu quả quản trị ngân sách và cơ chế tự động co giãn (Auto Scaling) thông qua việc tìm hiểu phương pháp phân bổ chi phí đa tài khoản, đồng thời thiết lập các chính sách mở rộng nâng cao dựa trên các chỉ số hiệu năng thực tế.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Thực hành cấu hình ủy quyền chéo tài khoản (Cross-Account Access) sử dụng cơ chế AWS STS Assume Role; thiết lập dịch vụ mã token an toàn (AWS Security Token Service) để cấp quyền cho các IAM Users và Roles từ tài khoản gốc (Management Account) truy cập tạm thời vào tài nguyên thuộc tài khoản Phát triển (Dev) và Sản xuất (Prod) mà không cần dùng đến các khóa truy cập dài hạn (Access Keys).  | 13/07/2026   | 13/07/2026      | https://000018.awsstudygroup.com/ |
| 3   | - Tiếp tục đào sâu thực hành giải pháp ủy quyền chéo tài khoản bằng AWS STS Assume Role; tối ưu hóa quy trình kiểm soát và thắt chặt cơ chế quản lý truy cập an toàn giữa hệ sinh thái gồm nhiều tài khoản AWS độc lập.                                   | 14/07/2026   | 14/07/2026      | https://000097.awsstudygroup.com/ |
| 4   | - Tối ưu hóa sơ đồ phân bổ chi phí trong môi trường đa tài khoản; phân tích chuyên sâu tính năng Hợp nhất hóa đơn (Consolidated Billing) của AWS Organizations, đánh giá lợi ích thực tế của mô hình quản trị đa tài khoản, đồng thời vận dụng công cụ AWS Cost Explorer kết hợp thẻ phân bổ chi phí (Cost Allocation Tags) để bóc tách, theo dõi ngân sách chi tiết theo từng phòng ban và dự án cụ thể. | 15/07/2026   | 15/07/2026      | https://000075.awsstudygroup.com/ |
| 5   | - Rà soát tổng thể kiến trúc mạng nội bộ Amazon VPC và cấu hình các lớp tường lửa nâng cao; phân tích sâu sơ đồ thiết lập các phân vùng mạng con (Subnets), bảng định tuyến (Route Tables), cổng kết nối Internet Gateway và NAT Gateway; thực hành cấu hình đồng bộ bộ lọc Security Groups cùng Network ACLs (NACLs) để thiết lập rào chắn bảo mật đa tầng.     | 16/07/2026   | 16/07/2026     | https://000019.awsstudygroup.com/ https://000074.awsstudygroup.com/ https://000111.awsstudygroup.com/ |
| 6   | - Triển khai hệ thống tự động co giãn nâng cao dựa trên mức độ tiêu thụ bộ nhớ (Memory Utilization); phối hợp cấu hình bộ cân bằng tải Application Load Balancer (ALB) cùng nhóm tự động co giãn Auto Scaling Group (ASG), sau đó tạo một chỉ số tùy chỉnh (custom metric) trên CloudWatch để kích hoạt tăng/giảm số lượng máy chủ EC2 theo dung lượng RAM thay vì dựa vào CPU như mặc định.    | 17/07/2026   | 17/07/2026      | https://000061.awsstudygroup.com/ https://000006.awsstudygroup.com/ |


### Kết quả đạt được tuần 11:

* Chuẩn hóa truy cập đa tài khoản an toàn: Triển khai thành công giải pháp Cross-Account thông qua AWS STS Assume Role, loại bỏ hoàn toàn rủi ro bảo mật từ việc sử dụng Access Keys dài hạn bằng cách áp dụng cơ chế cấp phát token tạm thời.

* Minh bạch hóa chi phí vận hành: Vận dụng thành thạo AWS Cost Explorer và hệ thống thẻ Cost Allocation Tags để thiết lập biểu đồ theo dõi tài chính trực quan cho từng dự án trong mô hình đa tài khoản.

* Tối ưu kiến trúc mạng & Tự động co giãn thông minh: Kiên cố hóa an ninh VPC với sự kết hợp chặt chẽ giữa Security Groups và NACLs, đồng thời cấu hình thành công luồng giám sát CloudWatch Custom Metric giúp Auto Scaling Group co giãn máy chủ EC2 chính xác theo lượng RAM tiêu thụ.

### Đánh giá tuần 11:
* Trong ngày Thứ Sáu, khi triển khai chỉ số tùy chỉnh CloudWatch (Custom Metric) để đo lượng RAM trên máy chủ EC2 nhằm kích hoạt Auto Scaling, hệ thống ASG ban đầu không nhận được dữ liệu chỉ số và không thể tự động co giãn. Đây là bài học thực tế đắt giá về cơ chế giám sát trên Cloud: mặc định AWS chỉ thu thập chỉ số phần cứng lớp ảo hóa (như CPU, Network), còn RAM thuộc về tài nguyên hệ điều hành bên trong (OS level). Tôi đã xử lý triệt để bằng cách cài đặt và phân quyền cho bộ chạy ngầm CloudWatch Agent (Unified CloudWatch Agent) trực tiếp trên hệ điều hành của máy chủ EC2 để đẩy dữ liệu Memory Utilization về CloudWatch một cách đều đặn, giúp chu trình Auto Scaling vận hành hoàn hảo.


