---
title : "Lab 3: Amazon S3 Storage"
date : 2024-01-01
weight : 5
chapter : false
pre : " <b>5.5. </b> "
---

Trong Lab này, chúng ta sẽ triển khai dịch vụ **Amazon Simple Storage Service (Amazon S3)** để lưu trữ dữ liệu của hệ thống.

Amazon S3 là dịch vụ lưu trữ đối tượng có độ bền cao, khả năng mở rộng gần như không giới hạn và tích hợp với nhiều dịch vụ AWS khác. Trong hệ thống này, Amazon S3 được sử dụng để lưu trữ tài liệu, hình ảnh và các tệp do người dùng tải lên.

Bên cạnh việc tạo S3 Bucket và cấu trúc thư mục, chúng ta cũng sẽ cấu hình **S3 Gateway Endpoint** để các tài nguyên trong VPC có thể truy cập Amazon S3 mà không cần đi qua Internet, giúp tăng tính bảo mật và tối ưu chi phí truyền dữ liệu.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.5-lab3/5.5.1-create-s3-bucket.png" width="900">
</p>

<p align="center">
<i>Hình 5.5.1. Tạo Amazon S3 Bucket cho hệ thống.</i>
</p>

---

## Mục tiêu của Lab

Sau khi hoàn thành Lab này, bạn sẽ thực hiện được các nội dung sau:

- Tạo Amazon S3 Bucket.
- Thiết lập cấu trúc thư mục lưu trữ.
- Quản lý dữ liệu trong Amazon S3.
- Cấu hình S3 Gateway Endpoint.
- Cho phép EC2 truy cập Amazon S3 thông qua mạng nội bộ AWS.
- Giảm lưu lượng Internet bằng Gateway Endpoint.
- Chuẩn bị môi trường lưu trữ cho các Lab tiếp theo.

---

## Kiến trúc lưu trữ

Trong Lab này, hệ thống lưu trữ được tổ chức như sau:

```text
Application
      │
      ▼
Amazon S3 Bucket
      │
      ├── documents/
      ├── uploads/
      └── backups/
```

Các EC2 Instance sẽ truy cập trực tiếp vào Amazon S3 thông qua **S3 Gateway Endpoint** mà không cần sử dụng Internet Gateway hoặc NAT Gateway.

---

## Thành phần chính

Lab này sử dụng các thành phần sau:

| Thành phần | Mô tả |
|---|---|
| Amazon S3 | Lưu trữ dữ liệu của hệ thống |
| S3 Bucket | Bucket chứa toàn bộ dữ liệu |
| Folder Structure | Tổ chức dữ liệu theo từng thư mục |
| S3 Gateway Endpoint | Truy cập Amazon S3 từ VPC |

---

## Nội dung của Lab

Lab 3 được chia thành ba phần:

### 5.5.1 Tạo Amazon S3 Bucket

Trong phần này, chúng ta sẽ:

- Tạo Bucket mới.
- Cấu hình Region.
- Thiết lập các tùy chọn cơ bản.
- Kiểm tra Bucket sau khi tạo.

### 5.5.2 Tạo cấu trúc thư mục

Trong phần này, chúng ta sẽ:

- Tạo các thư mục trong Bucket.
- Chuẩn bị nơi lưu trữ dữ liệu.
- Kiểm tra cấu trúc thư mục.

### 5.5.3 Cấu hình S3 Gateway Endpoint

Trong phần này, chúng ta sẽ:

- Tạo S3 Gateway Endpoint.
- Liên kết Endpoint với Route Table.
- Cho phép EC2 truy cập Amazon S3 thông qua mạng nội bộ AWS.
- Kiểm tra kết nối giữa EC2 và Amazon S3.

---

## Kết quả mong đợi

Sau khi hoàn thành Lab 3:

- Amazon S3 Bucket đã được tạo thành công.
- Cấu trúc thư mục trong Bucket đã được thiết lập.
- S3 Gateway Endpoint đã được cấu hình.
- EC2 có thể truy cập Amazon S3 mà không cần Internet.
- Hệ thống đã có môi trường lưu trữ dữ liệu an toàn và hiệu quả.

Sau khi hoàn thành Lab 3, hệ thống sẽ sẵn sàng cho **Lab 4 – CloudWatch Monitoring**.