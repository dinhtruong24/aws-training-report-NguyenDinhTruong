---
title : "Tạo Launch Template"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b>5.9.1. </b> "
---

Trong phần này, chúng ta sẽ tạo một **Launch Template** để định nghĩa cấu hình chuẩn cho các Amazon EC2 instances được triển khai trong Auto Scaling Group.

Launch Template giúp lưu trữ các thông tin như Amazon Machine Image (AMI), Instance Type, Key Pair, Security Group và các thiết lập mạng. Việc sử dụng Launch Template giúp triển khai các EC2 instances một cách nhất quán và đơn giản trong quá trình mở rộng hệ thống.

---

## Bước 1. Mở dịch vụ Amazon EC2

Đăng nhập vào **AWS Management Console**.

Thực hiện các bước sau:

1. Tìm kiếm **Amazon EC2**.
2. Chọn **EC2 Dashboard**.
3. Trong menu bên trái, chọn **Launch Templates**.
4. Chọn **Create launch template**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.9-lab7/5.9.1-create-launch-template.png" width="900">
</p>

<p align="center">
<i>Hình 5.9.2. Tạo Launch Template.</i>
</p>

---

## Bước 2. Cấu hình Launch Template

Trên trang **Create launch template**, thực hiện các bước sau:

1. Nhập **Launch Template Name**.
2. Chọn **Amazon Machine Image (AMI)**.
3. Chọn **Instance Type**.
4. Chọn **Key Pair**.
5. Chọn **Security Group**.
6. Cấu hình các tùy chọn khác nếu cần.
7. Chọn **Create launch template**.

Ví dụ:

```text
delivery-launch-template
```

---

## Bước 3. Kiểm tra Launch Template

Sau khi tạo thành công:

- Mở danh sách **Launch Templates**.
- Xác nhận Launch Template đã được tạo.
- Kiểm tra tên và cấu hình của Launch Template.
- Đảm bảo Launch Template sẵn sàng sử dụng cho Auto Scaling Group.

---

## Bảng cấu hình

| Thuộc tính | Giá trị |
|---|---|
| AWS Service | Amazon EC2 |
| Resource | Launch Template |
| Template Name | `delivery-launch-template` |
| Instance Type | t2.micro (ví dụ) |
| Status | Available |

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Truy cập dịch vụ Amazon EC2.
- Tạo thành công Launch Template.
- Cấu hình các thông số triển khai cho EC2.
- Chuẩn bị Launch Template để sử dụng trong Auto Scaling Group.

Tiếp theo, chúng ta sẽ thực hiện **5.9.2 – Tạo Target Group**.