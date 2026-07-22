---
title : "Cấu hình quyền truy cập và kết nối Amazon S3"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b>5.3.2. </b> "
---

# CẤU HÌNH QUYỀN TRUY CẬP VÀ KẾT NỐI AMAZON S3

Trong phần này, chúng ta sẽ cấu hình quyền truy cập Amazon S3 để các thành phần của hệ thống **VietAI Scholar Assistant** có thể lưu trữ và truy xuất tài liệu một cách an toàn. Đồng thời, chúng ta sẽ kiểm tra khả năng kết nối giữa hệ thống và Amazon S3 trước khi thực hiện các bước xử lý tài liệu bằng AI.

---

## Bước 1. Cấu hình quyền truy cập Amazon S3

Sau khi tạo Bucket thành công, tiến hành cấu hình quyền truy cập để ứng dụng có thể đọc và ghi dữ liệu trên Amazon S3. Các quyền cần thiết bao gồm:

- `s3:ListBucket`
- `s3:GetObject`
- `s3:PutObject`
- `s3:DeleteObject`

Các quyền này chỉ được cấp cho Bucket phục vụ dự án nhằm đảm bảo an toàn và tuân thủ nguyên tắc **Least Privilege**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.2%20Configure%20Amazon%20S3%20Access.png" width="900">
</p>

<p align="center">
<i>Hình 5.3.3. Cấu hình quyền truy cập Amazon S3.</i>
</p>

---

## Bước 2. Tải tài liệu lên Amazon S3

Sau khi hoàn tất cấu hình quyền truy cập, mở Bucket đã tạo và chọn **Upload** để tải tài liệu lên hệ thống.

Đối với dự án **VietAI Scholar Assistant**, các tài liệu PDF sẽ được lưu trong thư mục **uploads/** và đóng vai trò là dữ liệu đầu vào cho các bước OCR, RAG và Generative AI ở các phần tiếp theo.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.2%20Upload%20Documents.png" width="900">
</p>

<p align="center">
<i>Hình 5.3.4. Tải tài liệu PDF lên Amazon S3 Bucket.</i>
</p>

---

## Bước 3. Kiểm tra kết nối Amazon S3

Sau khi tài liệu được tải lên thành công, tiến hành kiểm tra khả năng kết nối đến Amazon S3 để đảm bảo hệ thống có thể truy cập và quản lý dữ liệu.

Việc kiểm tra kết nối giúp xác nhận rằng Bucket đã được cấu hình chính xác và sẵn sàng phục vụ cho các dịch vụ AI trong các bước tiếp theo của Workshop.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.2%20Configure%20S3%20Connectivity.png" width="900">
</p>

<p align="center">
<i>Hình 5.3.5. Kiểm tra khả năng kết nối với Amazon S3.</i>
</p>

---

## Kết quả đạt được

Sau khi hoàn thành phần này:

- Amazon S3 đã được cấu hình quyền truy cập phù hợp.
- Bucket có thể lưu trữ và quản lý tài liệu của hệ thống.
- Tài liệu đã được tải lên Amazon S3 thành công.
- Kết nối giữa ứng dụng và Amazon S3 đã được kiểm tra và xác nhận hoạt động ổn định.

Tiếp theo, chúng ta sẽ thực hiện **5.3.3 – Kiểm tra và quản lý dữ liệu lưu trữ trên Amazon S3**.