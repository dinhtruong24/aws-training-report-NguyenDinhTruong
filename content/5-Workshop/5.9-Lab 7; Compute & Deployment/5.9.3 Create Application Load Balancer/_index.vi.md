---
title : "Create Application Load Balancer"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b>5.9.3. </b> "
---

Trong phần này, chúng ta sẽ cấu hình **Application Load Balancer** có tên `delivery-alb` để tiếp nhận lưu lượng từ Internet và chuyển tiếp yêu cầu đến Target Group `delivery-app-tg`.

Sau khi hoàn thành cấu hình Load Balancer, chúng ta sẽ triển khai một phiên bản mới của ứng dụng từ Amazon S3 bằng phương pháp **symbolic link (symlink)**. Phương pháp này giúp chuyển đổi nhanh giữa các phiên bản ứng dụng và hỗ trợ rollback khi cần thiết.

---

## Bước 1. Tạo Application Load Balancer

Đăng nhập vào **AWS Management Console**.

Thực hiện các bước sau:

1. Mở dịch vụ **Amazon EC2**.
2. Trong menu bên trái, chọn **Load Balancers**.
3. Chọn **Create Load Balancer**.
4. Chọn **Application Load Balancer**.
5. Nhập tên Load Balancer:

```text
delivery-alb
```

---

## Bước 2. Cấu hình Application Load Balancer

Cấu hình Application Load Balancer theo các thông tin sau:

| Thuộc tính | Giá trị |
|---|---|
| Load Balancer Name | `delivery-alb` |
| Load Balancer Type | Application Load Balancer |
| Scheme | Internet-facing |
| Network | `delivery-dev-vpc` |
| Availability Zones | `public-a` và `public-b` |
| Security Group | `delivery-alb-sg` |
| Listener | HTTP cổng `80` |
| Target Group | `delivery-app-tg` |

Application Load Balancer được đặt trong hai public subnets để có thể nhận lưu lượng từ Internet.

Listener HTTP trên cổng `80` sẽ chuyển tiếp yêu cầu đến Target Group `delivery-app-tg`. Target Group tiếp tục chuyển lưu lượng đến ứng dụng trên cổng `5000`.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.9-lab7/5.9.1-compose-test-email.png" width="900">
</p>

<p align="center">
<i>Hình 5.9.3. Application Load Balancer delivery-alb.</i>
</p>

---

## Bước 3. Kiểm tra Application Load Balancer

Sau khi tạo thành công:

- Mở danh sách **Load Balancers**.
- Chọn `delivery-alb`.
- Kiểm tra trạng thái của Load Balancer.
- Xác nhận hai public subnets đã được cấu hình.
- Xác nhận Security Group là `delivery-alb-sg`.
- Kiểm tra Listener HTTP cổng `80`.
- Xác nhận Listener chuyển tiếp đến `delivery-app-tg`.

Trạng thái mong đợi:

```text
Active
```

Luồng truy cập của hệ thống:

```text
Internet
    │
    ▼
delivery-alb
HTTP:80
    │
    ▼
delivery-app-tg
HTTP:5000
    │
    ▼
Amazon EC2 Instances
```

---

## Bước 4. Chuẩn bị thông tin release

Trong file Word, phiên bản triển khai mẫu sử dụng các giá trị sau:

```bash
RELEASE=20260722-09
PACKAGE=WedNightFury-linux-x64-v9.tar.gz
```

Trong đó:

- `RELEASE` là mã của phiên bản triển khai.
- `PACKAGE` là tên gói ứng dụng được lưu trong Amazon S3.

Gói triển khai được lưu tại:

```text
s3://delivery-dev-pod-nm2026a/deployments/
```

---

## Bước 5. Tải gói triển khai từ Amazon S3

Thực hiện lệnh sau trên EC2 instance:

```bash
sudo aws s3 cp \
  s3://delivery-dev-pod-nm2026a/deployments/$PACKAGE \
  /opt/delivery/packages/$PACKAGE \
  --region ap-southeast-1
```

Lệnh trên tải gói ứng dụng từ Amazon S3 về thư mục:

```text
/opt/delivery/packages/
```

EC2 sử dụng IAM Instance Profile `delivery-ec2-role` để truy cập Amazon S3 mà không cần lưu access key trên máy chủ.

---

## Bước 6. Giải nén release

Tạo thư mục cho release mới:

```bash
sudo mkdir -p /opt/delivery/releases/$RELEASE
```

