---
title : "Tạo các Subnet"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b>5.3.2. </b> "
---

Trong phần này, chúng ta sẽ chia VPC `delivery-dev-vpc` thành sáu Subnet được phân bố trên hai Availability Zones.

Kiến trúc mạng gồm ba lớp:

- **Public Subnets:** Dành cho các tài nguyên cần kết nối trực tiếp với Internet, chẳng hạn như Application Load Balancer và NAT Gateway.
- **Private Application Subnets:** Dành cho các EC2 Instance hoặc dịch vụ ứng dụng.
- **Private Database Subnets:** Dành cho Amazon RDS và các tài nguyên cơ sở dữ liệu.

Việc phân bố các Subnet trên hai Availability Zones giúp cải thiện tính sẵn sàng và khả năng chịu lỗi của hệ thống.

---

## Bước 1. Chuẩn bị kế hoạch địa chỉ mạng

Các Subnet được tạo theo bảng sau:

| Tên Subnet | Availability Zone | IPv4 CIDR | Tự động gán Public IPv4 |
|---|---|---|---|
| `delivery-public-a` | `ap-southeast-1a` | `10.0.1.0/24` | Bật |
| `delivery-public-b` | `ap-southeast-1b` | `10.0.2.0/24` | Bật |
| `delivery-app-a` | `ap-southeast-1a` | `10.0.11.0/24` | Tắt |
| `delivery-app-b` | `ap-southeast-1b` | `10.0.12.0/24` | Tắt |
| `delivery-db-a` | `ap-southeast-1a` | `10.0.21.0/24` | Tắt |
| `delivery-db-b` | `ap-southeast-1b` | `10.0.22.0/24` | Tắt |

Các dải CIDR không được trùng nhau và phải nằm trong dải CIDR của VPC:

```text
10.0.0.0/16
```

---

## Bước 2. Tạo các Subnet

Trong **AWS Management Console**, mở dịch vụ **VPC** và thực hiện:

1. Chọn **Subnets** trong menu bên trái.
2. Chọn **Create subnet**.
3. Trong phần **VPC ID**, chọn:

```text
delivery-dev-vpc
```

4. Nhập tên Subnet.
5. Chọn Availability Zone tương ứng.
6. Nhập IPv4 CIDR theo bảng kế hoạch.
7. Chọn **Add new subnet** để tiếp tục khai báo Subnet tiếp theo.
8. Sau khi nhập đủ sáu Subnet, chọn **Create subnet**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.2-create-subnets.png" width="900">
</p>

<p align="center">
<i>Hình 5.3.5. Khởi tạo các Subnet và chọn delivery-dev-vpc.</i>
</p>

---

## Bước 3. Cấu hình tự động gán Public IPv4

Sau khi tạo thành công sáu Subnet, bật tính năng tự động gán Public IPv4 cho hai Public Subnets.

Thực hiện lần lượt với:

```text
delivery-public-a
delivery-public-b
```

Các bước thực hiện:

1. Chọn Public Subnet cần cấu hình.
2. Chọn **Actions**.
3. Chọn **Edit subnet settings**.
4. Bật tùy chọn:

```text
Enable auto-assign public IPv4 address
```

5. Chọn **Save**.

Không bật tùy chọn này đối với:

```text
delivery-app-a
delivery-app-b
delivery-db-a
delivery-db-b
```

Các Application Subnets và Database Subnets phải được giữ ở chế độ Private để hạn chế khả năng truy cập trực tiếp từ Internet.

---

## Bước 4. Kiểm tra các Subnet

Sau khi hoàn tất cấu hình, kiểm tra danh sách Subnet và xác nhận:

- Có đủ sáu Subnet.
- Tất cả Subnet có trạng thái `Available`.
- Các Subnet được phân bố trên hai Availability Zones.
- Hai Public Subnets bật tự động gán Public IPv4.
- Application Subnets và Database Subnets không tự động gán Public IPv4.
- Mỗi Subnet sử dụng đúng IPv4 CIDR đã thiết kế.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.2-verify-subnets.png" width="900">
</p>

<p align="center">
<i>Hình 5.3.6. Kiểm tra sáu Subnet và cấu hình Public IPv4.</i>
</p>

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Tạo thành công hai Public Subnets.
- Tạo thành công hai Private Application Subnets.
- Tạo thành công hai Private Database Subnets.
- Phân bố các Subnet trên hai Availability Zones.
- Bật tự động gán Public IPv4 cho hai Public Subnets.
- Giữ các Application Subnets và Database Subnets ở chế độ Private.
- Xác nhận toàn bộ sáu Subnet ở trạng thái `Available`.

Trong phần tiếp theo, chúng ta sẽ thực hiện **5.3.3 – Cấu hình Internet Gateway** để cung cấp kết nối Internet cho các Public Subnets.