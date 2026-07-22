---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

#### Tổng quan

Workshop này hướng dẫn triển khai **hệ thống quản lý giao hàng trên AWS** với kiến trúc nhiều tầng, bảo mật và có khả năng mở rộng.

Trong workshop, người học sẽ lần lượt xây dựng hạ tầng mạng, cấu hình bảo mật, triển khai cơ sở dữ liệu, lưu trữ dữ liệu trên Amazon S3, xử lý sự kiện bằng Amazon SQS và AWS Lambda, gửi email bằng Amazon SES, tích hợp Amazon Location Service và triển khai ứng dụng trên Amazon EC2 phía sau Application Load Balancer.

Hệ thống được thiết kế theo mô hình phân tầng gồm public subnet, private application subnet và private database subnet. Application Load Balancer tiếp nhận lưu lượng từ Internet, Amazon EC2 chạy ứng dụng trong private subnet và Amazon RDS MySQL lưu trữ dữ liệu trong database subnet.

Ngoài ra, workshop còn hướng dẫn triển khai ứng dụng bằng symbolic link, kiểm tra health check, rollback khi release mới gặp lỗi, kiểm thử toàn bộ hệ thống và dọn dẹp tài nguyên sau khi hoàn thành.

---

#### Điểm nổi bật về kiến trúc

- **Networking:** Amazon VPC được chia thành public subnets, private application subnets và private database subnets trên nhiều Availability Zones.
- **Load Balancing:** Application Load Balancer tiếp nhận lưu lượng từ Internet và chuyển tiếp yêu cầu đến Target Group.
- **Compute:** Amazon EC2 chạy ứng dụng quản lý giao hàng và được quản lý bởi Auto Scaling Group.
- **Database:** Amazon RDS for MySQL lưu trữ dữ liệu nghiệp vụ trong private database subnets.
- **Secrets Management:** AWS Secrets Manager lưu thông tin kết nối cơ sở dữ liệu và giúp ứng dụng không phải lưu credential trực tiếp trong source code.
- **Storage:** Amazon S3 lưu trữ ảnh POD, chữ ký tài xế, minh chứng giao hàng thất bại và các gói triển khai ứng dụng.
- **Messaging:** Amazon SQS tiếp nhận các sự kiện đơn hàng và hỗ trợ xử lý bất đồng bộ.
- **Serverless Processing:** AWS Lambda xử lý các sự kiện từ SQS và thực hiện các tác vụ nền.
- **Email:** Amazon SES được sử dụng để gửi email thông báo.
- **Location Services:** Amazon Location Service hỗ trợ tìm kiếm địa điểm và xử lý dữ liệu vị trí.
- **Security:** AWS IAM, Security Groups và Instance Profiles kiểm soát quyền truy cập giữa các tài nguyên.
- **Deployment:** Ứng dụng được triển khai trên EC2 bằng release directory và symbolic link để hỗ trợ chuyển phiên bản và rollback.
- **High Availability:** Application Load Balancer và Auto Scaling Group giúp tăng tính sẵn sàng và khả năng mở rộng của hệ thống.

---

#### Nội dung

1. [Tổng quan về workshop](5.1-Workshop-overview/)
2. [Chuẩn bị](5.2-Prerequiste/)
3. [Lab 1: Network Infrastructure](5.3/)
4. [Lab 2: Security Groups và IAM](5.4/)
5. [Lab 3: Storage với Amazon S3](5.5/)
6. [Lab 4: Database và các dịch vụ liên quan](5.6/)
7. [Lab 5: Events, Lambda và Email](5.7/)
8. [Lab 6: Amazon Location Service](5.8/)
9. [Lab 7: Compute & Deployment](5.9/)
10. [End-to-End Testing](5.10/)
11. [Cleanup](5.11/)

---

## Mục tiêu đạt được

Sau khi hoàn thành workshop, người học có thể:

- Thiết kế VPC với public, private application và private database subnets.
- Cấu hình Internet Gateway, Route Tables và NAT Gateway.
- Xây dựng chuỗi Security Group cho Application Load Balancer, Amazon EC2 và Amazon RDS.
- Tạo IAM Role và Instance Profile cho EC2 theo nguyên tắc quyền tối thiểu.
- Lưu trữ dữ liệu ứng dụng trên Amazon S3.
- Triển khai Amazon RDS for MySQL trong private database subnets.
- Sử dụng AWS Secrets Manager để quản lý thông tin kết nối cơ sở dữ liệu.
- Cấu hình Amazon SQS và AWS Lambda để xử lý sự kiện đơn hàng.
- Gửi email thông báo bằng Amazon SES.
- Tích hợp Amazon Location Service vào ứng dụng.
- Tạo Launch Template, Target Group, Application Load Balancer và Auto Scaling Group.
- Triển khai release ứng dụng từ Amazon S3 bằng symbolic link.
- Thực hiện health check và rollback khi release mới gặp lỗi.
- Kiểm thử toàn bộ hệ thống từ người dùng đến ứng dụng và cơ sở dữ liệu.
- Dọn dẹp các tài nguyên AWS để tránh phát sinh chi phí không cần thiết.

---

## Kiến trúc hệ thống

<p align="center">
  <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/Workshop.png" width="900">
</p>