Giải nén gói triển khai:

```bash
sudo tar -xzf /opt/delivery/packages/$PACKAGE \
  -C /opt/delivery/releases/$RELEASE
```

Cập nhật quyền sở hữu thư mục:

```bash
sudo chown -R deliveryapp:deliveryapp \
  /opt/delivery/releases/$RELEASE
```

Cấp quyền thực thi cho ứng dụng:

```bash
sudo chmod +x \
  /opt/delivery/releases/$RELEASE/WedNightFury
```

Sau khi hoàn thành, release mới sẽ nằm tại:

```text
/opt/delivery/releases/20260722-09
```

---

## Bước 7. Lưu release hiện tại

Trước khi chuyển sang release mới, cần lưu lại đường dẫn của release đang hoạt động:

```bash
PREVIOUS_RELEASE=$(readlink -f /opt/delivery/current)
```

Biến `PREVIOUS_RELEASE` sẽ được sử dụng để rollback nếu release mới gặp lỗi.

Có thể kiểm tra giá trị bằng lệnh:

```bash
echo "$PREVIOUS_RELEASE"
```

---

## Bước 8. Chuyển symlink sang release mới

Tạo symlink tạm thời trỏ đến release mới:

```bash
sudo ln -sfn \
  /opt/delivery/releases/$RELEASE \
  /opt/delivery/current.next
```

Sau đó đổi symlink tạm thành symlink chính:

```bash
sudo mv -Tf \
  /opt/delivery/current.next \
  /opt/delivery/current
```

Cách cập nhật này giúp việc chuyển release diễn ra nhanh chóng và hạn chế trạng thái symlink không hoàn chỉnh.

Cấu trúc sau khi chuyển release:

```text
/opt/delivery/releases/20260722-09
                 ▲
                 │
/opt/delivery/current
```

---

## Bước 9. Khởi động lại dịch vụ

Sau khi cập nhật symlink, khởi động lại ứng dụng:

```bash
sudo systemctl restart delivery.service
```

Ứng dụng được chạy thông qua systemd service:

```text
delivery.service
```

Executable của ứng dụng:

```text
/opt/delivery/current/WedNightFury
```

---

## Quy trình triển khai hoàn chỉnh

Toàn bộ các lệnh triển khai release:

```bash
RELEASE=20260722-09
PACKAGE=WedNightFury-linux-x64-v9.tar.gz

sudo aws s3 cp \
  s3://delivery-dev-pod-nm2026a/deployments/$PACKAGE \
  /opt/delivery/packages/$PACKAGE \
  --region ap-southeast-1

sudo mkdir -p /opt/delivery/releases/$RELEASE

sudo tar -xzf /opt/delivery/packages/$PACKAGE \
  -C /opt/delivery/releases/$RELEASE

sudo chown -R deliveryapp:deliveryapp \
  /opt/delivery/releases/$RELEASE

sudo chmod +x \
  /opt/delivery/releases/$RELEASE/WedNightFury

PREVIOUS_RELEASE=$(readlink -f /opt/delivery/current)

sudo ln -sfn \
  /opt/delivery/releases/$RELEASE \
  /opt/delivery/current.next

sudo mv -Tf \
  /opt/delivery/current.next \
  /opt/delivery/current

sudo systemctl restart delivery.service
```

---

## Lưu ý về migration

Nếu release chỉ thay đổi các thành phần như:

- Amazon S3.
- Amazon SQS.
- Amazon Location.
- JavaScript.
- Cấu hình ứng dụng không liên quan đến schema.

thì **không chạy migration** nếu database schema không thay đổi.

```text
Không thay đổi schema → Không chạy migration
```

Chỉ nên chạy migration khi release thực sự có thay đổi liên quan đến database schema và đã thực hiện backup phù hợp.

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Tạo Application Load Balancer `delivery-alb`.
- Triển khai Load Balancer trong hai public subnets.
- Gắn Security Group `delivery-alb-sg`.
- Liên kết Load Balancer với Target Group `delivery-app-tg`.
- Tải gói ứng dụng từ Amazon S3.
- Giải nén ứng dụng vào thư mục release riêng.
- Lưu lại phiên bản đang hoạt động trước khi triển khai.
- Cập nhật symlink `/opt/delivery/current` sang release mới.
- Khởi động lại `delivery.service`.
- Chuẩn bị thông tin cần thiết để rollback khi release mới gặp lỗi.