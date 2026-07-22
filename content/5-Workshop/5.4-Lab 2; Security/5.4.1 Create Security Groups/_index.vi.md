---
title : "Tạo Security Groups"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b>5.4.1. </b> "
---

Trong phần này, chúng ta sẽ tạo các **Security Groups** để kiểm soát lưu lượng mạng giữa các thành phần của hệ thống.

Ba Security Groups sẽ được tạo gồm:

- Security Group cho Application Load Balancer.
- Security Group cho EC2 Application Server.
- Security Group cho Amazon RDS.

Việc tách riêng Security Groups giúp tăng cường bảo mật và chỉ cho phép các kết nối cần thiết giữa các thành phần.

---

## Bước 1. Tạo Security Group cho Application Load Balancer

Đăng nhập **AWS Management Console**, mở dịch vụ **EC2**, sau đó:

1. Chọn **Security Groups**.
2. Chọn **Create security group**.
3. Nhập:

```text
Security group name:
delivery-alb-sg
```

4. Description:

```text
Security Group for Application Load Balancer
```

5. Chọn VPC:

```text
delivery-dev-vpc
```

6. Thêm Inbound Rules:

| Type | Port | Source |
|------|------|--------|
| HTTP | 80 | 0.0.0.0/0 |
| HTTPS | 443 | 0.0.0.0/0 |

7. Chọn **Create security group**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.4-lab2/5.4.1-create-alb-security-group.png" width="900">
</p>

<p align="center">
<i>Hình 5.4.1. Tạo Security Group cho Application Load Balancer.</i>
</p>

---

## Bước 2. Tạo Security Group cho EC2

Tiếp tục tạo Security Group mới.

Nhập:

```text
delivery-ec2-sg
```

Description:

```text
Security Group for EC2
```

Chọn cùng VPC:

```text
delivery-dev-vpc
```

Cấu hình Inbound Rules:

| Type | Port | Source |
|------|------|--------|
| HTTP | 80 | delivery-alb-sg |
| HTTPS | 443 | delivery-alb-sg |

Điều này đảm bảo chỉ Application Load Balancer mới có thể truy cập EC2.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.4-lab2/5.4.1-create-ec2-security-group.png" width="900">
</p>

<p align="center">
<i>Hình 5.4.2. Tạo Security Group cho EC2.</i>
</p>

---

## Bước 3. Tạo Security Group cho Amazon RDS

Tiếp tục tạo Security Group cuối cùng.

Tên:

```text
delivery-rds-sg
```

Description:

```text
Security Group for Amazon RDS
```

Inbound Rule:

| Type | Port | Source |
|------|------|--------|
| MySQL/Aurora | 3306 | delivery-ec2-sg |

Nhờ đó chỉ EC2 Application Server mới có quyền kết nối tới cơ sở dữ liệu.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.4-lab2/5.4.1-create-rds-security-group.png" width="900">
</p>

<p align="center">
<i>Hình 5.4.3. Tạo Security Group cho Amazon RDS.</i>
</p>

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Tạo Security Group cho Application Load Balancer.
- Tạo Security Group cho EC2 Application Server.
- Tạo Security Group cho Amazon RDS.
- Thiết lập quy tắc truy cập giữa các thành phần của hệ thống.
- Hoàn thành cấu hình Security Groups cho Lab 2.

Trong phần tiếp theo, chúng ta sẽ thực hiện **5.4.2 – Cấu hình IAM Role và IAM Policy**.