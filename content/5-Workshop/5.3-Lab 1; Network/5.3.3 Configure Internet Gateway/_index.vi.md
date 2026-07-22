---
title : "Cấu hình Internet Gateway"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b>5.3.3. </b> "
---

Trong phần này, chúng ta sẽ tạo một **Internet Gateway** và gắn nó vào VPC `delivery-dev-vpc`.

Internet Gateway là thành phần cho phép các tài nguyên trong Public Subnets giao tiếp với Internet khi Route Table được cấu hình phù hợp. Đây là bước cần thiết trước khi thiết lập đường định tuyến mặc định cho các Public Subnets.

---

## Bước 1. Tạo Internet Gateway

Đăng nhập vào **AWS Management Console**, mở dịch vụ **VPC** và thực hiện các bước sau:

1. Chọn **Internet Gateways** trong menu bên trái.
2. Chọn **Create internet gateway**.
3. Nhập Name tag:

```text
delivery-dev-igw
```

4. Chọn **Create internet gateway**.

Sau khi tạo thành công, Internet Gateway sẽ xuất hiện trong danh sách tài nguyên với trạng thái chưa được gắn vào VPC.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.3-create-internet-gateway.png" width="900">
</p>

<p align="center">
<i>Hình 5.3.7. Tạo Internet Gateway delivery-dev-igw.</i>
</p>

---

## Bước 2. Gắn Internet Gateway vào VPC

Sau khi Internet Gateway được tạo thành công, tiến hành gắn nó vào VPC.

Thực hiện các bước sau:

1. Chọn Internet Gateway:

```text
delivery-dev-igw
```

2. Chọn **Actions**.
3. Chọn **Attach to a VPC**.
4. Trong phần **Available VPCs**, chọn:

```text
delivery-dev-vpc
```

5. Chọn **Attach internet gateway**.

Internet Gateway sau khi được gắn sẽ trở thành cổng kết nối giữa VPC và Internet.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-document-storage/5.3.3-attach-internet-gateway.png" width="900">
</p>

<p align="center">
<i>Hình 5.3.8. Gắn Internet Gateway vào VPC delivery-dev-vpc.</i>
</p>

---

## Bước 3. Kiểm tra Internet Gateway

Sau khi hoàn tất quá trình gắn Internet Gateway, kiểm tra các thông tin sau:

- **Name:** `delivery-dev-igw`
- **State:** `Attached`
- **VPC:** `delivery-dev-vpc`
- Internet Gateway được tạo trong đúng Region `ap-southeast-1`.

Việc gắn Internet Gateway vào VPC chưa tự động cung cấp kết nối Internet cho các Subnet.

Để Public Subnets có thể truy cập Internet, cần tạo Public Route Table và thêm đường định tuyến:

```text
0.0.0.0/0 → delivery-dev-igw
```

Nội dung này sẽ được thực hiện trong phần tiếp theo.

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Tạo thành công Internet Gateway `delivery-dev-igw`.
- Gắn Internet Gateway vào VPC `delivery-dev-vpc`.
- Xác nhận Internet Gateway ở trạng thái `Attached`.
- Chuẩn bị sẵn cổng kết nối Internet cho Public Subnets.

Trong phần tiếp theo, chúng ta sẽ thực hiện **5.3.4 – Cấu hình Route Tables** để thiết lập đường định tuyến cho Public, Application và Database Subnets.