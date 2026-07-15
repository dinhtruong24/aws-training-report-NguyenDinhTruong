---
title: "Worklog Tuần 10"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


### Mục tiêu tuần 10:

* Hoạch định mô hình kiến trúc cho đồ án cá nhân cuối khóa bằng cách xác định giải pháp thiết kế tổng thể và lựa chọn các dịch vụ AI/ML phù hợp để giải quyết một bài toán thực tế.
* Nghiên cứu chiến lược quản trị nhiều tài khoản cấp doanh nghiệp (Enterprise Multi-Account Strategy) và thấu suốt vai trò của việc cô lập tài nguyên trong các hệ thống Cloud quy mô lớn.
* Triển khai hệ thống bảo mật và quản trị tập trung thông qua việc kiểm soát quyền hạn tối ưu, hợp nhất hóa đơn thanh toán (Consolidated Billing) và thiết lập truy cập an toàn liên kết giữa nhiều tài khoản AWS khác nhau.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Phác thảo sơ đồ kiến trúc tổng quan và xây dựng kế hoạch tích hợp các dịch vụ AI chuyên biệt cho đồ án cá nhân cuối khóa.   | 06/07/2026   | 06/07/2026      | https://cloudjourney.awsstudygroup.com/ |
| 3   | - Nghiên cứu chiến lược quản lý đa tài khoản trong doanh nghiệp; phân tích chi tiết các rủi ro về mặt an ninh và vận hành khi gộp chung mọi thứ vào một tài khoản AWS duy nhất (như phạm vi ảnh hưởng khi gặp sự cố - blast radius, rào cản trong quản lý chi phí, và xung đột tài nguyên); tìm hiểu mô hình kiến trúc AWS Landing Zone.   | 07/07/2026   | 07/07/2026      | https://000002.awsstudygroup.com/ https://000030.awsstudygroup.com/ https://000031.awsstudygroup.com/ |
| 4   | - Xây dựng và thiết lập hệ thống AWS Organization; khởi tạo tổ chức từ Tài khoản Quản trị chính (Management Account), gửi lời mời liên kết đến các tài khoản thành viên (member accounts) và cấu hình tính năng Hợp nhất hóa đơn (Consolidated Billing) để quản lý tài chính tập trung. | 08/07/2026   | 08/07/2026      | https://000027.awsstudygroup.com/ |
| 5   | - Khởi tạo các Đơn vị Tổ chức (Organizational Units - OUs) và cấu hình Chính sách Kiểm soát Dịch vụ (Service Control Policies - SCPs); phân nhóm các tài khoản vào các phân vùng môi trường riêng biệt bao gồm Dev, Test, Production và Security, sau đó áp dụng các quy tắc SCPs nhằm giới hạn việc sử dụng các dịch vụ đắt đỏ hoặc khóa các vùng địa lý (Regions) không được phép hoạt động.    | 09/07/2026   | 09/07/2026     | https://000064.awsstudygroup.com/ https://000010.awsstudygroup.com/ |
| 6   | - Cấu hình dịch vụ quản lý định danh AWS IAM Identity Center; thiết lập các bộ phân quyền (Permission Sets) và triển khai giải pháp truy cập chéo tài khoản (Cross-Account Access) nhằm cho phép các kỹ sư đăng nhập và làm việc an toàn trên nhiều tài khoản đích từ một cổng xác thực duy nhất.   | 10/07/2026  | 10/07/2026      | https://000096.awsstudygroup.com/ |
| 7   | - Hoàn thiện tài liệu kỹ thuật cho Blog 3; đồng thời trực tiếp triển khai hạ tầng container không máy chủ AWS ECS Fargate phục vụ cho dự án cá nhân cuối khóa.          | 11/07/2026   | 11/07/2026     | https://cloudjourney.awsstudygroup.com/ |

### Kết quả đạt được tuần 10:

* Hoạch định dự án & Triển khai hạ tầng: Thiết lập thành công bản vẽ kiến trúc kết hợp AI cho đồ án tốt nghiệp, hoàn thành nội dung bài Blog 3 và trực tiếp cấu hình chạy thực tế hệ thống container trên AWS ECS Fargate.

* Kiến trúc hóa hệ thống tài khoản doanh nghiệp: Xây dựng thành công cấu trúc AWS Organizations hoàn chỉnh, liên kết các tài khoản thành viên về tài khoản gốc để tập trung quản lý dòng tiền (Consolidated Billing).

* Thắt chặt an ninh & Phân quyền tập trung: Thiết kế thành công các phân vùng OUs (Dev, Test, Prod, Security), kiểm soát chặt chẽ giới hạn chi phí và địa lý bằng các bộ lọc chính sách SCPs, đồng thời cấu hình AWS IAM Identity Center giúp đơn giản hóa quy trình đăng nhập một lần (SSO) chéo tài khoản.

### Đánh giá tuần 10:
* Trong ngày Thứ Năm, sau khi áp dụng chính sách SCPs (Service Control Policies) lên Đơn vị Tổ chức (OU) dành cho môi trường Dev để chặn các dịch vụ đắt tiền, một số dịch vụ nền tảng dùng chung hỗ trợ cho quá trình CI/CD đột ngột bị gián đoạn và báo lỗi từ chối quyền truy cập (Access Denied). Đây là bài học thực tiễn giá trị về việc kiểm soát quyền lực của SCPs vì nó có tính chất phủ quyết mọi quyền IAM thông thường. Tôi đã khắc phục bằng cách phân tích kỹ log lỗi từ CloudTrail, tinh chỉnh lại các điều kiện loại trừ (Conditions) trong tệp chính sách JSON của SCP để chỉ chặn các dòng tài nguyên đắt đỏ thực sự mà không gây ảnh hưởng đến các tác vụ tự động hóa thiết yếu của lập trình viên.

