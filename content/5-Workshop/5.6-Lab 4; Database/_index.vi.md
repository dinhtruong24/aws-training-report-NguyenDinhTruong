---
title : "Lab 4: CloudWatch Monitoring"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b>5.6. </b> "
---

Trong Lab này, chúng ta sẽ sử dụng **Amazon CloudWatch** để giám sát hoạt động của các tài nguyên AWS trong hệ thống.

Amazon CloudWatch là dịch vụ giám sát và quan sát (Monitoring & Observability) của AWS, cho phép thu thập Metrics, Logs và Events từ các dịch vụ như Amazon EC2, Amazon RDS và Application Load Balancer.

Ngoài việc theo dõi hiệu năng của hệ thống, CloudWatch còn hỗ trợ tạo Alarm để gửi cảnh báo khi tài nguyên vượt quá các ngưỡng được cấu hình trước.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.6-lab4/5.6.1-open-cloudwatch-dashboard.png" width="900">
</p>

<p align="center">
<i>Hình 5.6.1. Giao diện Amazon CloudWatch Dashboard.</i>
</p>

---

## Mục tiêu của Lab

Sau khi hoàn thành Lab này, bạn sẽ thực hiện được các nội dung sau:

- Truy cập Amazon CloudWatch Dashboard.
- Theo dõi các Metrics của hệ thống.
- Kiểm tra hiệu năng của EC2 Instance.
- Giám sát CPU, Network và các tài nguyên AWS.
- Tạo CloudWatch Alarm.
- Thiết lập điều kiện cảnh báo.
- Chuẩn bị môi trường giám sát cho hệ thống.

---

## Kiến trúc giám sát

Trong Lab này, Amazon CloudWatch sẽ thu thập Metrics từ các tài nguyên AWS như sau:

```text
EC2 Instance
        │
        ▼
Amazon CloudWatch
        │
        ├── Metrics
        ├── Dashboard
        └── Alarm
```

CloudWatch sẽ liên tục thu thập dữ liệu hoạt động của hệ thống để hỗ trợ giám sát và cảnh báo.

---

## Thành phần chính

Lab này sử dụng các thành phần sau:

| Thành phần | Mô tả |
|---|---|
| Amazon CloudWatch | Dịch vụ giám sát hệ thống |
| Dashboard | Hiển thị thông tin giám sát |
| Metrics | Dữ liệu hiệu năng của tài nguyên |
| Alarm | Cảnh báo khi vượt ngưỡng cấu hình |

---

## Nội dung của Lab

Lab 4 được chia thành ba phần:

### 5.6.1 Truy cập CloudWatch Dashboard

Trong phần này, chúng ta sẽ:

- Mở dịch vụ Amazon CloudWatch.
- Truy cập Dashboard.
- Làm quen với giao diện giám sát.

### 5.6.2 Theo dõi CloudWatch Metrics

Trong phần này, chúng ta sẽ:

- Xem Metrics của EC2.
- Theo dõi CPU Utilization.
- Theo dõi Network In và Network Out.
- Kiểm tra tình trạng hoạt động của tài nguyên.

### 5.6.3 Tạo CloudWatch Alarm

Trong phần này, chúng ta sẽ:

- Tạo Alarm mới.
- Chọn Metric cần giám sát.
- Thiết lập ngưỡng cảnh báo.
- Kiểm tra Alarm sau khi tạo.

---

## Kết quả mong đợi

Sau khi hoàn thành Lab 4:

- Amazon CloudWatch đã được cấu hình.
- Dashboard hiển thị các Metrics của hệ thống.
- Theo dõi được hiệu năng của EC2.
- CloudWatch Alarm được tạo thành công.
- Hệ thống đã có khả năng giám sát và cảnh báo tài nguyên AWS.

Sau khi hoàn thành Lab 4, hệ thống sẽ sẵn sàng cho **Lab 5 – AWS Backup**.