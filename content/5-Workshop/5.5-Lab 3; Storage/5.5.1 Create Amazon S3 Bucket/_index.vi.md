---
title : "Tạo Amazon S3 Bucket"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b>5.5.1. </b> "
---

Trong phần này, chúng ta sẽ tạo một **Amazon S3 Bucket** để lưu trữ dữ liệu của hệ thống.

Amazon S3 Bucket sẽ đóng vai trò là nơi lưu trữ tập trung cho các tài liệu, hình ảnh và các tệp được tải lên từ ứng dụng. Bucket được cấu hình trong cùng AWS Region với các tài nguyên khác nhằm giảm độ trễ khi truy cập và tối ưu hiệu năng.

---

## Bước 1. Mở dịch vụ Amazon S3

Đăng nhập vào **AWS Management Console**.

Thực hiện các bước sau:

1. Tìm kiếm dịch vụ **Amazon S3**.
2. Chọn **Buckets**.
3. Chọn **Create bucket**.

---

## Bước 2. Cấu hình Bucket

Trong màn hình **Create bucket**, nhập các thông tin sau:

**Bucket name**

```text
delivery-dev-storage
```

**AWS Region**

```text
Asia Pacific (Singapore) ap-southeast-1
```

Giữ nguyên các thiết lập mặc định cho:

- Object Ownership
- Block Public Access
- Bucket Versioning
- Default Encryption

Sau khi hoàn tất, chọn **Create bucket**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.5-lab3/5.5.1-create-s3-bucket.png" width="900">
</p>

<p align="center">
<i>Hình 5.5.2. Tạo Amazon S3 Bucket.</i>
</p>

---

## Bước 3. Kiểm tra Bucket

Sau khi Bucket được tạo thành công:

- Mở danh sách **Buckets**.
- Xác nhận Bucket mới đã xuất hiện.
- Kiểm tra Region của Bucket.
- Kiểm tra trạng thái Bucket.

Bucket sẽ được sử dụng trong các bước tiếp theo để lưu trữ dữ liệu của hệ thống.

---

## Bảng cấu hình

| Thuộc tính | Giá trị |
|---|---|
| Service | Amazon S3 |
| Bucket Name | `delivery-dev-storage` |
| Region | Asia Pacific (Singapore) |
| Versioning | Disabled |
| Block Public Access | Enabled |
| Encryption | AWS Managed Keys (SSE-S3) |

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Tạo thành công Amazon S3 Bucket.
- Cấu hình Bucket trong Region phù hợp.
- Giữ nguyên các thiết lập bảo mật mặc định.
- Chuẩn bị môi trường lưu trữ dữ liệu cho ứng dụng.
- Sẵn sàng tạo cấu trúc thư mục trong phần tiếp theo.

Tiếp theo, chúng ta sẽ thực hiện **5.5.2 – Tạo cấu trúc thư mục trong Amazon S3 Bucket**.