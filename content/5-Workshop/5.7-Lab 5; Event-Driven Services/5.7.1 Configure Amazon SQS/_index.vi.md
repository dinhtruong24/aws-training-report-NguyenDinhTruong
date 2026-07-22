---
title : "Tạo Backup Vault"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b>5.7.1. </b> "
---

Trong phần này, chúng ta sẽ tạo một **Backup Vault** để lưu trữ các bản sao lưu được tạo bởi AWS Backup.

Backup Vault là nơi lưu trữ tập trung các **Recovery Points** của các tài nguyên AWS. Việc sử dụng Backup Vault giúp quản lý dữ liệu sao lưu một cách an toàn, dễ dàng theo dõi và hỗ trợ quá trình khôi phục dữ liệu khi cần thiết.

---

## Bước 1. Mở dịch vụ AWS Backup

Đăng nhập vào **AWS Management Console**.

Thực hiện các bước sau:

1. Tìm kiếm dịch vụ **AWS Backup**.
2. Chọn **AWS Backup**.
3. Mở giao diện quản lý của AWS Backup.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.7-lab5/5.7.1-open-aws-backup.png" width="900">
</p>

<p align="center">
<i>Hình 5.7.2. Mở dịch vụ AWS Backup.</i>
</p>

---

## Bước 2. Tạo Backup Vault

Trong bảng điều khiển AWS Backup:

1. Chọn **Backup vaults**.
2. Chọn **Create Backup vault**.
3. Nhập tên Backup Vault.

Ví dụ:

```text
delivery-backup-vault
```

Sau đó chọn **Create Backup vault** để hoàn tất.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.7-lab5/5.7.1-create-backup-vault.png" width="900">
</p>

<p align="center">
<i>Hình 5.7.3. Tạo Backup Vault.</i>
</p>

---

## Bước 3. Kiểm tra Backup Vault

Sau khi tạo thành công:

- Mở danh sách **Backup Vaults**.
- Xác nhận Backup Vault đã xuất hiện.
- Kiểm tra trạng thái của Backup Vault.
- Xác nhận Vault sẵn sàng lưu trữ các Recovery Points.

Backup Vault sẽ được sử dụng trong các phần tiếp theo để lưu trữ dữ liệu sao lưu của hệ thống.

---

## Bảng cấu hình

| Thuộc tính | Giá trị |
|---|---|
| AWS Service | AWS Backup |
| Resource | Backup Vault |
| Vault Name | `delivery-backup-vault` |
| Encryption | AWS Managed Key |
| Status | Available |

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Truy cập thành công dịch vụ AWS Backup.
- Tạo thành công Backup Vault.
- Kiểm tra trạng thái của Backup Vault.
- Chuẩn bị môi trường lưu trữ các bản sao lưu.

Tiếp theo, chúng ta sẽ thực hiện **5.7.2 – Tạo Backup Plan**.