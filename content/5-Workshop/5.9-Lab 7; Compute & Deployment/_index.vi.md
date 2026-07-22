---
title : "Lab 7: Compute & Deployment"
date : 2024-01-01
weight : 9
chapter : false
pre : " <b>5.9. </b> "
---

Trong Lab này, chúng ta sẽ triển khai hạ tầng tính toán và cấu hình các thành phần cần thiết để ứng dụng có thể hoạt động với khả năng mở rộng và tính sẵn sàng cao trên AWS.

Chúng ta sẽ sử dụng **Amazon EC2**, **Application Load Balancer (ALB)** và **Amazon EC2 Auto Scaling** để xây dựng môi trường triển khai. Kiến trúc này giúp phân phối lưu lượng truy cập giữa nhiều EC2 instances và tự động tăng hoặc giảm số lượng máy chủ theo nhu cầu của hệ thống.

Trong Lab này, chúng ta sẽ tạo **Launch Template**, **Target Group**, **Application Load Balancer** và **Auto Scaling Group** để hoàn thiện môi trường triển khai.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.9-lab7/5.9.1-create-launch-template.png" width="900">
</p>

<p align="center">
<i>Hình 5.9.1. Tạo Launch Template.</i>
</p>

---

## Mục tiêu của Lab

Sau khi hoàn thành Lab này, bạn sẽ có thể:

- Tạo Launch Template cho EC2.
- Tạo Target Group.
- Cấu hình Application Load Balancer.
- Tạo Auto Scaling Group.
- Chuẩn bị môi trường triển khai có khả năng mở rộng.

---

## Kiến trúc triển khai

Trong Lab này, hệ thống được triển khai theo mô hình sau:

```text
Internet
     │
     ▼
Application Load Balancer
     │
     ▼
Target Group
     │
     ▼
Auto Scaling Group
     │
     ▼
Amazon EC2 Instances
```

Application Load Balancer sẽ phân phối lưu lượng truy cập đến các EC2 instances trong Auto Scaling Group, giúp tăng khả năng chịu tải và đảm bảo tính sẵn sàng của ứng dụng.

---

## Thành phần chính

Lab này sử dụng các thành phần sau:

| Thành phần | Mô tả |
|---|---|
| Amazon EC2 | Máy chủ ứng dụng |
| Launch Template | Mẫu cấu hình EC2 |
| Target Group | Nhóm đích của Load Balancer |
| Application Load Balancer | Cân bằng tải ứng dụng |
| Auto Scaling Group | Tự động mở rộng EC2 |

---

## Nội dung của Lab

Lab 7 gồm bốn phần:

### 5.9.1 Create Launch Template

- Tạo Launch Template.
- Cấu hình AMI, Instance Type và Security Group.

### 5.9.2 Create Target Group

- Tạo Target Group.
- Cấu hình Health Check.

### 5.9.3 Create Application Load Balancer

- Tạo Application Load Balancer.
- Liên kết với Target Group.

### 5.9.4 Create Auto Scaling Group

- Tạo Auto Scaling Group.
- Liên kết Launch Template và Load Balancer.
- Kiểm tra khả năng tự động mở rộng.

---

## Kết quả mong đợi

Sau khi hoàn thành Lab 7:

- Launch Template đã được tạo.
- Target Group đã được cấu hình.
- Application Load Balancer hoạt động bình thường.
- Auto Scaling Group đã được triển khai.
- Môi trường triển khai có khả năng mở rộng và sẵn sàng phục vụ ứng dụng.

Sau khi hoàn thành Lab 7, hệ thống đã sẵn sàng cho bước **End-to-End Testing** trong phần tiếp theo.