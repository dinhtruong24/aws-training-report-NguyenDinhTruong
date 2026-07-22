---
title : "Cấu hình Route Tables"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b>5.3.4. </b> "
---

Trong phần này, chúng ta sẽ tạo và cấu hình các **Route Tables** cho ba lớp mạng của hệ thống:

- Public Subnets
- Private Application Subnets
- Private Database Subnets

Mỗi lớp mạng sử dụng Route Table riêng để kiểm soát luồng lưu lượng và đảm bảo các tài nguyên được đặt đúng tầng mạng.

---

## Bước 1. Tạo Public Route Table

Trong **AWS Management Console**, mở dịch vụ **VPC** và thực hiện:

1. Chọn **Route Tables** trong menu bên trái.
2. Chọn **Create route table**.
3. Nhập Name tag:

```text
delivery-public-rt
```

4. Trong phần **VPC**, chọn:

```text
delivery-dev-vpc
```

5. Chọn **Create route table**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.4-create-public-route-table.png" width="900">
</p>

<p align="center">
<i>Hình 5.3.9. Tạo Public Route Table delivery-public-rt.</i>
</p>

---

## Bước 2. Thêm Default Route qua Internet Gateway

Mở Route Table `delivery-public-rt`, chọn tab **Routes** và thực hiện:

1. Chọn **Edit routes**.
2. Chọn **Add route**.
3. Nhập Destination:

```text
0.0.0.0/0
```

4. Trong phần Target, chọn **Internet Gateway**.
5. Chọn:

```text
delivery-dev-igw
```

6. Chọn **Save changes**.

Route này cho phép các tài nguyên trong Public Subnets truy cập Internet thông qua Internet Gateway.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.4-configure-public-route.png" width="900">
</p>

<p align="center">
<i>Hình 5.3.10. Thêm Default Route 0.0.0.0/0 qua Internet Gateway.</i>
</p>

---

## Bước 3. Associate Public Subnets

Trong Route Table `delivery-public-rt`, chọn tab **Subnet associations** và thực hiện:

1. Chọn **Edit subnet associations**.
2. Chọn hai Public Subnets:

```text
delivery-public-a
delivery-public-b
```

3. Chọn **Save associations**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.4-associate-public-subnets.png" width="900">
</p>

<p align="center">
<i>Hình 5.3.11. Associate hai Public Subnets với Public Route Table.</i>
</p>

Sau khi lưu, kiểm tra và xác nhận hai Public Subnets đã được liên kết đúng với `delivery-public-rt`.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.4-verify-public-route-table.png" width="900">
</p>

<p align="center">
<i>Hình 5.3.12. Xác nhận Public Subnet Associations.</i>
</p>

---

## Bước 4. Tạo Private Application Route Table

Tiếp tục tạo Route Table cho các Private Application Subnets.

1. Chọn **Create route table**.
2. Nhập Name tag:

```text
delivery-app-rt
```

3. Chọn VPC:

```text
delivery-dev-vpc
```

4. Chọn **Create route table**.
5. Mở tab **Subnet associations**.
6. Associate hai Application Subnets:

```text
delivery-app-a
delivery-app-b
```

Route Table này sẽ được cấu hình thêm Default Route qua NAT Gateway trong phần 5.3.5.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.4-create-private-route-table.png" width="900">
</p>

<p align="center">
<i>Hình 5.3.13. Tạo delivery-app-rt và associate hai Application Subnets.</i>
</p>

Kiểm tra Route Table và xác nhận hiện tại chỉ có Local Route trước khi thêm NAT Route.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.4-verify-private-route-table.png" width="900">
</p>

<p align="center">
<i>Hình 5.3.14. Kiểm tra Application Route Table trước khi thêm NAT Route.</i>
</p>

---

## Bước 5. Tạo Database Route Table

Tạo Route Table riêng cho các Private Database Subnets.

1. Chọn **Create route table**.
2. Nhập Name tag:

```text
delivery-db-rt
```

3. Chọn VPC:

```text
delivery-dev-vpc
```

4. Chọn **Create route table**.
5. Mở tab **Subnet associations**.
6. Associate hai Database Subnets:

```text
delivery-db-a
delivery-db-b
```

Database Route Table chỉ sử dụng Local Route. Không thêm Internet Gateway hoặc NAT Gateway để hạn chế kết nối Internet trực tiếp đến tầng cơ sở dữ liệu.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.4-create-database-route-table.png" width="900">
</p>

<p align="center">
<i>Hình 5.3.15. Tạo delivery-db-rt và associate các Database Subnets.</i>
</p>

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.4-associate-database-subnets.png" width="900">
</p>

<p align="center">
<i>Hình 5.3.16. Xác nhận Database Subnet Associations.</i>
</p>

---

## Bước 6. Kiểm tra Route Tables

Sau khi hoàn tất, kiểm tra các cấu hình sau:

| Route Table | Subnets | Routes |
|---|---|---|
| `delivery-public-rt` | `delivery-public-a`, `delivery-public-b` | Local và `0.0.0.0/0 → delivery-dev-igw` |
| `delivery-app-rt` | `delivery-app-a`, `delivery-app-b` | Local; NAT Route sẽ được thêm ở phần tiếp theo |
| `delivery-db-rt` | `delivery-db-a`, `delivery-db-b` | Chỉ Local Route |

Đảm bảo mỗi Subnet chỉ được associate với Route Table phù hợp với tầng mạng của nó.

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Tạo Public Route Table `delivery-public-rt`.
- Thêm Default Route qua Internet Gateway.
- Associate hai Public Subnets với Public Route Table.
- Tạo Private Application Route Table `delivery-app-rt`.
- Associate hai Application Subnets với Application Route Table.
- Tạo Database Route Table `delivery-db-rt`.
- Associate hai Database Subnets với Database Route Table.
- Giữ Database Route Table chỉ có Local Route.

Trong phần tiếp theo, chúng ta sẽ thực hiện **5.3.5 – Tạo NAT Gateway** và thêm Default Route cho các Private Application Subnets.