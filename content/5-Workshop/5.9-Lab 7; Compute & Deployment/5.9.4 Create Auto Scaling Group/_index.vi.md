---
title : "Tạo Auto Scaling Group"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b>5.9.4. </b> "
---

Trong phần này, chúng ta sẽ tạo một **Auto Scaling Group (ASG)** để tự động quản lý số lượng Amazon EC2 instances dựa trên nhu cầu của hệ thống.

Auto Scaling Group giúp duy trì số lượng EC2 instances theo cấu hình mong muốn và tự động tăng hoặc giảm số lượng máy chủ khi lưu lượng truy cập thay đổi. Khi kết hợp với Launch Template và Application Load Balancer, ASG giúp hệ thống đạt được khả năng mở rộng và tính sẵn sàng cao.

---

## Bước 1. Mở Auto Scaling Groups

Đăng nhập vào **AWS Management Console**.

Thực hiện các bước sau:

1. Mở dịch vụ **Amazon EC2**.
2. Trong menu bên trái, chọn **Auto Scaling Groups**.
3. Chọn **Create Auto Scaling group**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.9-lab7/5.9.4-create-auto-scaling-group.png" width="900">
</p>

<p align="center">
<i>Hình 5.9.5. Tạo Auto Scaling Group.</i>
</p>

---

## Bước 2. Cấu hình Auto Scaling Group

Trên trang **Create Auto Scaling group**, thực hiện các bước sau:

1. Nhập tên Auto Scaling Group.
2. Chọn **Launch Template** đã tạo ở phần trước.
3. Chọn **VPC** và các **Subnets**.
4. Liên kết với **Application Load Balancer**.
5. Chọn **Target Group**.
6. Thiết lập **Desired Capacity**, **Minimum Capacity** và **Maximum Capacity**.
7. Chọn **Create Auto Scaling group**.

Ví dụ:

```text
delivery-auto-scaling-group
```

---

## Bước 3. Kiểm tra Auto Scaling Group

Sau khi tạo thành công:

- Mở danh sách **Auto Scaling Groups**.
- Kiểm tra trạng thái của Auto Scaling Group.
- Xác nhận các EC2 instances đã được tạo từ Launch Template.
- Kiểm tra rằng các instances đã được đăng ký vào Target Group.
- Đảm bảo trạng thái của Auto Scaling Group là **In Service**.

---

## Bảng cấu hình

| Thuộc tính | Giá trị |
|---|---|
| AWS Service | Amazon EC2 Auto Scaling |
| Resource | Auto Scaling Group |
| Launch Template | `delivery-launch-template` |
| Target Group | `delivery-target-group` |
| Desired Capacity | 2 |
| Minimum Capacity | 2 |
| Maximum Capacity | 4 |
| Status | In Service |

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Tạo thành công Auto Scaling Group.
- Liên kết Launch Template với Auto Scaling Group.
- Kết nối Auto Scaling Group với Application Load Balancer.
- Xác nhận các EC2 instances hoạt động bình thường.
- Hoàn thành môi trường triển khai có khả năng tự động mở rộng.

Sau khi hoàn thành Lab 7, hệ thống đã sẵn sàng phục vụ ứng dụng với khả năng cân bằng tải và mở rộng tự động.