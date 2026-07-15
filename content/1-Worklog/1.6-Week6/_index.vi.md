---
title: "Worklog Tuần 6"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


### Mục tiêu tuần 6:

* Tinh gọn và thắt chặt an toàn cho ứng dụng đóng gói bằng việc nâng cao kỹ nghệ xử lý Docker Image và thiết lập các phân vùng mạng độc lập trên môi trường Production.
* Làm chủ các giải pháp quản lý container nâng cao thông qua tìm hiểu chuyên sâu về Kubernetes, Amazon EKS và phân tích chiến lược lựa chọn mô hình hạ tầng (ECS vs EKS) dựa trên bài toán kinh tế lẫn quy mô dự án.
* Hiện thực hóa mô hình DevOps thông qua việc làm quen với bộ công cụ phát triển chuyên dụng của AWS để thiết lập luồng phân phối tự động, hạn chế tối đa sai sót từ con người.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Triển khai tối ưu hóa Docker chuyên sâu; áp dụng giải pháp Multi-stage Build vào Dockerfile nhằm bóc tách môi trường đóng gói ứng dụng, lọc bỏ hoàn toàn các thư viện thừa giúp thu nhỏ tối đa dung lượng tệp tin Image.  | 08/06/2026   | 08/06/2026    | https://000015.awsstudygroup.com/ |
| 3   | - Thiết lập kiến trúc mạng và kiểm soát phân quyền trên Amazon ECS; kích hoạt cơ chế mạng awsvpc nhằm cấp phát card mạng ảo (ENI) và IP nội bộ riêng biệt cho từng Task, đồng thời áp dụng chính sách cấp quyền tối thiểu cho Task Roles. | 09/06/2026   | 09/06/2026      | https://000016.awsstudygroup.com/ https://000067.awsstudygroup.com/ https://000118.awsstudygroup.com/ https://000152.awsstudygroup.com/ |
| 4   | - Tiếp cận hệ sinh thái Kubernetes cùng dịch vụ Amazon EKS; phân tích mô hình hoạt động của các thành phần Control Plane, Worker Nodes, Pods và Services, đánh giá cách thức EKS tối giản hóa việc quản trị cụm máy chủ trên Cloud. | 10/06/2026   | 10/06/2026      | https://000126.awsstudygroup.com/ |
| 5   | - Thực hiện báo cáo đối sánh toàn diện giữa hai nền tảng Amazon ECS và Amazon EKS; lập bảng đánh giá chi tiết từ cấu trúc vận hành, tính năng đi kèm đến độ phức tạp quản trị nhằm tìm ra phương án tối ưu cho từng bài toán cụ thể của doanh nghiệp.    | 11/06/2026   | 11/06/2026      | https://000065.awsstudygroup.com/ https://000126.awsstudygroup.com/ |
| 6   | - Nghiên cứu quy trình tự động hóa với hệ sinh thái AWS Developer Tools; khảo sát mô hình phối hợp khép kín giữa AWS CodePipeline, CodeBuild và CodeDeploy từ bước tiếp nhận mã nguồn, kiểm thử tự động cho tới khi phát hành sản phẩm.  | 12/06/2026   | 12/06/2026      | https://000017.awsstudygroup.com/ https://000023.awsstudygroup.com/ https://000080.awsstudygroup.com/ https://000136.awsstudygroup.com/ https://000112.awsstudygroup.com/ |
| 7   | - Phát triển dự án Tập trung xây dựng và phát triển phần Backend cho dịch vụ cốt lõi của dự án.  | 13/06/2026   | 13/06/2026      | https://cloudjourney.awsstudygroup.com/ |

### Kết quả đạt được tuần 6:
* Hạ tầng Container gọn nhẹ & Bảo mật: Áp dụng thành công cơ chế Multi-stage Build giúp giảm dung lượng bộ nhớ lưu trữ cho Docker Image, đồng thời cô lập hoàn toàn luồng giao tiếp mạng của hệ thống Microservices nhờ cấu hình awsvpc trên ECS.

* Hoàn thiện tư duy điều phối hệ thống: Thấu suốt nguyên lý vận hành của Kubernetes và thiết lập thành công tài liệu phân tích chiến lược chọn lựa giữa ECS và EKS, tạo tiền đề vững chắc cho việc định hình cấu trúc hạ tầng lớn.

* Tự động hóa quy trình & Phát triển tính năng: Thiết lập sơ đồ vận hành luồng CI/CD tự động bằng các công cụ chuyên dụng của AWS và hoàn thành đúng tiến độ mã nguồn Backend cho phân hệ Tenant-service.

### Đánh giá tuần 5:
* Trong ngày Thứ Ba, khi triển khai chế độ mạng awsvpc trên cụm Amazon ECS, hệ thống đã gặp lỗi cạn kiệt địa chỉ IP khả dụng trong dải mạng con (Subnet IP) do tốc độ tự động mở rộng (Scale-out) các Task diễn ra quá nhanh. Đây là một bài học thực tiễn vô cùng giá trị về tầm quan trọng của việc quy hoạch dải mạng CIDR lúc ban đầu. Tôi đã xử lý triệt để vấn đề này bằng cách thiết kế và định tuyến lại một phân khu mạng con thứ cấp (Secondary Subnet) dành riêng cho các tác vụ ECS để đảm bảo hệ thống co giãn an toàn.

