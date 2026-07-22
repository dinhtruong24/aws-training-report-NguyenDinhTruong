---
title : "Cấu hình S3 Gateway Endpoint"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b>5.5.3. </b> "
---

Trong phần này, chúng ta sẽ cấu hình **Amazon S3 Gateway Endpoint** để các tài nguyên trong VPC có thể truy cập Amazon S3 thông qua mạng nội bộ AWS mà không cần sử dụng Internet Gateway hoặc NAT Gateway.

Việc sử dụng Gateway Endpoint giúp tăng cường bảo mật, giảm chi phí truyền dữ liệu và cải thiện hiệu suất truy cập giữa EC2 và Amazon S3.

---

## Bước 1. Mở dịch vụ VPC

Đăng nhập vào **AWS Management Console**.

Thực hiện các bước sau:

1. Tìm kiếm dịch vụ **VPC**.
2. Chọn **Endpoints**.
3. Chọn **Create endpoint**.

---

## Bước 2. Tạo S3 Gateway Endpoint

Trong màn hình **Create endpoint**, cấu hình các thông tin sau:

**Service category**

```text
AWS services
```

**Service**

```text
com.amazonaws.ap-southeast-1.s3
```

**Endpoint type**

```text
Gateway
```

**VPC**

```text
delivery-dev-vpc
```

Tiếp theo, chọn các **Route Tables** cần liên kết với Gateway Endpoint.

Sau khi hoàn tất, chọn **Create endpoint**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.5-lab3/5.5.3-create-s3-gateway-endpoint.png" width="900">
</p>

<p align="center">
<i>Hình 5.5.4. Tạo Amazon S3 Gateway Endpoint.</i>
</p>

---

## Bước 3. Kiểm tra Gateway Endpoint

Sau khi Endpoint được tạo thành công:

- Mở danh sách **Endpoints**.
- Xác nhận Endpoint đã ở trạng thái **Available**.
- Kiểm tra Endpoint đã được liên kết với các Route Table tương ứng.
- Kiểm tra Service Name là:

```text
com.amazonaws.ap-southeast-1.s3
```

Từ thời điểm này, các EC2 Instance trong VPC có thể truy cập Amazon S3 thông qua mạng nội bộ AWS.

---

## Bảng cấu hình

| Thuộc tính | Giá trị |
|---|---|
| Service | Amazon S3 |
| Endpoint Type | Gateway |
| Service Name | `com.amazonaws.ap-southeast-1.s3` |
| VPC | `delivery-dev-vpc` |
| Status | Available |

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Tạo thành công Amazon S3 Gateway Endpoint.
- Liên kết Endpoint với các Route Table trong VPC.
- Cho phép EC2 truy cập Amazon S3 thông qua mạng nội bộ AWS.
- Loại bỏ nhu cầu truy cập Amazon S3 qua Internet.
- Hoàn thành cấu hình lưu trữ cho Lab 3.

Sau khi hoàn thành **5.5.3**, hệ thống đã có môi trường lưu trữ dữ liệu hoàn chỉnh và sẵn sàng cho **Lab 4 – CloudWatch Monitoring**.