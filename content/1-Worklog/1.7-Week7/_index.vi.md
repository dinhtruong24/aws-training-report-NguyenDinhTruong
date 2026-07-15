---
title: "Worklog Tuần 7"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:

* Vận hành và tinh chỉnh chu kỳ CI/CD thực tế bằng việc tự động hóa toàn bộ tiến trình bàn giao phần mềm từ mã nguồn GitHub sang môi trường chạy Amazon ECS.
* Nâng cao tính ổn định và khả năng mở rộng của lớp cơ sở dữ liệu thông qua cấu hình các giải pháp dự phòng thảm họa cho Amazon RDS và tối ưu hóa chi phí vận hành cho Amazon DynamoDB.
* Khảo sát mảng phân tích dữ liệu lớn (Big Data) bằng việc tiếp cận phương pháp thu thập, xử lý và phân tích các luồng dữ liệu truyền phát trực tiếp (Real-time streaming) trên đám mây.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Thiết lập trục tự động hóa CI/CD khép kín; kết nối kho mã nguồn GitHub thông qua cơ chế Webhooks để tự động kích hoạt AWS CodeBuild đóng gói ứng dụng thành Docker Image, đẩy sản phẩm lên kho lưu trữ Amazon ECR và dùng AWS CodeDeploy để phát hành phiên bản mới lên Amazon ECS.  | 15/06/2026   | 15/06/2026      | https://000051.awsstudygroup.com/ https://000099.awsstudygroup.com/ https://000152.awsstudygroup.com/ |
| 3   | - Thực hiện kiểm thử tải và giám sát tiến trình CI/CD; đẩy các bản cập nhật mới lên GitHub để kích hoạt chuỗi triển khai tự động, theo dõi trực quan quá trình cập nhật cuốn chiếu (Rolling Update) nhằm xác minh hệ thống hoạt động liên tục không bị gián đoạn (Zero-downtime) và phân tích nhật ký để cải thiện hiệu năng build.   | 16/06/2026   | 16/06/2026      | https://000062.awsstudygroup.com/ https://000084.awsstudygroup.com/ https://000113.awsstudygroup.com/ |
| 4   | - Gia cố độ bền vững và hiệu năng cho Amazon RDS; triển khai cấu hình Multi-AZ giúp tự động chuyển vùng dự phòng khi có sự cố (Failover), đồng thời khởi tạo các bản sao chỉ đọc (Read Replicas) nhằm san sẻ tải truy xuất dữ liệu và nâng cao tốc độ phản hồi. | 17/06/2026   | 17/06/2026      | https://100000.awsstudygroup.com/ https://100001.awsstudygroup.com/ |
| 5   | - Tối ưu hiệu quả hoạt động của Amazon DynamoDB; nghiên cứu cơ chế thiết lập Chỉ mục thứ cấp toàn cục (Global Secondary Indexes - GSI), lựa chọn khóa phân vùng tối ưu để hạn chế tối đa việc tiêu hao tài nguyên RCU/WCU không cần thiết, giúp tiết kiệm chi phí vận hành DB.         | 18/06/2026   | 18/06/2026      | https://000039.awsstudygroup.com/ https://000078.awsstudygroup.com/ |
| 6   | - Tiếp cận giải pháp xử lý dữ liệu thời gian thực với Amazon Kinesis; phân tích mô hình kiến trúc của Kinesis Data Streams và Kinesis Data Firehose, thực hành cấu hình thu thập luồng nhật ký ứng dụng (App logs) lẫn hành vi người dùng, rồi đẩy luồng dữ liệu trực tiếp về các dịch vụ lưu trữ như Amazon S3 và Amazon OpenSearch.        | 19/06/2026   | 19/06/2026      | https://000035.awsstudygroup.com/ https://000070.awsstudygroup.com/ https://000072.awsstudygroup.com/ https://000105.awsstudygroup.com/ |


### Kết quả đạt được tuần 7:

* Tự động hóa luồng phân phối toàn diện: Xây dựng thành công đường ống CI/CD hoàn toàn tự động kích hoạt từ GitHub, đóng gói ứng dụng qua CodeBuild/ECR và phát hành không gián đoạn hệ thống lên cụm ECS Service.

* Nâng cấp sức mạnh hệ thống Database: Tối ưu hóa thành công khả năng chịu lỗi của hệ thống RDS nhờ cấu hình dự phòng Multi-AZ, giải phóng băng thông truy vấn bằng Read Replicas và tinh chỉnh chỉ mục GSI trên DynamoDB để cắt giảm tối đa chi phí tài nguyên tiêu thụ.

* Làm chủ quy trình phân tích luồng dữ liệu: Nắm vững cách thức thiết lập hạ tầng tiếp nhận dữ liệu thời gian thực thông qua Amazon Kinesis, tạo nền tảng vững chắc cho việc thu thập và phân tích dữ liệu lớn.

### Đánh giá tuần 7:
* Trong quá trình kiểm thử chuỗi CI/CD vào ngày Thứ Ba, khi thực hiện đẩy commit liên tục để kích hoạt cơ chế Rolling Update, hệ thống ECS thỉnh thoảng gặp tình trạng tắc nghẽn tài nguyên do các Task cũ chưa kịp giải phóng hoàn toàn trong khi Task mới đã được khởi tạo. Đây là bài học thực tế rất bổ ích về cấu hình vòng đời dịch vụ. Tôi đã xử lý triệt để bằng cách tinh chỉnh lại các tham số giới hạn tỷ lệ phần trăm tác vụ hoạt động tối thiểu và tối đa (minimumHealthyPercent và maximumPercent) trong ECS Service, giúp tiến trình cập nhật diễn ra mượt mà và duy trì tính sẵn sàng cao của ứng dụng.


