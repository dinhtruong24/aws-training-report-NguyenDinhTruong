---
title : "Tạo Application Load Balancer"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b>5.9.3. </b> "
---

Trong phần này, chúng ta sẽ tạo một **Application Load Balancer (ALB)** để phân phối lưu lượng truy cập đến các Amazon EC2 instances thông qua Target Group.

Application Load Balancer là dịch vụ cân bằng tải ở tầng ứng dụng (Layer 7), có khả năng định tuyến các yêu cầu HTTP và HTTPS đến các tài nguyên phù hợp. Kết hợp với Target Group và Auto Scaling Group, ALB giúp tăng tính sẵn sàng và khả năng mở rộng của hệ thống.

---

## Bước 1. Mở Application Load Balancers

Đăng nhập vào **AWS Management Console**.

Thực hiện các bước sau:

1. Mở dịch vụ **Amazon EC2**.
2. Trong menu bên trái, chọn **Load Balancers**.
3. Chọn **Create Load Balancer**.
4. Chọn **Application Load Balancer**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.9-lab7/5.9.3-create-application-load-balancer.png" width="900">
</p>

<p align="center">
<i>Hình 5.9.4. Tạo Application Load Balancer.</i>
</p>

---

## Bước 2. Cấu hình Application Load Balancer

Trên trang cấu hình, thực hiện các bước sau:

1. Nhập tên Load Balancer.
2. Chọn **Internet-facing**.
3. Chọn **IPv4**.
4. Chọn các **Availability Zones**.
5. Chọn **Security Group**.
6. Chọn **Target Group** đã tạo ở bước trước.
7. Chọn **Create Load Balancer**.

Ví dụ:

```text
delivery-alb
```

---

## Bước 3. Kiểm tra Application Load Balancer

Sau khi tạo thành công:

- Mở danh sách **Load Balancers**.
- Kiểm tra trạng thái của Application Load Balancer.
- Xác nhận Listener đã được cấu hình.
- Kiểm tra Target Group đã được liên kết thành công.
- Đảm bảo trạng thái là **Active**.

---

## Bảng cấu hình

| Thuộc tính | Giá trị |
|---|---|
| AWS Service | Elastic Load Balancing |
| Resource | Application Load Balancer |
| Scheme | Internet-facing |
| IP Address Type | IPv4 |
| Listener | HTTP : 80 |
| Target Group | delivery-target-group |
| Status | Active |

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Tạo thành công Application Load Balancer.
- Cấu hình Listener.
- Liên kết Target Group với Load Balancer.
- Chuẩn bị hạ tầng cân bằng tải cho hệ thống.

Tiếp theo, chúng ta sẽ thực hiện **5.9.4 – Tạo Auto Scaling Group**.