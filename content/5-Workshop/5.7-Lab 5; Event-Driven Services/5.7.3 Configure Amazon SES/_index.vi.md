---
title : "Thực hiện và kiểm tra Backup Jobs"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b>5.7.3. </b> "
---

Trong phần này, chúng ta sẽ thực hiện **Backup Job** và kiểm tra kết quả sao lưu bằng AWS Backup.

Backup Job là quá trình AWS Backup tạo bản sao lưu của các tài nguyên đã được gán vào Backup Plan. Sau khi hoàn thành, các bản sao lưu sẽ được lưu dưới dạng **Recovery Points** trong Backup Vault và sẵn sàng cho việc khôi phục dữ liệu khi cần.

---

## Bước 1. Thực hiện Backup Job

Đăng nhập vào **AWS Management Console**.

Thực hiện các bước sau:

1. Mở dịch vụ **AWS Backup**.
2. Chọn **Protected resources** hoặc **Backup plans**.
3. Chọn tài nguyên cần sao lưu.
4. Chọn **Create on-demand backup** hoặc khởi chạy Backup Job theo kế hoạch đã cấu hình.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.7-lab5/5.7.3-start-backup-job.png" width="900">
</p>

<p align="center">
<i>Hình 5.7.7. Thực hiện Backup Job.</i>
</p>

---

## Bước 2. Kiểm tra Backup Jobs

Sau khi Backup Job được tạo:

1. Chọn **Backup jobs**.
2. Kiểm tra trạng thái của Backup Job.
3. Xác nhận quá trình sao lưu đã hoàn tất.

Trạng thái của Backup Job có thể là:

- Running
- Completed
- Failed

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.7-lab5/5.7.3-view-backup-jobs.png" width="900">
</p>

<p align="center">
<i>Hình 5.7.8. Kiểm tra trạng thái Backup Jobs.</i>
</p>

---

## Bước 3. Xác nhận kết quả sao lưu

Sau khi Backup Job hoàn thành:

- Mở **Backup Vault**.
- Kiểm tra các **Recovery Points** đã được tạo.
- Xác nhận dữ liệu sao lưu được lưu thành công.
- Kiểm tra thời gian tạo và trạng thái của bản sao lưu.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.7-lab5/5.7.3-verify-backup-results.png" width="900">
</p>

<p align="center">
<i>Hình 5.7.9. Xác nhận kết quả sao lưu.</i>
</p>

---

## Bảng thông tin

| Thành phần | Mô tả |
|---|---|
| AWS Service | AWS Backup |
| Backup Job | Tác vụ sao lưu |
| Backup Vault | Nơi lưu Recovery Points |
| Recovery Point | Bản sao lưu của tài nguyên |
| Status | Running / Completed / Failed |

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Thực hiện thành công Backup Job.
- Theo dõi trạng thái của Backup Job.
- Kiểm tra các Recovery Points trong Backup Vault.
- Xác nhận dữ liệu đã được sao lưu thành công.
- Hoàn thành Lab 5 về sao lưu dữ liệu bằng AWS Backup.

Sau khi hoàn thành Lab 5, hệ thống đã có giải pháp sao lưu tập trung và sẵn sàng cho việc khôi phục dữ liệu khi cần thiết.