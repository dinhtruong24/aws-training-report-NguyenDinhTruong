---
title : "Cấu hình VPC"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b>5.3.1. </b> "
---

Trong phần này, chúng ta sẽ tạo một **Amazon Virtual Private Cloud (VPC)** làm nền tảng mạng riêng cho toàn bộ hệ thống quản lý giao hàng trên AWS.

VPC sử dụng dải địa chỉ IPv4 `10.0.0.0/16`, cung cấp không gian địa chỉ đủ lớn để phân chia thành các Public Subnets, Private Application Subnets và Private Database Subnets trong các bước tiếp theo.

---

## Bước 1. Tạo Amazon VPC

Đăng nhập vào **AWS Management Console** và kiểm tra Region hiện tại là:

```text
Asia Pacific (Singapore) – ap-southeast-1
```

Tìm kiếm và mở dịch vụ **VPC**, sau đó thực hiện:

1. Chọn **Your VPCs** trong menu bên trái.
2. Chọn **Create VPC**.
3. Chọn tùy chọn **VPC only**.
4. Nhập Name tag:

```text
delivery-dev-vpc
```

5. Nhập IPv4 CIDR:

```text
10.0.0.0/16
```

6. Giữ nguyên các cấu hình còn lại và chọn **Create VPC**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.1-create-vpc.png" width="900">
</p>

<p align="center">
<i>Hình 5.3.2. Tạo VPC và khai báo dải CIDR 10.0.0.0/16.</i>
</p>

---

## Bước 2. Kiểm tra VPC

Sau khi quá trình tạo hoàn tất, quay lại danh sách **Your VPCs** và chọn VPC vừa tạo.

Kiểm tra các thông tin sau:

- **Name:** `delivery-dev-vpc`
- **IPv4 CIDR:** `10.0.0.0/16`
- **State:** `Available`
- **Region:** `ap-southeast-1`

Ghi lại **VPC ID** để sử dụng khi tạo Subnet, Route Table, Internet Gateway và các tài nguyên mạng khác.

Tiếp theo, chọn **Actions** và mở phần **Edit VPC settings** để cấu hình thuộc tính DNS.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.1-verify-vpc.png" width="900">
</p>

<p align="center">
<i>Hình 5.3.3. Kiểm tra VPC và mở phần chỉnh sửa thuộc tính DNS.</i>
</p>

---

## Bước 3. Bật DNS Resolution và DNS Hostnames

Trong phần cấu hình DNS của VPC, bật hai tùy chọn:

```text
Enable DNS resolution
Enable DNS hostnames
```

Sau đó chọn **Save changes** để lưu cấu hình.

- **DNS Resolution** cho phép các tài nguyên trong VPC phân giải tên miền thông qua DNS do AWS cung cấp.
- **DNS Hostnames** cho phép các EC2 Instance nhận DNS hostname khi đáp ứng điều kiện cấu hình mạng.

Hai thuộc tính này cần thiết để các tài nguyên trong hệ thống có thể giao tiếp với nhau và truy cập các dịch vụ AWS bằng tên miền thay vì chỉ sử dụng địa chỉ IP.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.1-enable-dns.png" width="900">
</p>

<p align="center">
<i>Hình 5.3.4. Bật DNS Resolution và DNS Hostnames cho VPC.</i>
</p>

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Tạo thành công VPC `delivery-dev-vpc`.
- Cấu hình dải IPv4 CIDR `10.0.0.0/16`.
- Xác nhận VPC ở trạng thái `Available`.
- Ghi nhận VPC ID để sử dụng trong các bước tiếp theo.
- Bật DNS Resolution.
- Bật DNS Hostnames.

VPC hiện đã sẵn sàng để phân chia thành các lớp mạng khác nhau.

Trong phần tiếp theo, chúng ta sẽ thực hiện **5.3.2 – Tạo các Subnet** trên hai Availability Zones.