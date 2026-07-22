---
title : "Điều kiện tiên quyết"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

Để triển khai thành công hệ thống **VietAI Scholar Assistant**, bạn cần chuẩn bị sẵn môi trường AWS và các công cụ phát triển cần thiết. Việc hoàn thành các điều kiện dưới đây sẽ giúp quá trình thực hành diễn ra thuận lợi và hạn chế các lỗi phát sinh trong quá trình triển khai.

## 1. Tài khoản AWS

Bạn cần có một tài khoản AWS đang hoạt động để tạo và quản lý các dịch vụ được sử dụng trong workshop.

Khuyến nghị sử dụng **AWS Free Tier** nếu bạn chưa từng sử dụng AWS trước đây. Ngoài ra, hãy đảm bảo tài khoản của bạn đã được kích hoạt đầy đủ và có quyền tạo các tài nguyên cần thiết.

---

## 2. Chọn Region

Trong toàn bộ workshop, chúng ta sẽ triển khai tài nguyên trong cùng một AWS Region để đảm bảo các dịch vụ có thể kết nối với nhau.

Khuyến nghị sử dụng:

- **Asia Pacific (Singapore) – ap-southeast-1**

Việc sử dụng cùng một Region giúp giảm độ trễ và tránh phát sinh lỗi khi tích hợp giữa các dịch vụ AWS.

---

## 3. Công cụ phát triển

Máy tính cần cài đặt sẵn các công cụ sau:

- Visual Studio Code
- Git
- Python 3.11 hoặc mới hơn
- Node.js
- AWS CLI
- Docker Desktop (khuyến nghị)

Đây là các công cụ sẽ được sử dụng trong suốt quá trình xây dựng và triển khai hệ thống.

---

## 4. Quyền truy cập AWS

Đảm bảo tài khoản AWS có đủ quyền sử dụng các dịch vụ sau:

- Amazon S3
- AWS Lambda
- Amazon Bedrock
- Amazon DynamoDB
- Amazon Cognito
- Amazon API Gateway
- AWS IAM
- Amazon CloudFront
- AWS CloudWatch

Nếu sử dụng tài khoản IAM, hãy cấp đầy đủ quyền cần thiết trước khi bắt đầu workshop.

---

## 5. Truy cập Amazon Bedrock

Dự án sử dụng **Amazon Bedrock** để xây dựng các AI Agents và xử lý tài liệu.

Trước khi thực hiện các Lab, hãy kiểm tra rằng tài khoản AWS đã được cấp quyền truy cập vào Amazon Bedrock và các mô hình ngôn ngữ sẽ sử dụng trong workshop.

---

## 6. Mã nguồn dự án

Chuẩn bị mã nguồn của dự án **VietAI Scholar Assistant** trên máy tính và kiểm tra rằng tất cả các thư viện phụ thuộc đã được cài đặt đầy đủ.

Nếu sử dụng Git, hãy clone repository về máy trước khi bắt đầu triển khai.

---

## 7. Kiểm tra môi trường

Trước khi chuyển sang Lab đầu tiên, hãy xác nhận rằng:

- Đăng nhập thành công vào AWS Console.
- Đã chọn đúng Region.
- AWS CLI hoạt động bình thường.
- Các công cụ phát triển đã được cài đặt.
- Có thể truy cập các dịch vụ AWS cần thiết.

---

Bạn đã sẵn sàng chưa?

Sau khi hoàn thành các điều kiện trên, chúng ta sẽ bắt đầu **Lab 1: Document Storage & Upload**, nơi hệ thống sẽ được triển khai từ bước lưu trữ tài liệu trên Amazon S3.