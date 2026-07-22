---
title : "Tạo Amazon S3 Bucket"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b>5.3.1. </b> "
---

# TẠO AMAZON S3 BUCKET

Trong phần này, chúng ta sẽ tạo một **Amazon S3 Bucket** để lưu trữ các tài liệu PDF của hệ thống **VietAI Scholar Assistant**. Bucket sẽ là nơi lưu trữ dữ liệu đầu vào, dữ liệu đã xử lý và kết quả sinh ra từ các dịch vụ AI trong các bước tiếp theo.

---

## Bước 1. Tạo Amazon S3 Bucket

Đăng nhập vào **AWS Management Console**, tìm kiếm dịch vụ **Amazon S3** và chọn **Create bucket**.

Nhập tên Bucket theo quy tắc đặt tên của Amazon S3, chọn **Region: Asia Pacific (Singapore) – ap-southeast-1**, giữ nguyên các thiết lập mặc định về **Object Ownership**, **Block Public Access** và **Default Encryption**, sau đó nhấn **Create bucket** để hoàn tất quá trình tạo Bucket.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.1-create-s3-bucket.png" width="900">
</p>

<p align="center">
<i>Hình 5.3.1. Tạo Amazon S3 Bucket trên AWS Management Console.</i>
</p>

---

## Bước 2. Tạo cấu trúc lưu trữ tài liệu

Sau khi Bucket được tạo thành công, mở Bucket vừa tạo và chọn **Create folder** để tạo các thư mục phục vụ cho hệ thống.

Đối với dự án **VietAI Scholar Assistant**, tạo ba thư mục sau:

```text
uploads/
processed/
outputs/
```

Trong đó:

- **uploads/**: Lưu các tài liệu PDF được người dùng tải lên.
- **processed/**: Lưu dữ liệu sau khi OCR hoặc các bước tiền xử lý hoàn tất.
- **outputs/**: Lưu kết quả cuối cùng như bản tóm tắt, bản dịch và nội dung được AI sinh ra.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.1-create-folder.png" width="900">
</p>

<p align="center">
<i>Hình 5.3.2. Tạo các thư mục logic trong Amazon S3 Bucket.</i>
</p>

---

## Kết quả đạt được

Sau khi hoàn thành bước này, hệ thống đã có một **Amazon S3 Bucket** được cấu hình đúng Region cùng với cấu trúc lưu trữ tài liệu ban đầu. Đây sẽ là nền tảng để các dịch vụ AI truy cập và xử lý dữ liệu trong các Lab tiếp theo.

Tiếp theo, chúng ta sẽ thực hiện **5.3.2 – Configure Document Upload** để cấu hình quy trình tải tài liệu từ ứng dụng lên Amazon S3.