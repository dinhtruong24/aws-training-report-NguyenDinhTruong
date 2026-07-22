---
title : "Tạo CloudWatch Alarm"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b>5.6.3. </b> "
---

Trong phần này, chúng ta sẽ tạo **Amazon CloudWatch Alarm** để giám sát các chỉ số hiệu năng của tài nguyên AWS.

CloudWatch Alarm cho phép theo dõi các Metrics và tự động thay đổi trạng thái khi giá trị của Metric vượt quá ngưỡng đã được cấu hình. Điều này giúp người quản trị nhanh chóng phát hiện các sự cố và đưa ra biện pháp xử lý kịp thời.

---

## Bước 1. Mở CloudWatch Alarms

Đăng nhập vào **AWS Management Console**.

Thực hiện các bước sau:

1. Mở dịch vụ **Amazon CloudWatch**.
2. Chọn **Alarms**.
3. Chọn **Create alarm**.

---

## Bước 2. Cấu hình Alarm

Trong màn hình **Create alarm**, thực hiện các bước sau:

1. Chọn **Select metric**.
2. Chọn Metric cần giám sát.
3. Thiết lập ngưỡng cảnh báo.
4. Chọn điều kiện kích hoạt Alarm.
5. Đặt tên cho Alarm.
6. Chọn **Create alarm**.

Sau khi hoàn tất, CloudWatch sẽ tự động theo dõi Metric đã chọn.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.6-lab4/5.6.3-create-cloudwatch-alarm.png" width="900">
</p>

<p align="center">
<i>Hình 5.6.4. Tạo Amazon CloudWatch Alarm.</i>
</p>

---

## Bước 3. Kiểm tra Alarm

Sau khi Alarm được tạo thành công:

- Mở danh sách **Alarms**.
- Xác nhận Alarm hiển thị trong danh sách.
- Kiểm tra trạng thái của Alarm.
- Xác nhận Alarm đang theo dõi đúng Metric đã chọn.

CloudWatch sẽ liên tục đánh giá Metric và tự động cập nhật trạng thái của Alarm khi điều kiện thay đổi.

---

## Bảng cấu hình

| Thành phần | Mô tả |
|---|---|
| AWS Service | Amazon CloudWatch |
| Resource | CloudWatch Alarm |
| Metric | Chỉ số cần giám sát |
| Threshold | Ngưỡng kích hoạt cảnh báo |
| Status | OK / Alarm / Insufficient Data |

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Tạo thành công CloudWatch Alarm.
- Cấu hình Metric cần giám sát.
- Thiết lập ngưỡng cảnh báo.
- Kiểm tra trạng thái hoạt động của Alarm.
- Hoàn thành Lab 4 về giám sát hệ thống bằng Amazon CloudWatch.

Sau khi hoàn thành Lab 4, hệ thống đã có khả năng giám sát hiệu năng và cảnh báo tự động đối với các tài nguyên AWS.