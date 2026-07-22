---
title : "End-to-End Testing"
date : 2024-01-01
weight : 10
chapter : false
pre : " <b>5.10. </b> "
---

Sau khi hoàn thành tất cả các Lab trước, bước cuối cùng là thực hiện **End-to-End Testing** để xác minh toàn bộ hệ thống hoạt động chính xác.

Quá trình kiểm thử này giúp đảm bảo rằng tất cả các thành phần AWS đã được triển khai và cấu hình đúng cách, đồng thời ứng dụng có thể hoạt động ổn định từ đầu đến cuối.

---

## Mục tiêu

Sau khi hoàn thành phần này, bạn sẽ có thể:

- Kiểm tra kết nối giữa các dịch vụ AWS.
- Xác nhận Application Load Balancer hoạt động bình thường.
- Kiểm tra Auto Scaling Group và các EC2 instances.
- Kiểm tra truy cập ứng dụng từ Internet.
- Đảm bảo toàn bộ hệ thống hoạt động ổn định.

---

## Kiến trúc kiểm thử

```text
User
   │
   ▼
Application Load Balancer
   │
   ▼
Target Group
   │
   ▼
Amazon EC2 Instances
   │
   ▼
Application
```

Người dùng gửi yêu cầu đến Application Load Balancer. Sau đó Load Balancer sẽ chuyển tiếp yêu cầu đến các EC2 instances trong Target Group để xử lý.

---

## Các nội dung kiểm thử

Trong phần này sẽ thực hiện các bước sau:

- Kiểm tra Application Load Balancer.
- Kiểm tra Target Group Health Checks.
- Kiểm tra Auto Scaling Group.
- Truy cập ứng dụng thông qua DNS của Load Balancer.
- Xác nhận ứng dụng hoạt động bình thường.

---

## Tiêu chí thành công

Hệ thống được xem là triển khai thành công khi:

- Application Load Balancer có trạng thái **Active**.
- Target Group hiển thị tất cả EC2 instances ở trạng thái **Healthy**.
- Auto Scaling Group hoạt động bình thường.
- Ứng dụng có thể truy cập thông qua DNS của Load Balancer.
- Không phát sinh lỗi trong quá trình kiểm thử.

---

## Kết quả đạt được

Sau khi hoàn thành End-to-End Testing:

- Toàn bộ các dịch vụ AWS đã được tích hợp thành công.
- Ứng dụng hoạt động ổn định.
- Hệ thống đáp ứng yêu cầu về khả năng mở rộng và tính sẵn sàng cao.
- Workshop được hoàn thành thành công.