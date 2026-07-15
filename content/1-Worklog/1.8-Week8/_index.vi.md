---
title: "Worklog Tuần 8"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8:

* Làm chủ vòng đời kỹ nghệ dữ liệu bằng cách tiếp cận tiến trình tự động hóa ETL (Trích xuất, Biến đổi, Nạp) và xây dựng hệ thống thu thập log vận hành theo thời gian thực.
* Tiếp thu nguyên lý nền tảng để thiết kế mô hình Cloud Data Lake có khả năng co giãn cao, phục vụ cho việc lưu kho tập trung và phân tích chuyên sâu sau này.
* Khảo sát mảng AI/ML ứng dụng thông qua việc tích hợp các dịch vụ trí tuệ nhân tạo sẵn có của AWS vào ứng dụng mà không cần tự phát triển các mô hình học máy phức tạp.
### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Nghiên cứu chuyên sâu về dịch vụ AWS Data Pipeline và kiến trúc luồng ETL; tìm hiểu nguyên lý vận hành hệ thống, trực tiếp thiết kế một chu trình ETL tự động nhằm luân chuyển và định hình lại dữ liệu một cách an toàn giữa các nền tảng lưu trữ khác nhau.    | 22/06/2026   | 22/06/2026      | https://000113.awsstudygroup.com/ https://00012.awsstudygroup.com/ |
| 3   | - Hiện thực hóa hệ thống tiếp nhận log thời gian thực bằng Amazon Kinesis; khởi tạo cấu hình luồng Kinesis Data Streams, đồng thời viết một ứng dụng web mô phỏng để liên tục sản sinh log hệ thống, phục vụ cho bài toán truyền phát và xử lý sự kiện tức thời.    | 23/06/2026   | 23/06/2026      | https://000040.awsstudygroup.com/ https://000053.awsstudygroup.com/ |
| 4   | - Thiết lập cơ chế sao lưu tự động dữ liệu từ Amazon DynamoDB sang Amazon S3; ứng dụng bộ công cụ AWS Data Pipeline để lập lịch xuất dữ liệu định kỳ, bảo vệ an toàn cho các bảng DynamoDB và lưu trữ trên S3 nhằm sẵn sàng cho việc khôi phục sau thảm họa lẫn phân tích số liệu. | 24/06/2026   | 24/06/2026      | https://000060.awsstudygroup.com/ |
| 5   | - Khảo sát mô hình kiến trúc kho dữ liệu đám mây Cloud Data Lake; học cách xây dựng một Data Lake tập trung trên nền tảng Amazon S3, thực hành phân tách và tổ chức dữ liệu theo cấu trúc 3 lớp (Raw - Dữ liệu thô, Cleaned - Dữ liệu sạch, và Curated - Dữ liệu tinh chế) kết hợp quản lý siêu dữ liệu (Metadata).  | 25/06/2026   | 25/06/2026      | https://000035.awsstudygroup.com/ https://000070.awsstudygroup.com/ |
| 6   | - Tìm hiểu ứng dụng thị giác máy tính với Amazon Rekognition; nghiên cứu cách thức gọi các API tích hợp để nhận diện khuôn mặt, phân tích trạng thái cảm xúc, phát hiện vật thể xung quanh và trích xuất văn bản từ hình ảnh (công nghệ OCR).    | 26/06/2026   | 26/06/2026      | https://000135.awsstudygroup.com/ https://000066.awsstudygroup.com/ |


### Kết quả đạt được tuần 8:

* Tự động hóa luồng dữ liệu & ETL: Thiết lập thành công chu trình ETL tự động qua AWS Data Pipeline và xây dựng hoàn chỉnh hệ thống bắt log thời gian thực phối hợp giữa ứng dụng web mô phỏng và Kinesis Data Streams.

* Hoàn thiện mô hình lưu trữ Data Lake: Nắm vững tư duy tổ chức kho dữ liệu phân lớp trên Amazon S3, đồng thời cấu hình thành công hệ thống backup định kỳ tự động cho cơ sở dữ liệu NoSQL DynamoDB để đảm bảo an toàn thông tin.

* Tích hợp giải pháp AI thông minh: Làm chủ các API cốt lõi của Amazon Rekognition, hiện thực hóa khả năng phân tích hình ảnh nâng cao (nhận diện vật thể, đọc chữ OCR) giúp tối ưu hóa tính năng thông minh cho ứng dụng.

### Đánh giá tuần 8:
* Trong ngày Thứ Tư, khi cấu hình AWS Data Pipeline để xuất dữ liệu dung lượng lớn từ DynamoDB sang Amazon S3, hệ thống ban đầu đã tiêu thụ quá nhiều throughput (RCU) của bảng dữ liệu, làm ảnh hưởng đến tốc độ phản hồi chung của ứng dụng đang chạy. Đây là một bài học kinh nghiệm rất sâu sắc về việc quản lý băng thông cơ sở dữ liệu khi làm ETL. Tôi đã khắc phục bằng cách điều chỉnh lại tỷ lệ đọc dữ liệu (read throughput ratio) trong cấu hình thiết lập của Data Pipeline, giúp tiến trình backup diễn ra êm ái mà không gây nghẽn hệ sinh thái ứng dụng.


