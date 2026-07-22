---
title : "Workshop Overview"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

## Giới thiệu

Trong workshop này, chúng ta sẽ triển khai **hệ thống quản lý giao hàng trên AWS** bằng kiến trúc nhiều tầng, bảo mật và có khả năng mở rộng.

Hệ thống hỗ trợ quản lý các nghiệp vụ giao hàng, lưu trữ thông tin đơn hàng, người dùng, trung tâm phân phối, trạng thái vận chuyển, ảnh Proof of Delivery (POD), chữ ký tài xế và minh chứng giao hàng thất bại.

Ứng dụng được triển khai trên **Amazon EC2** phía sau **Application Load Balancer**. Các EC2 instances chạy trong private application subnets, trong khi cơ sở dữ liệu **Amazon RDS for MySQL** được đặt trong private database subnets để hạn chế truy cập trực tiếp từ Internet.

Ngoài ra, hệ thống sử dụng Amazon S3 để lưu trữ tệp và hình ảnh, Amazon SQS để truyền sự kiện đơn hàng, AWS Lambda để xử lý tác vụ nền, Amazon SES để gửi email thông báo và Amazon Location Service để hỗ trợ tìm kiếm địa điểm và xử lý dữ liệu vị trí.

---

## Mục tiêu của Workshop

Sau khi hoàn thành workshop này, người thực hiện có thể:

- Thiết kế một Amazon VPC với public subnets, private application subnets và private database subnets.
- Cấu hình Internet Gateway, NAT Gateway và Route Tables.
- Xây dựng chuỗi Security Group cho Application Load Balancer, Amazon EC2 và Amazon RDS.
- Tạo IAM Role và Instance Profile cho EC2 theo nguyên tắc quyền tối thiểu.
- Triển khai Amazon RDS for MySQL trong private database subnets.
- Sử dụng AWS Secrets Manager để quản lý thông tin kết nối cơ sở dữ liệu.
- Lưu trữ ảnh POD, chữ ký và minh chứng giao hàng trên Amazon S3.
- Sử dụng Amazon SQS và AWS Lambda để xử lý sự kiện bất đồng bộ.
- Gửi email thông báo bằng Amazon SES.
- Tích hợp Amazon Location Service vào ứng dụng.
- Tạo Launch Template, Target Group, Application Load Balancer và Auto Scaling Group.
- Triển khai release ứng dụng bằng symbolic link.
- Thực hiện health check, rollback và kiểm thử toàn bộ hệ thống.

---

## Kiến trúc hệ thống

Hệ thống được xây dựng theo kiến trúc nhiều tầng trên AWS.

Người dùng gửi yêu cầu đến **Application Load Balancer** thông qua Internet. Load Balancer tiếp nhận lưu lượng và chuyển tiếp yêu cầu đến các Amazon EC2 instances đang ở trạng thái healthy trong Target Group.

Các EC2 instances chạy ứng dụng trong private application subnets và không cần public IP. Việc quản trị instance được thực hiện thông qua **AWS Systems Manager Session Manager** thay vì mở SSH trực tiếp từ Internet.

Ứng dụng lấy thông tin kết nối cơ sở dữ liệu từ **AWS Secrets Manager** và truy cập **Amazon RDS for MySQL** trong private database subnets.

Các tệp như ảnh POD, chữ ký tài xế, minh chứng giao hàng thất bại và gói triển khai được lưu trong **Amazon S3**. Khi trạng thái đơn hàng thay đổi, ứng dụng gửi sự kiện đến **Amazon SQS**. AWS Lambda xử lý message từ queue và có thể gửi email thông báo thông qua **Amazon SES**.

Amazon Location Service được sử dụng để hỗ trợ tìm kiếm địa điểm, geocoding và reverse geocoding trong ứng dụng.

---

## Luồng xử lý chính

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
Amazon EC2
  │
  ├── AWS Secrets Manager
  │        │
  │        ▼
  │   Amazon RDS MySQL
  │
  ├── Amazon S3
  │
  ├── Amazon SQS
  │        │
  │        ▼
  │    AWS Lambda
  │        │
  │        ▼
  │    Amazon SES
  │
  └── Amazon Location Service
```

---

## Các dịch vụ AWS sử dụng

Workshop sử dụng các dịch vụ AWS sau:

- Amazon VPC
- Internet Gateway
- NAT Gateway
- Amazon EC2
- Amazon EC2 Auto Scaling
- Application Load Balancer
- Amazon RDS for MySQL
- AWS Secrets Manager
- Amazon S3
- Amazon SQS
- AWS Lambda
- Amazon SES
- Amazon Location Service
- AWS IAM
- AWS Systems Manager
- AWS KMS

Mỗi dịch vụ đảm nhận một vai trò riêng nhằm đảm bảo hệ thống có khả năng mở rộng, bảo mật, lưu trữ dữ liệu an toàn và xử lý các tác vụ theo kiến trúc phù hợp.

---

## Kiến thức đạt được

Sau khi hoàn thành workshop, người học sẽ nắm được:

- Cách thiết kế kiến trúc mạng nhiều tầng trên Amazon VPC.
- Cách phân chia public, private application và private database subnets.
- Cách sử dụng Security Groups để kiểm soát luồng ALB → EC2 → RDS.
- Cách sử dụng IAM Role thay cho access key tĩnh.
- Cách triển khai ứng dụng trên Amazon EC2 trong private subnet.
- Cách lưu trữ dữ liệu và tệp ứng dụng trên Amazon S3.
- Cách sử dụng Amazon RDS for MySQL và AWS Secrets Manager.
- Cách xử lý sự kiện đơn hàng bằng Amazon SQS và AWS Lambda.
- Cách gửi email bằng Amazon SES.
- Cách tích hợp Amazon Location Service.
- Cách triển khai ứng dụng phía sau Application Load Balancer.
- Cách cấu hình Auto Scaling Group.
- Cách triển khai release bằng symlink và rollback khi có lỗi.
- Cách thực hiện End-to-End Testing và Cleanup tài nguyên AWS.

---

## Kiến trúc tổng thể

<p align="center">
  <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.1-Workshop-overview/overview5.1.png" width="1000">
</p>

<p align="center">
<i>Hình 5.1. Kiến trúc tổng thể của hệ thống quản lý giao hàng trên nền tảng AWS.</i>
</p>

---

Sau khi hoàn thành phần **Workshop Overview**, chúng ta sẽ tiếp tục chuẩn bị tài khoản AWS, quyền truy cập, công cụ và các điều kiện cần thiết trong phần **Prerequisites**.