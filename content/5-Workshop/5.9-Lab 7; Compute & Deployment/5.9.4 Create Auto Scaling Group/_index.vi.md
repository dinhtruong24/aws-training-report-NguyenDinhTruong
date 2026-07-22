---
title : "Create Auto Scaling Group"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b>5.9.4. </b> "
---

Trong phần này, chúng ta sẽ tạo **Auto Scaling Group (ASG)** sử dụng Launch Template `delivery-ec2-lt` để quản lý các Amazon EC2 instances chạy ứng dụng.

Auto Scaling Group được triển khai trong hai private application subnets là `app-a` và `app-b`. ASG giúp duy trì số lượng EC2 instances theo cấu hình mong muốn và thay thế instance khi một instance không còn hoạt động bình thường.

Sau khi cấu hình Auto Scaling Group, chúng ta sẽ kiểm tra trạng thái của ứng dụng, xác nhận HTTP health check và thực hiện rollback nếu release mới gặp lỗi.

---

## Bước 1. Mở Auto Scaling Groups

Đăng nhập vào **AWS Management Console**.

Thực hiện các bước sau:

1. Mở dịch vụ **Amazon EC2**.
2. Trong menu bên trái, chọn **Auto Scaling Groups**.
3. Chọn **Create Auto Scaling group**.
4. Nhập tên cho Auto Scaling Group.
5. Chọn Launch Template `delivery-ec2-lt`.

---

## Bước 2. Cấu hình Auto Scaling Group

Cấu hình Auto Scaling Group theo các thông tin sau:

| Thuộc tính | Giá trị |
|---|---|
| Launch Template | `delivery-ec2-lt` |
| VPC | `delivery-dev-vpc` |
| Subnets | `app-a` và `app-b` |
| Target Group | `delivery-app-tg` |
| Minimum Capacity | `1` |
| Desired Capacity | `1` |
| Maximum Capacity | Theo ngân sách workshop |
| Health Check | Elastic Load Balancing |
| Application Service | `delivery.service` |
| Executable | `/opt/delivery/current/WedNightFury` |

Các EC2 instances được đặt trong private application subnets và không cần public IP.

Việc quản trị instance được thực hiện thông qua **AWS Systems Manager Session Manager** thay vì mở SSH trực tiếp từ Internet.

---

## Bước 3. Liên kết Target Group

Trong quá trình tạo Auto Scaling Group:

1. Chọn tùy chọn liên kết với Load Balancer hiện có.
2. Chọn Target Group:

```text
delivery-app-tg
```

3. Bật Elastic Load Balancing health checks.
4. Xác nhận Target Group sử dụng HTTP trên cổng `5000`.
5. Hoàn tất quá trình tạo Auto Scaling Group.

Luồng hoạt động:

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
Auto Scaling Group
    │
    ▼
Amazon EC2 Instances
app-a / app-b
```

---

## Bước 4. Kiểm tra Auto Scaling Group

Sau khi Auto Scaling Group được tạo:

- Mở danh sách **Auto Scaling Groups**.
- Chọn Auto Scaling Group vừa tạo.
- Kiểm tra Launch Template là `delivery-ec2-lt`.
- Kiểm tra các subnets là `app-a` và `app-b`.
- Kiểm tra Desired Capacity là `1`.
- Xác nhận EC2 instance đã được tạo.
- Kiểm tra instance đã được đăng ký vào `delivery-app-tg`.
- Xác nhận Target Group hiển thị trạng thái **Healthy**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.9-lab7/5.9.1-send-test-email.png" width="900">
</p>

<p align="center">
<i>Hình 5.9.4. Auto Scaling Group sử dụng delivery-ec2-lt.</i>
</p>

---

## Bước 5. Kiểm tra release hiện tại

Kết nối đến EC2 instance thông qua **AWS Systems Manager Session Manager**.

Kiểm tra symbolic link của release đang hoạt động:

```bash
readlink -f /opt/delivery/current
```

Kết quả phải trỏ đến thư mục release hiện tại, ví dụ:

```text
/opt/delivery/releases/20260722-09
```

Executable của ứng dụng được chạy từ:

```text
/opt/delivery/current/WedNightFury
```

---

## Bước 6. Kiểm tra trạng thái dịch vụ

Kiểm tra trạng thái của `delivery.service`:

```bash
sudo systemctl status delivery.service --no-pager -l
```

Trạng thái mong đợi:

```text
active (running)
```

Nếu service không hoạt động, cần kiểm tra:

- Đường dẫn executable.
- Quyền thực thi của file `WedNightFury`.
- Biến môi trường của ứng dụng.
- Log của systemd service.
- Kết nối đến RDS và các dịch vụ AWS liên quan.

---

## Bước 7. Kiểm tra HTTP response

Kiểm tra trực tiếp ứng dụng trên EC2 instance:

```bash
curl -sS -o /dev/null \
  -w 'HTTP %{http_code}\n' \
  http://127.0.0.1:5000/
