---
title : "Tạo Backup Plan"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b>5.7.2. </b> "
---

Trong phần này, chúng ta sẽ tạo một **Backup Plan** để xác định cách thức AWS Backup thực hiện sao lưu các tài nguyên của hệ thống.

Backup Plan bao gồm các **Backup Rules**, lịch sao lưu, thời gian lưu trữ (Retention Period) và các tài nguyên được chỉ định để sao lưu. Việc cấu hình Backup Plan giúp tự động hóa quá trình bảo vệ dữ liệu và đảm bảo các bản sao lưu được tạo theo đúng chính sách đã thiết lập.

---

## Bước 1. Tạo Backup Plan

Đăng nhập vào **AWS Management Console**.

Thực hiện các bước sau:

1. Mở dịch vụ **AWS Backup**.
2. Chọn **Backup plans**.
3. Chọn **Create Backup plan**.
4. Chọn phương thức tạo Backup Plan.
5. Nhập tên Backup Plan.

Ví dụ:

```text
delivery-backup-plan
```

Sau khi hoàn tất, chọn **Create plan**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.7-lab5/5.7.2-create-backup-plan.png" width="900">
</p>

<p align="center">
<i>Hình 5.7.4. Tạo Backup Plan.</i>
</p>

---

## Bước 2. Cấu hình Backup Rule

Sau khi tạo Backup Plan:

1. Chọn **Add backup rule**.
2. Đặt tên cho Backup Rule.
3. Chọn Backup Vault đã tạo.
4. Thiết lập lịch sao lưu.
5. Thiết lập thời gian lưu trữ bản sao lưu.

Sau khi hoàn tất, chọn **Save**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.7-lab5/5.7.2-configure-backup-rule.png" width="900">
</p>

<p align="center">
<i>Hình 5.7.5. Cấu hình Backup Rule.</i>
</p>

---

## Bước 3. Gán tài nguyên vào Backup Plan

Sau khi Backup Plan được tạo:

1. Chọn **Assign resources**.
2. Chọn Role thích hợp.
3. Chọn các tài nguyên cần sao lưu.
4. Lưu cấu hình.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.7-lab5/5.7.2-assign-resources.png" width="900">
</p>

<p align="center">
<i>Hình 5.7.6. Gán tài nguyên vào Backup Plan.</i>
</p>

---

## Bảng cấu hình

| Thuộc tính | Giá trị |
|---|---|
| AWS Service | AWS Backup |
| Resource | Backup Plan |
| Backup Rule | Daily Backup |
| Backup Vault | `delivery-backup-vault` |
| Status | Active |

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Tạo thành công Backup Plan.
- Cấu hình Backup Rule.
- Thiết lập lịch sao lưu.
- Gán các tài nguyên cần sao lưu.
- Chuẩn bị môi trường để thực hiện Backup Job.

Tiếp theo, chúng ta sẽ thực hiện **5.7.3 – Thực hiện và kiểm tra Backup Jobs**.