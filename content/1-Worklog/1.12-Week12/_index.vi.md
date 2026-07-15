---
title: "Worklog Tuần 12"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.12 </b> "
---

### Mục tiêu tuần 12:

* Tăng cường cơ chế quản trị đặc quyền IAM bằng cách xây dựng các chính sách phân quyền dựa trên định dạng JSON và áp dụng các điều kiện ràng buộc nâng cao (Policy Conditions).
* Thiết lập tài liệu tổng hợp các dòng lệnh AWS CLI cốt lõi (Cheat Sheet) nhằm tăng tốc độ xử lý và nâng cao hiệu suất thực hiện các tác vụ quản trị đám mây hàng ngày.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tối ưu hóa chi phí lưu trữ thông qua cấu hình quy trình Amazon S3 Lifecycle và tích hợp S3 Glacier; thiết lập các quy tắc vòng đời để tự động chuyển dịch các đối tượng dữ liệu ít khi truy cập sang các lớp lưu trữ lưu trữ Glacier, đồng thời cài đặt chính sách hết hạn (expiration) nhằm giảm thiểu chi phí phát sinh dài hạn.  | 20/07/2026   | 20/07/2026      | https://000078.awsstudygroup.com/ |
| 3   | - Tiếp tục đào sâu thực hành quản lý vòng đời dữ liệu trên Amazon S3 và cấu hình S3 Glacier; tiến hành rà soát kỹ lưỡng các chu trình chuyển đổi lớp dữ liệu (lifecycle transitions), phân loại kỹ các nhóm lưu trữ (storage classes) và kiểm thử các quy tắc hủy bỏ đối tượng cũ để hoàn thiện bài toán tiết kiệm tài nguyên.    | 21/07/2026   | 21/07/2026      | https://000069.awsstudygroup.com/ https://000111.awsstudygroup.com/ |
| 4   | - Xây dựng cẩm nang tra cứu nhanh AWS CLI (Cheat Sheet) tổng hợp toàn bộ các dòng lệnh thực thi thông dụng cho Amazon EC2, Amazon S3, IAM, Amazon RDS và Amazon CloudWatch; trực tiếp thực hành nâng cao các cú pháp sàng lọc dữ liệu như --query, bộ lọc --filter, và định cấu hình định dạng đầu ra linh hoạt dưới dạng bảng hoặc tệp JSON. | 22/07/2026   | 22/07/2026      | https://000011.awsstudygroup.com/ |
| 5   | - Nghiên cứu Trụ cột Bảo mật (Security Pillar) thuộc bộ khung chuẩn kiến trúc AWS Well-Architected Framework; tập trung phân tích các mô hình quản lý định danh tối ưu, các phương thức bảo vệ toàn vẹn dữ liệu và các quy trình chuẩn để ứng phó hiệu quả khi xảy ra sự cố an ninh hệ thống.   | 23/07/2026   | 23/07/2026      | https://000141.awsstudygroup.com/ |
| 6   | - Tìm hiểu Trụ cột Vận hành Xuất sắc (Operational Excellence Pillar) trong kiến trúc AWS Well-Architected Framework; tập trung làm rõ phương pháp tự động hóa quy trình, thiết lập hệ thống giám sát hoạt động thời gian thực và áp dụng các thói quen cải tiến hạ tầng liên tục.      | 24/07/2026   | 24/07/2026      | https://000098.awsstudygroup.com/ |


### Kết quả đạt được tuần 12:

* Tự động hóa chu kỳ lưu trữ: Triển khai thành công các chính sách S3 Lifecycle giúp phân tầng dữ liệu thông minh sang S3 Glacier, cắt giảm tối đa chi phí lưu trữ tệp tin cũ.

* Làm chủ công cụ quản trị CLI: Đóng gói hoàn chỉnh tài liệu AWS CLI Cheat Sheet cá nhân, thành thạo kỹ năng truy vấn dữ liệu phức tạp từ dòng lệnh bằng các tham số lọc cấu trúc cao như --query và --filter.

* Chuẩn hóa tư duy thiết kế hệ thống đám mây: Thấu suốt toàn bộ lý thuyết và thực tiễn cốt lõi của hai trụ cột Bảo mật và Vận hành Xuất sắc theo tiêu chuẩn AWS toàn cầu, sẵn sàng ứng dụng để chuẩn hóa hạ tầng hệ thống thực tế.

### Đánh giá tuần 12:
* Trong ngày Thứ Tư, khi xây dựng tài liệu AWS CLI Cheat Sheet và chạy các lệnh truy vấn phức tạp trên Amazon EC2 với lượng dữ liệu trả về rất lớn, câu lệnh sử dụng bộ lọc mặc định chạy rất chậm và định dạng JSON đổ ra thiết bị đầu cuối (Terminal) bị rối mắt, cực kỳ khó đọc. Đây là một bài học kinh nghiệm rất hay về việc tối ưu hóa giao diện dòng lệnh khi vận hành Cloud. Tôi đã khắc phục triệt để bằng cách kết hợp lồng ghép tham số --query để chỉ trích xuất đúng các trường thông tin cần thiết (như InstanceId, State), đồng thời định hướng định dạng đầu ra thành --output table để dữ liệu hiển thị trực quan theo dạng bảng, giúp việc kiểm tra thông số hệ thống nhanh chóng và chính xác hơn nhiều.


