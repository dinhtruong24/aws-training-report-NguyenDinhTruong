---
title : "Truy cập CloudWatch Dashboard"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b>5.6.1. </b> "
---

Trong phần này, chúng ta sẽ truy cập **Amazon CloudWatch Dashboard** để theo dõi trạng thái và hiệu năng của các tài nguyên AWS trong hệ thống.

CloudWatch Dashboard cung cấp giao diện trực quan giúp người quản trị theo dõi các chỉ số (Metrics), nhật ký (Logs) và các cảnh báo (Alarms) được thu thập từ các dịch vụ AWS.

---

## Bước 1. Mở dịch vụ Amazon CloudWatch

Đăng nhập vào **AWS Management Console**.

Thực hiện các bước sau:

1. Tìm kiếm dịch vụ **Amazon CloudWatch**.
2. Chọn **CloudWatch**.
3. Mở trang **Dashboard**.

---

## Bước 2. Truy cập Dashboard

Sau khi mở Dashboard, bạn có thể quan sát các thông tin sau:

- Danh sách Dashboard hiện có.
- Các biểu đồ giám sát tài nguyên.
- Các Metrics đang được thu thập.
- Trạng thái của các CloudWatch Alarm.

Dashboard cho phép người quản trị theo dõi toàn bộ hệ thống từ một giao diện duy nhất.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.6-lab4/5.6.1-open-cloudwatch-dashboard.png" width="900">
</p>

<p align="center">
<i>Hình 5.6.2. Truy cập Amazon CloudWatch Dashboard.</i>
</p>

---

## Bước 3. Kiểm tra Dashboard

Sau khi truy cập thành công:

- Xác nhận Dashboard hiển thị bình thường.
- Kiểm tra các Metrics đang được thu thập.
- Kiểm tra trạng thái của các Alarm (nếu có).
- Làm quen với giao diện quản lý của CloudWatch.

Dashboard sẽ được sử dụng trong các phần tiếp theo để theo dõi hiệu năng và trạng thái của hệ thống.

---

## Bảng thông tin

| Thành phần | Mô tả |
|---|---|
| AWS Service | Amazon CloudWatch |
| Dashboard | Giao diện giám sát hệ thống |
| Metrics | Dữ liệu hiệu năng của tài nguyên |
| Alarms | Cảnh báo khi vượt ngưỡng cấu hình |

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Truy cập thành công Amazon CloudWatch Dashboard.
- Quan sát được giao diện giám sát của CloudWatch.
- Xem các Metrics và Alarm hiện có.
- Chuẩn bị môi trường để theo dõi hiệu năng của hệ thống.

Tiếp theo, chúng ta sẽ thực hiện **5.6.2 – Theo dõi CloudWatch Metrics**.