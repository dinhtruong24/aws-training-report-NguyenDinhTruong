---
title : "Tạo NAT Gateway"
date : 2024-01-01
weight : 5
chapter : false
pre : " <b>5.3.5. </b> "
---

Trong phần này, chúng ta sẽ tạo một **NAT Gateway** để các tài nguyên trong Private Application Subnets có thể truy cập Internet theo chiều đi ra ngoài mà không cần gán Public IP trực tiếp.

NAT Gateway sẽ được đặt trong Public Subnet `delivery-public-a` và sử dụng một Elastic IP. Sau đó, Route Table `delivery-app-rt` sẽ được cập nhật để chuyển lưu lượng Internet từ các Application Subnets qua NAT Gateway.

---

## Bước 1. Tạo NAT Gateway

Trong **AWS Management Console**, mở dịch vụ **VPC** và thực hiện các bước sau:

1. Chọn **NAT Gateways** trong menu bên trái.
2. Chọn **Create NAT gateway**.
3. Nhập Name tag:

```text
delivery-nat-a
```

4. Trong phần **Subnet**, chọn:

```text
delivery-public-a
```

5. Trong phần **Connectivity type**, chọn:

```text
Public
```

6. Chọn **Allocate Elastic IP** để cấp một Elastic IP mới.
7. Chọn **Create NAT gateway**.

NAT Gateway phải được đặt trong Public Subnet vì cần sử dụng Internet Gateway để chuyển tiếp lưu lượng ra Internet.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.5-create-nat-gateway.png" width="900">
</p>

<p align="center">
<i>Hình 5.3.17. Tạo NAT Gateway delivery-nat-a trong Public Subnet delivery-public-a.</i>
</p>

---

## Bước 2. Chờ NAT Gateway sẵn sàng

Sau khi tạo NAT Gateway, kiểm tra trạng thái của tài nguyên.

Chờ đến khi trạng thái chuyển thành:

```text
Available
```

Đồng thời kiểm tra các thông tin sau:

- **Name:** `delivery-nat-a`
- **Subnet:** `delivery-public-a`
- **Connectivity type:** `Public`
- **Elastic IP:** Đã được cấp
- **State:** `Available`

Không cấu hình Route Table trước khi NAT Gateway ở trạng thái `Available`.

---

## Bước 3. Cập nhật Application Route Table

Mở Route Table:

```text
delivery-app-rt
```

Sau đó thực hiện:

1. Chọn tab **Routes**.
2. Chọn **Edit routes**.
3. Chọn **Add route**.
4. Nhập Destination:

```text
0.0.0.0/0
```

5. Trong phần **Target**, chọn **NAT Gateway**.
6. Chọn NAT Gateway:

```text
delivery-nat-a
```

7. Chọn **Save changes**.

Route Table của Application Subnets sau khi cấu hình phải gồm:

```text
10.0.0.0/16 → local
0.0.0.0/0 → delivery-nat-a
```

Route này cho phép các EC2 Instance trong Private Application Subnets tải package, cập nhật phần mềm hoặc truy cập các dịch vụ bên ngoài mà không cần Public IP.

---

## Bước 4. Giữ Database Route Table ở chế độ riêng tư

Không thêm NAT Gateway route vào Route Table:

```text
delivery-db-rt
```

Database Route Table chỉ giữ Local Route:

```text
10.0.0.0/16 → local
```

Việc này giúp tầng cơ sở dữ liệu không có đường truy cập Internet trực tiếp, giảm bề mặt tấn công và bảo vệ Amazon RDS trong Private Database Subnets.

---

## Bước 5. Kiểm tra cấu hình mạng

Sau khi hoàn tất cấu hình NAT Gateway, kiểm tra các Route Tables:

| Route Table | Route mong đợi |
|---|---|
| `delivery-public-rt` | Local và `0.0.0.0/0 → delivery-dev-igw` |
| `delivery-app-rt` | Local và `0.0.0.0/0 → delivery-nat-a` |
| `delivery-db-rt` | Chỉ Local Route |

Đồng thời xác nhận:

- Hai Public Subnets sử dụng `delivery-public-rt`.
- Hai Application Subnets sử dụng `delivery-app-rt`.
- Hai Database Subnets sử dụng `delivery-db-rt`.
- Public Subnets bật tự động gán Public IPv4.
- Application Subnets và Database Subnets không tự động gán Public IPv4.

---

> **Lưu ý chi phí:** NAT Gateway phát sinh chi phí theo thời gian hoạt động và lượng dữ liệu xử lý. Sau khi hoàn thành workshop, nên xóa NAT Gateway và giải phóng Elastic IP nếu không còn sử dụng.

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Tạo NAT Gateway `delivery-nat-a`.
- Đặt NAT Gateway trong Public Subnet `delivery-public-a`.
- Cấp Elastic IP cho NAT Gateway.
- Xác nhận NAT Gateway ở trạng thái `Available`.
- Thêm Default Route từ `delivery-app-rt` đến NAT Gateway.
- Cho phép Private Application Subnets truy cập Internet theo chiều outbound.
- Giữ Database Route Table chỉ có Local Route.
- Hoàn thành nền tảng mạng cho Lab 1.

Sau khi hoàn thành **5.3.5**, Lab 1 đã có đầy đủ VPC, Subnets, Internet Gateway, Route Tables và NAT Gateway để phục vụ các Lab tiếp theo.