```

Kết quả mong đợi:

```text
HTTP 200
```

HTTP `200` cho biết ứng dụng đang lắng nghe trên cổng `5000` và có thể phản hồi yêu cầu.

Nếu không nhận được HTTP `200`, cần kiểm tra:

- `delivery.service` có đang chạy hay không.
- Ứng dụng có bind đúng cổng `5000` hay không.
- Health check path có tồn tại hay không.
- Ứng dụng có gặp lỗi khi khởi động hay không.

---

## Bước 8. Kiểm tra application logs

Sử dụng lệnh sau để xem log trong năm phút gần nhất:

```bash
sudo journalctl \
  -u delivery.service \
  --since "5 minutes ago" \
  --no-pager
```

Kiểm tra các lỗi liên quan đến:

- Khởi động ứng dụng.
- Database connection.
- AWS Secrets Manager.
- Amazon S3.
- Amazon SQS.
- Amazon Location.
- Quyền IAM.
- File cấu hình hoặc biến môi trường.

---

## Bước 9. Thực hiện rollback

Trước khi triển khai release mới, release cũ đã được lưu trong biến:

```bash
PREVIOUS_RELEASE=$(readlink -f /opt/delivery/current)
```

Nếu release mới gặp lỗi, chuyển symbolic link về release trước:

```bash
sudo ln -sfn \
  "$PREVIOUS_RELEASE" \
  /opt/delivery/current.next
```

Thay symbolic link hiện tại:

```bash
sudo mv -Tf \
  /opt/delivery/current.next \
  /opt/delivery/current
```

Khởi động lại ứng dụng:

```bash
sudo systemctl restart delivery.service
```

Sau khi rollback, kiểm tra lại:

```bash
readlink -f /opt/delivery/current

sudo systemctl status \
  delivery.service \
  --no-pager -l

curl -sS -o /dev/null \
  -w 'HTTP %{http_code}\n' \
  http://127.0.0.1:5000/
```

---

## Quy trình kiểm tra và rollback hoàn chỉnh

```bash
readlink -f /opt/delivery/current

sudo systemctl status \
  delivery.service \
  --no-pager -l

curl -sS -o /dev/null \
  -w 'HTTP %{http_code}\n' \
  http://127.0.0.1:5000/

sudo journalctl \
  -u delivery.service \
  --since "5 minutes ago" \
  --no-pager

# Rollback khi release mới gặp lỗi
sudo ln -sfn \
  "$PREVIOUS_RELEASE" \
  /opt/delivery/current.next

sudo mv -Tf \
  /opt/delivery/current.next \
  /opt/delivery/current

sudo systemctl restart delivery.service
```

---

## Lưu ý về cookie khi sử dụng HTTP

Trong môi trường workshop, khi truy cập ứng dụng thông qua Application Load Balancer sử dụng HTTP, có thể tạm thời cấu hình:

```text
Security__AllowInsecureHttpForTesting=true
```

Cấu hình này **chỉ được sử dụng tạm thời cho mục đích kiểm thử**.

Sau khi CloudFront HTTPS hoạt động, cần đổi lại:

```text
Security__AllowInsecureHttpForTesting=false
```

Sau đó kiểm thử lại chức năng:

- Đăng nhập.
- Session.
- Cookie.
- Điều hướng sau đăng nhập.

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Tạo Auto Scaling Group sử dụng `delivery-ec2-lt`.
- Triển khai EC2 instances trong `app-a` và `app-b`.
- Liên kết Auto Scaling Group với `delivery-app-tg`.
- Cấu hình minimum và desired capacity là `1`.
- Kiểm tra symbolic link của release hiện tại.
- Kiểm tra trạng thái `delivery.service`.
- Xác nhận ứng dụng trả về HTTP `200` trên cổng `5000`.
- Kiểm tra application logs bằng `journalctl`.
- Thực hiện rollback về release trước khi release mới gặp lỗi.
- Hoàn thành Lab 7 về EC2, ALB, Auto Scaling và triển khai ứng dụng.