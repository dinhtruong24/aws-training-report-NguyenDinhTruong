---
title : "Lab 7: Compute & Deployment"
date : 2024-01-01
weight : 9
chapter : false
pre : " <b>5.9. </b> "
---

Trong Lab này, chúng ta sẽ triển khai ứng dụng quản lý giao hàng trên **Amazon EC2** và cấu hình hạ tầng cần thiết để hỗ trợ cân bằng tải, khả năng mở rộng và triển khai ứng dụng ổn định.

Môi trường triển khai sử dụng **EC2 Launch Template**, **Target Group**, **Application Load Balancer** và **Auto Scaling Group**. Các EC2 instances chạy trong private application subnets và được quản trị thông qua **AWS Systems Manager Session Manager** thay vì truy cập SSH trực tiếp.

Lab này cũng giới thiệu quy trình triển khai phiên bản ứng dụng bằng **symbolic link (symlink)**. Cách triển khai này cho phép kích hoạt nhanh một phiên bản mới và hỗ trợ rollback về phiên bản trước khi xảy ra lỗi.

---

## Mục tiêu của Lab

Sau khi hoàn thành Lab này, bạn sẽ có thể:

- Tạo EC2 Launch Template cho ứng dụng.
- Cấu hình Target Group sử dụng HTTP trên cổng `5000`.
- Tạo Application Load Balancer dạng Internet-facing.
- Cấu hình Auto Scaling Group trong private application subnets.
- Triển khai gói ứng dụng từ Amazon S3.
- Chuyển phiên bản đang hoạt động bằng symbolic link.
- Kiểm tra trạng thái dịch vụ và HTTP health check.
- Rollback về phiên bản trước khi quá trình triển khai gặp lỗi.

---

## Kiến trúc triển khai

Luồng triển khai ứng dụng được tổ chức như sau:

```text
Internet
    │
    ▼
Application Load Balancer
    │
    ▼
Target Group
HTTP:5000
    │
    ▼
Auto Scaling Group
    │
    ▼
Amazon EC2 Instances
Private Application Subnets
    │
    ▼
delivery.service
/opt/delivery/current/WedNightFury
```

Application Load Balancer tiếp nhận yêu cầu từ người dùng và chuyển tiếp đến các EC2 instances đang ở trạng thái healthy trong Target Group.

Các EC2 instances được tạo từ Launch Template và được quản lý bởi Auto Scaling Group. Mỗi instance chạy ứng dụng thông qua systemd service có tên `delivery.service`.

---

## Thành phần chính

| Thành phần | Cấu hình khuyến nghị |
|---|---|
| Launch Template | AMI phù hợp, `delivery-ec2-role`, `delivery-ec2-sg` và cấu hình root volume |
| Target Group | HTTP cổng `5000`, health check `/` hoặc endpoint health riêng |
| Application Load Balancer | Internet-facing, đặt trong `public-a` và `public-b`, sử dụng `delivery-alb-sg` |
| Auto Scaling Group | Đặt trong `app-a` và `app-b`; minimum 1, desired 1, maximum theo ngân sách |
| EC2 Service | `delivery.service` |
| Application Executable | `/opt/delivery/current/WedNightFury` |
| Quản trị instance | AWS Systems Manager Session Manager |

---

## Nội dung của Lab

Lab 7 gồm bốn phần. Tên các mục trên website được giữ nguyên.

### 5.9.1 Create Launch Template

Trong phần này, chúng ta sẽ:

- Tạo Launch Template `delivery-ec2-lt`.
- Chọn Amazon Machine Image phù hợp.
- Gắn instance profile `delivery-ec2-role`.
- Cấu hình Security Group `delivery-ec2-sg`.
- Cấu hình root storage volume.
- Chuẩn bị EC2 instances để chạy trong private application subnets.

### 5.9.2 Create Target Group

Trong phần này, chúng ta sẽ:

- Tạo Target Group `delivery-app-tg`.
- Cấu hình HTTP trên cổng `5000`.
- Cấu hình application health check.
- Chuẩn bị Target Group để liên kết với Application Load Balancer.

### 5.9.3 Create Application Load Balancer

Trong phần này, chúng ta sẽ:

- Tạo Application Load Balancer `delivery-alb` dạng Internet-facing.
- Triển khai Load Balancer trong hai public subnets.
- Gắn Security Group `delivery-alb-sg`.
- Chuyển tiếp lưu lượng đến `delivery-app-tg`.
- Triển khai release mới từ Amazon S3 bằng symbolic link.

### 5.9.4 Create Auto Scaling Group

Trong phần này, chúng ta sẽ:

- Tạo Auto Scaling Group sử dụng `delivery-ec2-lt`.
- Triển khai EC2 instances trong `app-a` và `app-b`.
- Cấu hình minimum, desired và maximum capacity.
- Kiểm tra `delivery.service` và HTTP response của ứng dụng.
- Kiểm tra application logs.
- Rollback về phiên bản trước nếu release mới gặp lỗi.

---

## Quy trình triển khai release

Gói triển khai ứng dụng được tải từ Amazon S3 và giải nén vào một thư mục release riêng theo phiên bản.

Sau đó, symbolic link `/opt/delivery/current` được cập nhật để trỏ đến release mới trước khi khởi động lại `delivery.service`.

```text
Amazon S3 deployment package
             │
             ▼
/opt/delivery/packages/
             │
             ▼
/opt/delivery/releases/{RELEASE}
             │
             ▼
/opt/delivery/current
             │
             ▼
delivery.service
```

Khi release chỉ thay đổi S3, SQS, Amazon Location hoặc JavaScript mà không thay đổi database schema, không nên chạy migration không cần thiết.

---

## Health check và rollback

Sau khi triển khai, cần kiểm tra:

- Symbolic link `/opt/delivery/current` đang trỏ đến đúng release.
- `delivery.service` đang hoạt động.
- Endpoint local trên cổng `5000` trả về HTTP `200`.
- Application logs gần nhất không có lỗi triển khai.
- Target Group hiển thị EC2 instance ở trạng thái healthy.

Nếu release mới gặp lỗi, symbolic link có thể được chuyển lại về release trước và service được khởi động lại.

---

## Kết quả mong đợi

Sau khi hoàn thành Lab 7:

- EC2 Launch Template đã được cấu hình thành công.
- Target Group nhận lưu lượng ứng dụng trên cổng `5000`.
- Application Load Balancer chuyển tiếp yêu cầu đến các instance healthy.
- Auto Scaling Group quản lý các application instances trong private subnets.
- Ứng dụng chạy thông qua `delivery.service`.
- Có thể triển khai release mới bằng symlink.
- Có thể nhanh chóng rollback về release trước nếu quá trình triển khai thất bại.
- Hệ thống sẵn sàng cho bước kiểm thử end-to-end.