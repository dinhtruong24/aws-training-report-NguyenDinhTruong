---
title : "Theo dõi CloudWatch Metrics"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b>5.6.2. </b> "
---

Trong phần này, chúng ta sẽ sử dụng **Amazon CloudWatch Metrics** để theo dõi hiệu năng của các tài nguyên AWS.

CloudWatch tự động thu thập các chỉ số hiệu năng từ nhiều dịch vụ AWS như Amazon EC2, Amazon RDS và Application Load Balancer. Các chỉ số này giúp đánh giá tình trạng hoạt động của hệ thống và hỗ trợ phát hiện sớm các vấn đề về hiệu năng.

---

## Bước 1. Mở CloudWatch Metrics

Đăng nhập vào **AWS Management Console**.

Thực hiện các bước sau:

1. Mở dịch vụ **Amazon CloudWatch**.
2. Chọn **Metrics**.
3. Chọn dịch vụ cần theo dõi.

---

## Bước 2. Xem các chỉ số hiệu năng

Trong màn hình **Metrics**, bạn có thể theo dõi các chỉ số như:

- CPU Utilization
- Network In
- Network Out
- Disk Read Operations
- Disk Write Operations

Các biểu đồ sẽ hiển thị dữ liệu theo thời gian thực, giúp đánh giá hiệu năng của tài nguyên.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.6-lab4/5.6.2-view-cloudwatch-metrics.png" width="900">
</p>

<p align="center">
<i>Hình 5.6.3. Theo dõi các CloudWatch Metrics.</i>
</p>

---

## Bước 3. Kiểm tra Metrics

Sau khi mở Metrics:

- Xác nhận các biểu đồ hiển thị dữ liệu.
- Kiểm tra mức sử dụng CPU.
- Theo dõi lưu lượng mạng vào và ra.
- Quan sát xu hướng hoạt động của tài nguyên theo thời gian.

Thông tin này sẽ được sử dụng để đánh giá hiệu năng và hỗ trợ cấu hình CloudWatch Alarm trong bước tiếp theo.

---

## Bảng thông tin

| Metric | Mô tả |
|---|---|
| CPU Utilization | Mức sử dụng CPU |
| Network In | Lưu lượng dữ liệu vào |
| Network Out | Lưu lượng dữ liệu ra |
| Disk Read Ops | Số lần đọc đĩa |
| Disk Write Ops | Số lần ghi đĩa |

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Truy cập thành công CloudWatch Metrics.
- Theo dõi hiệu năng của tài nguyên AWS.
- Quan sát các chỉ số CPU và Network.
- Chuẩn bị dữ liệu để cấu hình CloudWatch Alarm.

Tiếp theo, chúng ta sẽ thực hiện **5.6.3 – Tạo CloudWatch Alarm**.