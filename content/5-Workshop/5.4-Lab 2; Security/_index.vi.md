---
title : "Lab 2: Security Groups và IAM"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b>5.4. </b> "
---

Trong Lab này, chúng ta sẽ xây dựng lớp bảo mật cho hệ thống bằng cách cấu hình **Security Groups**, **IAM Role** và **IAM Policy**.

Security Groups được sử dụng để kiểm soát lưu lượng mạng giữa Application Load Balancer, EC2 Application Server và Amazon RDS. Mỗi thành phần sẽ sử dụng một Security Group riêng, giúp giới hạn kết nối và chỉ cho phép các luồng giao tiếp cần thiết.

Bên cạnh đó, một IAM Role dành cho EC2 sẽ được tạo để ứng dụng có thể truy cập các dịch vụ AWS bằng thông tin xác thực tạm thời. Phương pháp này giúp tránh lưu Access Key và Secret Access Key trực tiếp trong mã nguồn hoặc tệp cấu hình của ứng dụng.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.4-lab2/5.4.1-create-alb-security-group.png" width="900">
</p>

<p align="center">
<i>Hình 5.4.1. Cấu hình lớp bảo mật cho các thành phần của hệ thống.</i>
</p>

---

## Mục tiêu của Lab

Sau khi hoàn thành Lab này, bạn sẽ thực hiện được các nội dung sau:

- Tạo Security Group cho Application Load Balancer.
- Tạo Security Group cho EC2 Application Server.
- Tạo Security Group cho Amazon RDS.
- Giới hạn lưu lượng giữa ALB, EC2 và RDS.
- Tạo IAM Role dành cho EC2 Instance.
- Cấu hình Trust Relationship cho EC2.
- Tạo Runtime IAM Policy cho ứng dụng.
- Gắn IAM Policy vào IAM Role.
- Kiểm tra danh tính IAM bằng AWS STS.
- Kiểm tra quyền truy cập Amazon S3 và Amazon SQS.
- Áp dụng nguyên tắc **Least Privilege**.
- Tránh sử dụng Access Key cố định trên EC2 Instance.

---

## Kiến trúc bảo mật

Security Groups trong Lab này được cấu hình theo chuỗi truy cập:

```text
Internet
   ↓
Application Load Balancer
   ↓
EC2 Application Server
   ↓
Amazon RDS
```

Luồng truy cập được kiểm soát như sau:

| Thành phần | Lưu lượng được cho phép |
|---|---|
| `delivery-alb-sg` | Cho phép HTTP và HTTPS từ Internet |
| `delivery-ec2-sg` | Chỉ cho phép lưu lượng ứng dụng từ `delivery-alb-sg` |
| `delivery-rds-sg` | Chỉ cho phép kết nối MySQL từ `delivery-ec2-sg` |

Cấu hình này giúp Amazon RDS không bị truy cập trực tiếp từ Internet. EC2 Application Server cũng chỉ nhận lưu lượng thông qua Application Load Balancer.

---

## Cấu hình IAM

EC2 Instance sẽ sử dụng IAM Role:

```text
delivery-ec2-role
```

IAM Role được gắn Runtime Policy:

```text
delivery-runtime-policy
```

Runtime Policy cung cấp các quyền cần thiết để ứng dụng tương tác với những dịch vụ AWS như:

- Amazon S3
- Amazon SQS
- AWS STS
- Các dịch vụ hỗ trợ khác được sử dụng trong hệ thống

Các quyền chỉ nên được giới hạn trong những hành động và tài nguyên cần thiết, tuân thủ nguyên tắc:

```text
Principle of Least Privilege
```

---

## Nội dung của Lab

Lab 2 được chia thành ba phần:

### 5.4.1 Tạo Security Groups

Trong phần này, chúng ta sẽ:

- Tạo `delivery-alb-sg`.
- Cho phép HTTP và HTTPS từ Internet đến Application Load Balancer.
- Tạo `delivery-ec2-sg`.
- Chỉ cho phép Application Load Balancer truy cập EC2.
- Tạo `delivery-rds-sg`.
- Chỉ cho phép EC2 kết nối đến Amazon RDS qua cổng MySQL 3306.

### 5.4.2 Cấu hình IAM Role và IAM Policy

Trong phần này, chúng ta sẽ:

- Tạo IAM Role `delivery-ec2-role`.
- Chọn EC2 làm Trusted Entity.
- Kiểm tra Trust Relationship.
- Tạo Runtime Policy `delivery-runtime-policy`.
- Cấu hình quyền truy cập các dịch vụ AWS cần thiết.
- Gắn Runtime Policy vào IAM Role.

### 5.4.3 Kiểm tra quyền IAM

Trong phần này, chúng ta sẽ:

- Gắn IAM Role vào EC2 Instance.
- Kiểm tra danh tính bằng AWS STS.
- Kiểm tra quyền truy cập Amazon S3.
- Kiểm tra quyền truy cập Amazon SQS.
- Xác nhận ứng dụng sử dụng thông tin xác thực tạm thời.
- Kiểm tra nguyên tắc Least Privilege.
- Xử lý các lỗi `Unable to locate credentials` và `AccessDenied`.

---

## Kết quả mong đợi

Sau khi hoàn thành Lab 2:

- Ba Security Groups đã được tạo và cấu hình đúng.
- Lưu lượng mạng giữa ALB, EC2 và RDS được kiểm soát.
- Amazon RDS không thể bị truy cập trực tiếp từ Internet.
- IAM Role dành cho EC2 đã được tạo.
- Runtime IAM Policy đã được gắn vào IAM Role.
- EC2 Instance có thể nhận thông tin xác thực tạm thời.
- Ứng dụng có thể truy cập các dịch vụ AWS được cấp quyền.
- Không cần lưu Access Key hoặc Secret Access Key trên EC2.
- Hệ thống đã có lớp bảo mật mạng và quyền truy cập AWS phù hợp.

Sau khi hoàn thành Lab 2, hệ thống sẽ sẵn sàng cho **Lab 3 – Amazon S3 Storage**.