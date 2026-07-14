---
title: "Worklog Tuần 5"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


### Mục tiêu tuần 5:

* Làm chủ các công nghệ Cloud-Native và Serverless bằng cách xây dựng và cấu hình các ứng dụng không máy chủ, giảm thiểu chi phí quản lý hạ tầng và tối ưu hóa chi phí vận hành.

* Tìm hiểu kiến trúc hệ thống hiện đại thông qua việc nghiên cứu cách phân rã ứng dụng và chuyển đổi từ kiến trúc nguyên khối (Monolithic) sang kiến trúc vi dịch vụ (Microservices) linh hoạt.

* Phát triển tư duy DevOps bằng cách thấu suốt các nguyên lý nền tảng của Tích hợp liên tục và Triển khai liên tục (CI/CD), đặt nền móng cho việc tự động hóa đường ống phân phối phần mềm từ môi trường phát triển đến vận hành thực tế (Production).

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Xây dựng logic backend bằng AWS Lambda; phát triển, tối ưu hóa và cấu hình các hàm AWS Lambda để xử lý dữ liệu backend, thực hành cấu hình IAM Roles, phân bổ bộ nhớ (Memory Allocation), thiết lập thời gian chờ (Timeout) và quản lý an toàn các biến môi trường (Environment Variables).  | 01/06/2026   | 01/06/2026      | https://0000130.awsstudygroup.com/ https://000022.awsstudygroup.com/ |
| 3   | - Tích hợp Amazon API Gateway và hoàn thiện quy trình làm việc Serverless; triển khai Amazon API Gateway (HTTP/REST API) đóng vai trò là điểm tiếp nhận yêu cầu đầu vào (entry point), cấu hình định tuyến (routing) và tích hợp trực tiếp với AWS Lambda để xây dựng ứng dụng không máy chủ an toàn, hoàn chỉnh từ đầu đến cuối.   | 02/06/2026   | 02/06/2026    | https://000135.awsstudygroup.com/ |
| 4   | - Nghiên cứu kiến trúc vi dịch vụ Microservices; tìm hiểu phương pháp phân rã một ứng dụng Monolithic thành các dịch vụ độc lập dựa trên các nguyên tắc Bounded Context, đồng thời phân tích các mô hình giao tiếp sử dụng giao thức đồng bộ (REST, gRPC) và truyền thông điệp bất đồng bộ qua các Event Broker. | 03/06/2026   | 03/06/2026    | https://000050.awsstudygroup.com/ https://000052.awsstudygroup.com/ |
| 5   | - Nghiên cứu các nguyên lý nền tảng của đường ống CI/CD; tìm hiểu các khái niệm Tích hợp liên tục (CI) và Triển khai liên tục (CD), phân tích các giai đoạn tiêu chuẩn của một đường ống (Source $\rightarrow$ Build $\rightarrow$ Test $\rightarrow$ Deploy) và các chiến lược triển khai phổ biến như Blue-Green Deployment và Canary Deployment.  | 04/06/2026   | 04/06/2026      | https://000017.awsstudygroup.com/ https://000051.awsstudygroup.com/ https://000084.awsstudygroup.com/ https://000133.awsstudygroup.com/ |
| 6   | - Tối ưu hóa bài thực hành Serverless và đánh giá hiệu năng thực tế; hoàn thiện ứng dụng Serverless mẫu, thực hiện kiểm thử tải (load testing), đánh giá độ trễ của Lambda, hành vi khởi động nguội (Cold Start) và khả năng tự động co giãn dưới khối lượng công việc ngày càng tăng.  | 05/06/2026  | 05/06/2026     | https://000078.awsstudygroup.com/ |


### Kết quả đạt được tuần 5:

* Xây dựng ứng dụng Serverless hoàn chỉnh: Phát triển thành công hệ thống Backend không máy chủ bằng cách kết nối mượt mà Amazon API Gateway với các hàm AWS Lambda được cấu hình tối ưu về bộ nhớ, bảo mật và thời gian chờ.

* Thấu suốt tư duy kiến trúc hiện đại: Nắm vững phương pháp phân rã ứng dụng Monolithic sang Microservices theo nguyên tắc Bounded Context, phân biệt rõ các cơ chế giao tiếp đồng bộ (REST/gRPC) và bất đồng bộ qua Event Broker.

* Làm chủ quy trình DevOps & CI/CD: Hiểu rõ sơ đồ vận hành của một đường ống CI/CD tiêu chuẩn và các chiến lược phát hành giảm thiểu rủi ro (Canary, Blue-Green), đồng thời tối ưu hóa thành công hiệu năng ứng dụng Serverless thông qua việc đo lường, xử lý hiện tượng Cold Start.

### Đánh giá tuần 5:
* Trong quá trình thực hiện kiểm thử tải (load testing) cho ứng dụng Serverless vào ngày thứ Sáu, tôi đã trực tiếp quan sát thấy hiện tượng độ trễ tăng cao đột ngột khi xảy ra hành vi khởi động nguội (Cold Start) của các hàm AWS Lambda mới được khởi tạo. Để khắc phục và tối ưu hóa hiệu năng, tôi đã nghiên cứu áp dụng giải pháp cấu hình Provisioned Concurrency cho các tài nguyên quan trọng cần phản hồi nhanh. Bài học thực tế này giúp tôi hiểu sâu sắc cách cân bằng giữa chi phí vận hành và hiệu năng phản hồi của kiến trúc Serverless.

