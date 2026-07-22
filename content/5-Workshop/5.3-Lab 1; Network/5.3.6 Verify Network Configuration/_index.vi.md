---
title : "Kiểm tra cấu hình mạng"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b>5.3.6. </b> "
---

Trong phần này, chúng ta sẽ kiểm tra toàn bộ cấu hình mạng đã triển khai trong Lab 1, bao gồm VPC, Subnets, Internet Gateway, Route Tables và NAT Gateway.

Mục tiêu của bước kiểm tra là bảo đảm mỗi lớp mạng được cấu hình đúng chức năng, các Public Subnets có thể kết nối Internet và các Private Subnets vẫn được bảo vệ khỏi truy cập trực tiếp từ bên ngoài.

---

## Bước 1. Kiểm tra Public Route Table

Mở dịch vụ **VPC**, chọn **Route Tables** và mở:

```text
delivery-public-rt
```

Kiểm tra tab **Routes** và xác nhận có hai Route sau:

```text
10.0.0.0/16 → local
0.0.0.0/0 → delivery-dev-igw
```

Trong đó:

- Local Route cho phép các tài nguyên trong VPC giao tiếp nội bộ.
- Default Route `0.0.0.0/0` chuyển lưu lượng Internet đến Internet Gateway.

Tiếp theo, mở tab **Subnet associations** và xác nhận hai Public Subnets được liên kết:

```text
delivery-public-a
delivery-public-b
```

---

## Bước 2. Kiểm tra Application Route Table

Mở Route Table:

```text
delivery-app-rt
```

Kiểm tra tab **Routes** và xác nhận có:

```text
10.0.0.0/16 → local
0.0.0.0/0 → delivery-nat-a
```

Default Route qua NAT Gateway cho phép các tài nguyên trong Private Application Subnets truy cập Internet theo chiều outbound mà không cần Public IP.

Trong tab **Subnet associations**, xác nhận hai Application Subnets:

```text
delivery-app-a
delivery-app-b
```

đã được associate với `delivery-app-rt`.

---

## Bước 3. Kiểm tra Database Route Table

Mở Route Table:

```text
delivery-db-rt
```

Kiểm tra và xác nhận Route Table chỉ có Local Route:

```text
10.0.0.0/16 → local
```

Không được có:

```text
0.0.0.0/0 → Internet Gateway
```

hoặc:

```text
0.0.0.0/0 → NAT Gateway
```

Trong tab **Subnet associations**, xác nhận hai Database Subnets:

```text
delivery-db-a
delivery-db-b
```

đã được associate với `delivery-db-rt`.

Việc không cấu hình đường Internet cho Database Subnets giúp bảo vệ tầng cơ sở dữ liệu khỏi truy cập trực tiếp từ bên ngoài.

---

## Bước 4. Kiểm tra cấu hình Public IPv4 của các Subnet

Mở danh sách **Subnets** và kiểm tra thuộc tính tự động gán Public IPv4.

Hai Public Subnets phải có:

```text
Auto-assign public IPv4 address: Enabled
```

Áp dụng cho:

```text
delivery-public-a
delivery-public-b
```

Bốn Private Subnets phải có:

```text
Auto-assign public IPv4 address: Disabled
```

Áp dụng cho:

```text
delivery-app-a
delivery-app-b
delivery-db-a
delivery-db-b
```

---

## Bước 5. Kiểm tra trạng thái tài nguyên

Xác nhận các tài nguyên mạng có trạng thái hoạt động phù hợp:

| Tài nguyên | Trạng thái mong đợi |
|---|---|
| `delivery-dev-vpc` | `Available` |
| Sáu Subnets | `Available` |
| `delivery-dev-igw` | `Attached` |
| `delivery-nat-a` | `Available` |
| `delivery-public-rt` | Có Route qua Internet Gateway |
| `delivery-app-rt` | Có Route qua NAT Gateway |
| `delivery-db-rt` | Chỉ có Local Route |

---

## Bảng kiểm tra cuối cùng

| Thành phần | Kết quả mong đợi |
|---|---|
| Public Route Table | Có Local Route và `0.0.0.0/0 → Internet Gateway` |
| Application Route Table | Có Local Route và `0.0.0.0/0 → NAT Gateway` |
| Database Route Table | Chỉ có Local Route |
| Public Subnets | Auto-assign Public IPv4 = Enabled |
| Application Subnets | Auto-assign Public IPv4 = Disabled |
| Database Subnets | Auto-assign Public IPv4 = Disabled |

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Kiểm tra cấu hình Public Route Table.
- Kiểm tra cấu hình Application Route Table.
- Kiểm tra cấu hình Database Route Table.
- Xác nhận Public Subnets có khả năng kết nối Internet.
- Xác nhận Private Application Subnets sử dụng NAT Gateway.
- Xác nhận Private Database Subnets không có đường Internet trực tiếp.
- Kiểm tra cấu hình tự động gán Public IPv4 của sáu Subnets.
- Hoàn thành việc kiểm thử toàn bộ hạ tầng mạng trong Lab 1.

Sau khi hoàn thành **5.3.6**, Lab 1 đã được triển khai và kiểm tra đầy đủ. Hạ tầng mạng hiện sẵn sàng cho **Lab 2 – Security Groups và IAM**.