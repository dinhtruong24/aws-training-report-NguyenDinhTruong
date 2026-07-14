---
title: "Worklog Tuần 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


### Mục tiêu tuần 3:

* Tăng cường an ninh hệ thống toàn diện (End-to-End) bằng cách triển khai các giải pháp bảo mật đa lớp, từ quản lý định danh truy cập đến bảo vệ lớp ứng dụng.
* Nâng cao năng lực quản trị rủi ro và chủ động phát hiện mối đe dọa thông qua việc cấu hình tường lửa, đánh giá tuân thủ bảo mật và thiết lập các quy tắc tự động hóa nhằm phát hiện, ngăn chặn truy cập trái phép.
* Bảo mật dữ liệu nhạy cảm bằng mã hóa và tối ưu hóa quy trình triển khai ứng dụng bằng cách chuẩn hóa các tác vụ container quy mô lớn.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Triển khai kiến trúc container quy mô lớn bằng Amazon ECS; khởi tạo và cấu hình một Amazon ECS Cluster, định nghĩa các Task Definition tiêu chuẩn và triển khai một dịch vụ ECS (ECS Service) tích hợp với Application Load Balancer (ALB) để đảm bảo tính sẵn sàng cao.  | 18/05/2026   | 18/05/2026      | https://000016.awsstudygroup.com/ https://0000118.awsstudygroup.com/ |
| 3   | - Tích hợp hệ thống giám sát tập trung với Amazon CloudWatch; cấu hình thu thập log và chỉ số hiệu năng (metrics) từ Amazon ECS, thiết kế CloudWatch Dashboards trực quan hóa hiệu suất hệ thống và thiết lập CloudWatch Alarms gửi cảnh báo qua Email hoặc Slack khi mức sử dụng CPU/Memory vượt ngưỡng chỉ định.  | 19/05/2026   | 19/05/2026      | https://000008.awsstudygroup.com/ |
| 4   | - Chuẩn hóa quản lý định danh với AWS IAM Identity Center (SSO); cấu hình dịch vụ AWS Single Sign-On tập trung, khởi tạo các bộ phân quyền (Permission Sets) và quản trị quyền truy cập của người dùng trên các môi trường Phát triển (Development), Thử nghiệm (Staging) và Vận hành (Production). | 20/05/2026   | 20/05/2026      | https://000028.awsstudygroup.com/ https://000031.awsstudygroup.com/ https://000044.awsstudygroup.com/ https://000058.awsstudygroup.com/ |
| 5   | - Kích hoạt AWS Security Hub và thực hiện đánh giá mức độ tuân thủ an ninh; cấu hình AWS Security Hub để quét bảo mật tự động và đánh giá sự tuân thủ dựa trên tiêu chuẩn CIS AWS Foundations Benchmark nhằm phát hiện các cấu hình sai sót về bảo mật. | 21/05/2026   | 21/05/2026      | https://000018.awsstudygroup.com/ https://000069.awsstudygroup.com/ |
| 6   | - Cấu hình tường lửa ứng dụng web AWS WAF để bảo vệ ứng dụng; liên kết AWS WAF với Application Load Balancer, tạo các Web ACL và thiết lập các quy tắc bảo mật nhằm phát hiện và ngăn chặn các kiểu tấn công phổ biến như SQL Injection (SQLi), Cross-Site Scripting (XSS) và các lưu lượng truy cập bot độc hại.  | 22/05/2026   | 22/05/2026      | https://000026.awsstudygroup.com/ |


### Kết quả đạt được tuần 3:

* Vận hành hệ thống Container chuẩn hóa: Triển khai thành công ứng dụng trên cụm Amazon ECS tích hợp bộ cân bằng tải ALB, tối ưu hóa quy trình phân tải và đảm bảo khả năng chịu lỗi cao của dịch vụ.

* Thiết lập giám sát tự động chặt chẽ: Xây dựng hệ thống bảng điều khiển trung tâm và các cảnh báo tự động thông qua Amazon CloudWatch, giúp chủ động nắm bắt trạng thái tài nguyên và hiệu năng của cụm ECS.

* Bảo mật đa lớp toàn diện: Hoàn thành cấu hình Single Sign-On (SSO) để quản trị truy cập tập trung, tối ưu hóa điểm số an toàn hệ thống với AWS Security Hub theo chuẩn CIS, và dựng lá chắn bảo mật vững chắc cho ứng dụng web bằng AWS WAF.

### Đánh giá tuần 3:
* Trong quá trình liên kết AWS WAF với Application Load Balancer, tôi từng gặp khó khăn khi thiết lập các quy tắc chặn bot và lọc SQL Injection quá nghiêm ngặt, dẫn đến việc vô tình chặn cả một số yêu cầu (request) hợp lệ từ phía ứng dụng khách (false positive). Sau khi tiến hành phân tích log truy cập trên CloudWatch và tinh chỉnh lại các chính sách loại trừ (exclusion rules) trong Web ACL, hệ thống tường lửa đã hoạt động ổn định, bảo vệ tốt ứng dụng mà không gây ảnh hưởng đến trải nghiệm người dùng thực tế.


