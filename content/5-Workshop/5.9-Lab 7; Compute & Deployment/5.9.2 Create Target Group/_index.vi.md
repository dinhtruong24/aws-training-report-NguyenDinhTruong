---
title : "Create Target Group"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b>5.9.2. </b> "
---

Trong phần này, chúng ta sẽ tạo **Target Group** có tên `delivery-app-tg` để nhận lưu lượng từ Application Load Balancer và chuyển tiếp đến các EC2 instances đang chạy ứng dụng.

Theo cấu hình trong tài liệu, ứng dụng lắng nghe trên cổng HTTP `5000`. Target Group sẽ thực hiện health check để xác định những EC2 instances đang hoạt động bình thường trước khi chuyển tiếp yêu cầu.

---

## Bước 1. Mở Target Groups

Đăng nhập vào **AWS Management Console**.

Thực hiện các bước sau:

1. Mở dịch vụ **Amazon EC2**.
2. Trong menu bên trái, chọn **Target Groups**.
3. Chọn **Create target group**.
4. Chọn loại target phù hợp cho các EC2 instances.

---

## Bước 2. Cấu hình Target Group

Cấu hình Target Group theo các thông tin sau:

| Thuộc tính | Giá trị |
|---|---|
| Target Group Name | `delivery-app-tg` |
| Protocol | HTTP |
| Port | `5000` |
| Target Type | EC2 Instances |
| Health Check Protocol | HTTP |
| Health Check Path | `/` hoặc endpoint health riêng |

Target Group sử dụng HTTP trên cổng `5000`, tương ứng với cổng mà ứng dụng đang lắng nghe trên EC2.

Health check có thể sử dụng đường dẫn `/` hoặc một endpoint health riêng của ứng dụng. Endpoint được chọn phải trả về phản hồi thành công để Target Group xác định instance ở trạng thái healthy.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.9-lab7/5.9.1-verify-email-identity.png" width="900">
</p>

<p align="center">
<i>Hình 5.9.2. Target Group delivery-app-tg trên cổng HTTP 5000.</i>
</p>

---

## Bước 3. Đăng ký EC2 Instances

Sau khi cấu hình Target Group:

1. Chọn các EC2 instances chạy ứng dụng.
2. Đăng ký các instances vào `delivery-app-tg`.
3. Xác nhận cổng nhận lưu lượng là `5000`.
4. Hoàn tất quá trình tạo Target Group.

Các EC2 instances được tạo từ Launch Template `delivery-ec2-lt` và chạy trong private application subnets.

---

## Bước 4. Kiểm tra Health Check

Sau khi Target Group được tạo:

- Mở Target Group `delivery-app-tg`.
- Chọn tab **Targets**.
- Kiểm tra các EC2 instances đã được đăng ký.
- Xác nhận health check sử dụng đúng cổng `5000`.
- Kiểm tra trạng thái của instance.

Trạng thái mong đợi:

```text
Healthy
```

Nếu instance chưa healthy, cần kiểm tra:

- `delivery.service` có đang chạy hay không.
- Ứng dụng có lắng nghe trên cổng `5000` hay không.
- Security Group `delivery-ec2-sg` có cho phép lưu lượng từ `delivery-alb-sg` hay không.
- Health check path có trả về HTTP thành công hay không.

---

## Chuỗi kết nối

Target Group nằm giữa Application Load Balancer và các EC2 instances:

```text
Application Load Balancer
            │
            ▼
delivery-app-tg
HTTP:5000
            │
            ▼
Amazon EC2 Instances
            │
            ▼
delivery.service
```

Application Load Balancer chỉ chuyển tiếp lưu lượng đến những EC2 instances được Target Group xác định là healthy.

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Tạo Target Group `delivery-app-tg`.
- Cấu hình giao thức HTTP trên cổng `5000`.
- Cấu hình health check cho ứng dụng.
- Đăng ký các EC2 instances vào Target Group.
- Chuẩn bị Target Group để liên kết với Application Load Balancer.