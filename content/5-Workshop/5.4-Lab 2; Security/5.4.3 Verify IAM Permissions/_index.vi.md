---
title : "Kiểm tra quyền IAM"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b>5.4.3. </b> "
---

Trong phần này, chúng ta sẽ kiểm tra IAM Role và IAM Policy đã cấu hình ở phần trước để xác nhận EC2 Instance có thể nhận đúng danh tính AWS và truy cập các dịch vụ được cấp quyền.

Việc kiểm tra giúp bảo đảm IAM Role hoạt động đúng, Runtime Policy đã được gắn thành công và ứng dụng không cần sử dụng Access Key hoặc Secret Access Key cố định.

---

## Bước 1. Gắn IAM Role vào EC2 Instance

Mở dịch vụ **EC2** trong AWS Management Console và chọn EC2 Instance cần sử dụng IAM Role.

Thực hiện các bước sau:

1. Chọn EC2 Instance.
2. Chọn **Actions**.
3. Chọn **Security**.
4. Chọn **Modify IAM role**.
5. Trong danh sách IAM Role, chọn:

```text
delivery-ec2-role
```

6. Chọn **Update IAM role**.

Sau khi hoàn tất, EC2 Instance sẽ có thể nhận thông tin xác thực tạm thời thông qua IAM Role.

---

## Bước 2. Kết nối vào EC2 Instance

Kết nối đến EC2 Instance bằng AWS Systems Manager Session Manager hoặc phương thức truy cập phù hợp.

Sau khi đăng nhập thành công, mở Terminal và kiểm tra AWS CLI:

```bash
aws --version
```

Nếu AWS CLI đã được cài đặt, hệ thống sẽ hiển thị phiên bản hiện tại.

Không cấu hình Access Key bằng lệnh:

```bash
aws configure
```

vì EC2 Instance phải sử dụng thông tin xác thực tạm thời từ IAM Role.

---

## Bước 3. Kiểm tra danh tính IAM

Sử dụng lệnh sau:

```bash
aws sts get-caller-identity
```

Kết quả mong đợi có dạng:

```json
{
  "UserId": "AROAEXAMPLE:instance-id",
  "Account": "123456789012",
  "Arn": "arn:aws:sts::123456789012:assumed-role/delivery-ec2-role/instance-id"
}
```

Kiểm tra trường `Arn` và xác nhận IAM Role được sử dụng là:

```text
delivery-ec2-role
```

Nếu kết quả hiển thị đúng Assumed Role, EC2 Instance đã nhận được thông tin xác thực tạm thời từ IAM.

---

## Bước 4. Kiểm tra quyền truy cập Amazon S3

Sử dụng lệnh sau để kiểm tra khả năng truy cập Amazon S3:

```bash
aws s3api head-bucket \
  --bucket <bucket-name> \
  --region ap-southeast-1
```

Thay `<bucket-name>` bằng tên Amazon S3 Bucket được sử dụng trong hệ thống.

Nếu lệnh không trả về lỗi, IAM Role có quyền truy cập Bucket phù hợp.

Có thể tiếp tục kiểm tra danh sách Object:

```bash
aws s3 ls s3://<bucket-name>/
```

Kết quả mong đợi là danh sách các thư mục hoặc Object trong Bucket.

---

## Bước 5. Kiểm tra quyền truy cập Amazon SQS

Sử dụng lệnh sau:

```bash
aws sqs get-queue-url \
  --queue-name <queue-name> \
  --region ap-southeast-1
```

Thay `<queue-name>` bằng tên Amazon SQS Queue của hệ thống.

Kết quả mong đợi:

```json
{
  "QueueUrl": "https://sqs.ap-southeast-1.amazonaws.com/123456789012/<queue-name>"
}
```

Nếu Queue URL được trả về, IAM Role đã có quyền truy cập Amazon SQS theo Runtime Policy.

---

## Bước 6. Kiểm tra nguyên tắc Least Privilege

Ngoài các lệnh truy cập hợp lệ, cần xác nhận IAM Role không có quyền quản trị toàn bộ.

Kiểm tra trong AWS Management Console:

1. Mở dịch vụ **IAM**.
2. Chọn **Roles**.
3. Mở:

```text
delivery-ec2-role
```

4. Kiểm tra tab **Permissions**.
5. Xác nhận chỉ có Policy cần thiết, chẳng hạn:

```text
delivery-runtime-policy
```

6. Không được có các Policy rộng như:

```text
AdministratorAccess
PowerUserAccess
```

Runtime Policy chỉ nên cho phép các hành động và tài nguyên cần thiết đối với ứng dụng.

---

## Bước 7. Xử lý lỗi thường gặp

Nếu lệnh AWS CLI trả về:

```text
Unable to locate credentials
```

hãy kiểm tra:

- IAM Role đã được gắn vào đúng EC2 Instance chưa.
- EC2 Instance có truy cập được Instance Metadata Service không.
- Trust Relationship có cho phép `ec2.amazonaws.com` thực hiện `sts:AssumeRole` không.

Nếu lệnh trả về:

```text
AccessDenied
```

hãy kiểm tra:

- Runtime Policy đã được gắn vào IAM Role chưa.
- Policy có chứa đúng hành động AWS cần thiết không.
- ARN tài nguyên có khớp với Bucket hoặc Queue thực tế không.
- Region đang sử dụng có đúng là `ap-southeast-1` không.

---

## Bảng kiểm tra cuối cùng

| Nội dung kiểm tra | Kết quả mong đợi |
|---|---|
| IAM Role được gắn vào EC2 | `delivery-ec2-role` |
| `aws sts get-caller-identity` | Trả về Assumed Role hợp lệ |
| Kiểm tra Amazon S3 | Không có lỗi AccessDenied |
| Kiểm tra Amazon SQS | Trả về Queue URL |
| Access Key cố định | Không sử dụng |
| Quyền quản trị toàn bộ | Không được cấp |
| Runtime Policy | Đã gắn vào IAM Role |

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Gắn IAM Role vào EC2 Instance.
- Xác nhận EC2 nhận được thông tin xác thực tạm thời.
- Kiểm tra danh tính IAM bằng AWS STS.
- Kiểm tra quyền truy cập Amazon S3.
- Kiểm tra quyền truy cập Amazon SQS.
- Xác nhận Runtime Policy hoạt động đúng.
- Xác nhận hệ thống không sử dụng Access Key cố định.
- Kiểm tra việc áp dụng nguyên tắc **Least Privilege**.
- Hoàn thành Lab 2 về Security Groups và IAM.

Sau khi hoàn thành **5.4.3**, hệ thống đã có nền tảng bảo mật mạng và quyền truy cập AWS phù hợp. Tiếp theo, chúng ta sẽ thực hiện **Lab 3 – Amazon S3 Storage**.