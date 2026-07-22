---
title : "Tạo Target Group"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b>5.9.2. </b> "
---

Trong phần này, chúng ta sẽ tạo một **Target Group** để quản lý các Amazon EC2 instances nhận lưu lượng truy cập từ **Application Load Balancer (ALB)**.

Target Group là thành phần trung gian giữa Load Balancer và các EC2 instances. Mỗi Target Group chứa danh sách các máy chủ đích và thực hiện **Health Checks** để đảm bảo chỉ các EC2 instances đang hoạt động bình thường mới nhận được yêu cầu từ người dùng.

---

## Bước 1. Mở Target Groups

Đăng nhập vào **AWS Management Console**.

Thực hiện các bước sau:

1. Mở dịch vụ **Amazon EC2**.
2. Trong menu bên trái, chọn **Target Groups**.
3. Chọn **Create target group**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.9-lab7/5.9.2-create-target-group.png" width="900">
</p>

<p align="center">
<i>Hình 5.9.3. Tạo Target Group.</i>
</p>

---

## Bước 2. Cấu hình Target Group

Trên trang **Create target group**, thực hiện các bước sau:

1. Chọn **Target type** là **Instances**.
2. Nhập tên Target Group.
3. Chọn **Protocol** và **Port**.
4. Chọn **VPC** tương ứng.
5. Cấu hình **Health Check**.
6. Chọn **Next** để tiếp tục.

Ví dụ:

```text
delivery-target-group
```

---

## Bước 3. Đăng ký EC2 Instances

Sau khi cấu hình Target Group:

1. Chọn các EC2 instances cần thêm vào Target Group.
2. Chọn **Include as pending below**.
3. Chọn **Create target group**.

Sau khi tạo thành công:

- Kiểm tra danh sách Target Groups.
- Xác nhận trạng thái Health Check của các EC2 instances.
- Đảm bảo Target Group sẵn sàng để liên kết với Application Load Balancer.

---

## Bảng cấu hình

| Thuộc tính | Giá trị |
|---|---|
| AWS Service | Amazon EC2 |
| Resource | Target Group |
| Target Type | Instances |
| Protocol | HTTP |
| Port | 80 |
| Health Check | Enabled |
| Status | Healthy |

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Tạo thành công Target Group.
- Cấu hình Health Check.
- Đăng ký các EC2 instances.
- Chuẩn bị Target Group để kết nối với Application Load Balancer.

Tiếp theo, chúng ta sẽ thực hiện **5.9.3 – Tạo Application Load Balancer**.