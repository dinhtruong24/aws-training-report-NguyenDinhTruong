---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---


# BẢO MẬT THÔNG TIN XÁC THỰC CƠ SỞ DỮ LIỆU CHO AWS LAMBDA BẰNG AWS SECRETS MANAGER

Trong các ứng dụng Serverless, việc lưu trực tiếp tài khoản và mật khẩu cơ sở dữ liệu trong mã nguồn tiềm ẩn nhiều rủi ro về bảo mật. AWS Secrets Manager cung cấp giải pháp lưu trữ, quản lý và tự động xoay vòng thông tin xác thực, giúp ứng dụng AWS Lambda truy cập cơ sở dữ liệu an toàn hơn.

## Tổng quan

AWS Secrets Manager cho phép ứng dụng lấy thông tin xác thực chỉ khi cần sử dụng. Thay vì lưu mật khẩu trong mã nguồn hoặc biến môi trường, AWS Lambda sẽ truy xuất Secret trong quá trình thực thi, giúp giảm nguy cơ rò rỉ dữ liệu.

## Kiến trúc giải pháp

Giải pháp sử dụng các dịch vụ AWS sau:

- Amazon API Gateway tiếp nhận yêu cầu từ người dùng.
- AWS Lambda xử lý nghiệp vụ.
- AWS Secrets Manager lưu trữ thông tin xác thực.
- Amazon RDS lưu trữ dữ liệu.

Kiến trúc này giúp bảo vệ thông tin nhạy cảm và tách biệt dữ liệu xác thực khỏi mã nguồn ứng dụng.

## Quy trình triển khai

Quy trình gồm bốn bước chính.

### Bước 1 – Lưu thông tin xác thực

Tạo Secret trong AWS Secrets Manager chứa tên đăng nhập và mật khẩu của Amazon RDS.

### Bước 2 – Cấu hình Lambda

Cấp quyền cho AWS Lambda thông qua IAM Role để truy cập Secret.

### Bước 3 – Truy xuất Secret

Khi Lambda được thực thi, hàm sẽ lấy thông tin xác thực từ AWS Secrets Manager và kết nối đến Amazon RDS.

### Bước 4 – Tự động xoay vòng mật khẩu

AWS Secrets Manager hỗ trợ Automatic Rotation giúp thay đổi mật khẩu định kỳ mà không ảnh hưởng đến ứng dụng.

## Lợi ích

Giải pháp mang lại nhiều lợi ích:

- Loại bỏ mật khẩu hardcode trong mã nguồn.
- Bảo vệ thông tin xác thực an toàn.
- Hỗ trợ tự động xoay vòng mật khẩu.
- Đơn giản hóa việc quản lý Secret.
- Tăng cường bảo mật cho ứng dụng Serverless.
- Tích hợp dễ dàng với các dịch vụ AWS.

## Kết luận

AWS Secrets Manager là giải pháp hiệu quả để quản lý thông tin xác thực trong các ứng dụng Serverless. Việc kết hợp Amazon API Gateway, AWS Lambda, AWS Secrets Manager và Amazon RDS giúp tăng cường bảo mật, giảm công việc quản trị và đơn giản hóa việc quản lý thông tin xác thực.

<p align="center">
<img src="https://dinhtruong24.github.io/aws-training-report-NguyenDinhTruong/images/3-BlogsPosted/blog1-architecture.png" width="700" alt="Kiến trúc AWS Secrets Manager">
</p>

<p align="center">
<i>Hình 1. Kiến trúc quản lý an toàn thông tin xác thực cơ sở dữ liệu bằng AWS Secrets Manager.</i>
</p>

<p align="center">
<strong>Bài viết tham khảo:</strong>
<a href="https://aws.amazon.com/blogs/security/how-to-securely-provide-database-credentials-to-lambda-functions-by-using-aws-secrets-manager/">
AWS Security Blog
</a>
</p>

<p align="center">
<strong>Bài đăng cộng đồng:</strong>
<a href="https://www.facebook.com/groups/awsstudygroupfcj/posts/2187144322050528">
AWS Study Group – Facebook
</a>
</p>