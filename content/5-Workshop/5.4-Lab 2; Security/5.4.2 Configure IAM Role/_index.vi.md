---
title : "Cấu hình IAM Role và IAM Policy"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b>5.4.2. </b> "
---

Trong phần này, chúng ta sẽ tạo một **IAM Role** dành cho EC2 và cấu hình **IAM Policy** để ứng dụng có thể truy cập các dịch vụ AWS cần thiết trong quá trình hoạt động.

Việc sử dụng IAM Role giúp EC2 Instance nhận thông tin xác thực tạm thời từ AWS mà không cần lưu Access Key và Secret Access Key trực tiếp trong mã nguồn hoặc tệp cấu hình của ứng dụng.

---

## Bước 1. Tạo IAM Role cho EC2

Đăng nhập vào **AWS Management Console**, tìm kiếm và mở dịch vụ **IAM**.

Thực hiện các bước sau:

1. Chọn **Roles** trong menu bên trái.
2. Chọn **Create role**.
3. Trong phần **Trusted entity type**, chọn:

```text
AWS service
```

4. Trong phần **Use case**, chọn:

```text
EC2
```

5. Chọn **Next**.
6. Chuyển sang bước đặt tên Role.
7. Nhập tên IAM Role:

```text
delivery-ec2-role
```

8. Nhập mô tả:

```text
IAM Role for the delivery application EC2 instances
```

9. Kiểm tra thông tin và chọn **Create role**.

IAM Role này sẽ được gắn vào EC2 Instance trong Lab triển khai hệ thống tính toán.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.4-lab2/5.4.2-create-iam-role.png" width="900">
</p>

<p align="center">
<i>Hình 5.4.4. Tạo IAM Role dành cho EC2 Instance.</i>
</p>

---

## Bước 2. Kiểm tra IAM Role

Sau khi tạo IAM Role thành công, mở Role:

```text
delivery-ec2-role
```

Kiểm tra các thông tin sau:

- **Role name:** `delivery-ec2-role`
- **Trusted entity:** `ec2.amazonaws.com`
- **Use case:** EC2
- Role được tạo trong đúng tài khoản AWS.
- Role chưa chứa thông tin Access Key cố định.

Trong tab **Trust relationships**, xác nhận EC2 được phép sử dụng Role thông qua hành động:

```text
sts:AssumeRole
```

Trust Policy có dạng:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": "ec2.amazonaws.com"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.4-lab2/5.4.2-verify-iam-role.png" width="900">
</p>

<p align="center">
<i>Hình 5.4.5. Kiểm tra IAM Role và Trust Relationship dành cho EC2.</i>
</p>

---

## Bước 3. Tạo Runtime IAM Policy

Tiếp theo, tạo IAM Policy để cấp cho ứng dụng các quyền cần thiết trong quá trình hoạt động.

Trong dịch vụ **IAM**, thực hiện:

1. Chọn **Policies**.
2. Chọn **Create policy**.
3. Chọn tab **JSON**.
4. Nhập nội dung Policy phù hợp với các dịch vụ mà ứng dụng cần sử dụng.
5. Chọn **Next**.
6. Nhập tên Policy:

```text
delivery-runtime-policy
```

7. Nhập mô tả:

```text
Runtime permissions for the delivery application
```

8. Kiểm tra cấu hình và chọn **Create policy**.

Policy có thể bao gồm các quyền cần thiết để ứng dụng tương tác với Amazon S3, Amazon SQS và các dịch vụ hỗ trợ khác.

Ví dụ cấu trúc Policy:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "S3ObjectAccess",
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:PutObject",
        "s3:DeleteObject",
        "s3:ListBucket"
      ],
      "Resource": [
        "arn:aws:s3:::delivery-*",
        "arn:aws:s3:::delivery-*/*"
      ]
    },
    {
      "Sid": "SQSAccess",
      "Effect": "Allow",
      "Action": [
        "sqs:GetQueueUrl",
        "sqs:GetQueueAttributes",
        "sqs:SendMessage",
        "sqs:ReceiveMessage",
        "sqs:DeleteMessage"
      ],
      "Resource": "arn:aws:sqs:ap-southeast-1:*:delivery-*"
    }
  ]
}
```

> **Lưu ý:** Khi triển khai thực tế, nên thay ký tự đại diện bằng ARN cụ thể của từng tài nguyên để tuân thủ nguyên tắc **Least Privilege**.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.4-lab2/5.4.2-create-runtime-policy.png" width="900">
</p>

<p align="center">
<i>Hình 5.4.6. Tạo Runtime IAM Policy cho ứng dụng.</i>
</p>

---

## Bước 4. Gắn IAM Policy vào IAM Role

Sau khi tạo Policy, tiến hành gắn Policy vào Role `delivery-ec2-role`.

Thực hiện các bước sau:

1. Trong dịch vụ **IAM**, chọn **Roles**.
2. Mở Role:

```text
delivery-ec2-role
```

3. Trong tab **Permissions**, chọn **Add permissions**.
4. Chọn **Attach policies**.
5. Tìm kiếm Policy:

```text
delivery-runtime-policy
```

6. Đánh dấu Policy cần gắn.
7. Chọn **Add permissions**.

Sau khi hoàn tất, IAM Role sẽ có các quyền cần thiết để EC2 Instance truy cập những dịch vụ AWS được quy định trong Runtime Policy.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.4-lab2/5.4.2-attach-policy-to-role.png" width="900">
</p>

<p align="center">
<i>Hình 5.4.7. Gắn Runtime IAM Policy vào IAM Role dành cho EC2.</i>
</p>

---

## Bước 5. Kiểm tra quyền của IAM Role

Mở lại Role `delivery-ec2-role` và kiểm tra tab **Permissions**.

Xác nhận Policy sau đã xuất hiện:

```text
delivery-runtime-policy
```

Đồng thời kiểm tra:

- Role có đúng Trust Relationship dành cho EC2.
- Runtime Policy đã được gắn thành công.
- Không có quyền quản trị toàn bộ như `AdministratorAccess`.
- Quyền truy cập chỉ giới hạn trong các dịch vụ và tài nguyên cần thiết.
- Không sử dụng Access Key cố định trong ứng dụng.

---

## Kết quả đạt được

Sau khi hoàn thành phần này, bạn đã:

- Tạo IAM Role `delivery-ec2-role`.
- Cấu hình EC2 làm Trusted Entity.
- Kiểm tra Trust Relationship của IAM Role.
- Tạo Runtime IAM Policy `delivery-runtime-policy`.
- Cấu hình quyền truy cập các dịch vụ AWS cần thiết.
- Gắn Runtime Policy vào IAM Role.
- Áp dụng nguyên tắc **Least Privilege**.
- Chuẩn bị IAM Role để gắn vào EC2 Instance trong các Lab tiếp theo.

Trong phần tiếp theo, chúng ta sẽ thực hiện **5.4.3 – Kiểm tra quyền IAM** bằng AWS CLI.