---
title : "Create Launch Template"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b>5.9.1. </b> "
---

Trong phần này, chúng ta sẽ tạo **Launch Template** cho ứng dụng. Launch Template lưu trữ toàn bộ cấu hình cần thiết để khởi tạo các Amazon EC2 instances trong Auto Scaling Group.

Launch Template sử dụng AMI phù hợp, IAM Instance Profile, Security Group và cấu hình root volume. Các EC2 instances được triển khai trong **private application subnets** và được quản trị thông qua **AWS Systems Manager Session Manager (SSM)**.

---

## Bước 1. Tạo Launch Template

Đăng nhập vào **AWS Management Console**.

Thực hiện các bước sau:

1. Mở dịch vụ **Amazon EC2**.
2. Chọn **Launch Templates**.
3. Chọn **Create launch template**.
4. Nhập tên Launch Template.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.9-lab7/5.9.1-open-amazon-ses.png" width="900">
</p>

<p align="center">
<i>Hình 5.9.1. Launch Template của ứng dụng.</i>
</p>

---

## Bước 2. Cấu hình Launch Template

Cấu hình Launch Template với các thông số sau:

| Thuộc tính | Giá trị |
|---|---|
| Launch Template | `delivery-ec2-lt` |
| Amazon Machine Image | AMI phù hợp |
| Instance Profile | `delivery-ec2-role` |
| Security Group | `delivery-ec2-sg` |
| Root Volume | Cấu hình theo yêu cầu |

Các EC2 instances sẽ được triển khai trong **private application subnets** và được quản trị thông qua **AWS Systems Manager Session Manager (SSM)** thay vì sử dụng SSH.

---

## Bước 3. Kiểm tra Launch Template

Sau khi tạo thành công:

- Kiểm tra Launch Template `delivery-ec2-lt`.
- Xác nhận IAM Instance Profile đã được gắn.
- Kiểm tra Security Group.
- Kiểm tra cấu hình Root Volume.
- Đảm bảo Launch Template sẵn sàng sử dụng cho Auto Scaling Group.

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Tạo thành công Launch Template `delivery-ec2-lt`.
- Cấu hình AMI cho EC2.
- Gắn IAM Instance Profile `delivery-ec2-role`.
- Cấu hình Security Group `delivery-ec2-sg`.
- Chuẩn bị Launch Template để triển khai EC2 trong Auto Scaling Group.