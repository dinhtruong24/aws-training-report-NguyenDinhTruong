---
title : "Lab 5: AWS Backup"
date : 2024-01-01
weight : 7
chapter : false
pre : " <b>5.7. </b> "
---

Trong Lab này, chúng ta sẽ sử dụng **AWS Backup** để xây dựng giải pháp sao lưu dữ liệu cho các tài nguyên AWS.

AWS Backup là dịch vụ sao lưu tập trung của AWS, cho phép tạo và quản lý các kế hoạch sao lưu (Backup Plans), thực hiện sao lưu tự động và khôi phục dữ liệu khi cần thiết. Việc sử dụng AWS Backup giúp đơn giản hóa quá trình bảo vệ dữ liệu và đáp ứng các yêu cầu về an toàn thông tin.

Trong Lab này, chúng ta sẽ tạo **Backup Vault**, xây dựng **Backup Plan**, gán tài nguyên cần sao lưu và kiểm tra kết quả sau khi hoàn thành quá trình sao lưu.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.7-lab5/5.7.1-open-aws-backup.png" width="900">
</p>

<p align="center">
<i>Hình 5.7.1. Giao diện dịch vụ AWS Backup.</i>
</p>

---

## Mục tiêu của Lab

Sau khi hoàn thành Lab này, bạn sẽ thực hiện được các nội dung sau:

- Truy cập dịch vụ AWS Backup.
- Tạo Backup Vault.
- Tạo Backup Plan.
- Cấu hình Backup Rule.
- Gán tài nguyên vào Backup Plan.
- Thực hiện Backup Job.
- Kiểm tra trạng thái và kết quả sao lưu.
- Chuẩn bị môi trường để khôi phục dữ liệu khi cần.

---

## Kiến trúc sao lưu

Trong Lab này, AWS Backup sẽ quản lý quá trình sao lưu theo mô hình sau:

```text
AWS Resources
       │
       ▼
AWS Backup
       │
       ├── Backup Vault
       ├── Backup Plan
       ├── Backup Rule
       └── Backup Jobs
```

AWS Backup sẽ tự động thực hiện sao lưu các tài nguyên theo lịch trình đã được cấu hình trong Backup Plan.

---

## Thành phần chính

Lab này sử dụng các thành phần sau:

| Thành phần | Mô tả |
|---|---|
| AWS Backup | Dịch vụ quản lý sao lưu |
| Backup Vault | Nơi lưu trữ các bản sao lưu |
| Backup Plan | Kế hoạch sao lưu |
| Backup Rule | Quy tắc thực hiện sao lưu |
| Backup Jobs | Theo dõi tiến trình sao lưu |

---

## Nội dung của Lab

Lab 5 được chia thành ba phần:

### 5.7.1 Tạo Backup Vault

Trong phần này, chúng ta sẽ:

- Truy cập AWS Backup.
- Tạo Backup Vault.
- Kiểm tra Backup Vault sau khi tạo.

### 5.7.2 Tạo Backup Plan

Trong phần này, chúng ta sẽ:

- Tạo Backup Plan.
- Cấu hình Backup Rule.
- Gán tài nguyên cần sao lưu.
- Kiểm tra cấu hình Backup Plan.

### 5.7.3 Thực hiện và kiểm tra Backup Jobs

Trong phần này, chúng ta sẽ:

- Khởi chạy Backup Job.
- Theo dõi trạng thái Backup Job.
- Kiểm tra kết quả sao lưu.
- Xác nhận dữ liệu đã được lưu trong Backup Vault.

---

## Kết quả mong đợi

Sau khi hoàn thành Lab 5:

- AWS Backup đã được cấu hình thành công.
- Backup Vault đã được tạo.
- Backup Plan và Backup Rule đã được cấu hình.
- Các tài nguyên đã được gán vào Backup Plan.
- Backup Job đã hoàn thành thành công.
- Dữ liệu đã được sao lưu vào Backup Vault.
- Hệ thống đã sẵn sàng cho việc khôi phục dữ liệu khi cần thiết.

Sau khi hoàn thành Lab 5, hệ thống đã có cơ chế sao lưu dữ liệu an toàn và tập trung bằng AWS Backup.