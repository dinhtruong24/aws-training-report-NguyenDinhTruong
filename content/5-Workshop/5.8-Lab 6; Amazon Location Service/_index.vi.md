---
title : "Lab 6: Amazon Location Service"
date : 2024-01-01
weight : 8
chapter : false
pre : " <b>5.8. </b> "
---

Trong Lab này, chúng ta sẽ làm quen với **Amazon Location Service**, một dịch vụ của AWS cho phép tích hợp các chức năng bản đồ, tìm kiếm địa điểm, theo dõi vị trí và định tuyến vào ứng dụng.

Amazon Location Service cung cấp các API và SDK giúp xây dựng các ứng dụng có khả năng hiển thị bản đồ, tìm kiếm địa điểm và quản lý dữ liệu vị trí một cách an toàn và dễ dàng.

Trong Lab này, chúng ta sẽ cấu hình Amazon Location Service và kiểm tra các thành phần cần thiết để chuẩn bị cho việc tích hợp dịch vụ định vị vào ứng dụng.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.8-lab6/5.8.1-configure-amazon-location.png" width="900">
</p>

<p align="center">
<i>Hình 5.8.1. Cấu hình Amazon Location Service.</i>
</p>

---

## Mục tiêu của Lab

Sau khi hoàn thành Lab này, bạn sẽ thực hiện được các nội dung sau:

- Truy cập Amazon Location Service.
- Cấu hình các thành phần của Amazon Location.
- Làm quen với giao diện quản lý dịch vụ.
- Chuẩn bị môi trường để tích hợp chức năng bản đồ và định vị.

---

## Kiến trúc dịch vụ

Trong Lab này, Amazon Location Service được sử dụng theo mô hình sau:

```text
Application
      │
      ▼
Amazon Location Service
      │
      ├── Maps
      ├── Places
      ├── Routes
      └── Trackers
```

Amazon Location Service cung cấp các dịch vụ định vị để hỗ trợ ứng dụng hiển thị bản đồ, tìm kiếm địa điểm và xử lý dữ liệu vị trí.

---

## Thành phần chính

Lab này sử dụng các thành phần sau:

| Thành phần | Mô tả |
|---|---|
| Amazon Location Service | Dịch vụ định vị của AWS |
| Maps | Hiển thị bản đồ |
| Places | Tìm kiếm địa điểm |
| Routes | Tính toán tuyến đường |
| Trackers | Theo dõi vị trí thiết bị |

---

## Nội dung của Lab

Lab 6 gồm một phần duy nhất:

### 5.8.1 Configure Amazon Location

Trong phần này, chúng ta sẽ:

- Truy cập Amazon Location Service.
- Cấu hình các tài nguyên cần thiết.
- Kiểm tra cấu hình sau khi hoàn tất.

---

## Kết quả mong đợi

Sau khi hoàn thành Lab 6:

- Amazon Location Service đã được cấu hình.
- Các thành phần của dịch vụ đã sẵn sàng sử dụng.
- Môi trường đã được chuẩn bị để tích hợp chức năng bản đồ và định vị vào ứng dụng.

Sau khi hoàn thành Lab 6, chúng ta sẽ tiếp tục với **Lab 7**.