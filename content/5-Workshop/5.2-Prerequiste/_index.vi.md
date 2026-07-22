---
title : "Điều kiện tiên quyết"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

Để triển khai thành công **hệ thống quản lý giao hàng trên AWS**, bạn cần chuẩn bị tài khoản AWS, quyền truy cập, công cụ quản trị và các thông tin cấu hình cần thiết.

Việc hoàn thành các điều kiện tiên quyết dưới đây sẽ giúp quá trình thực hành diễn ra thuận lợi và hạn chế lỗi khi triển khai các tài nguyên mạng, cơ sở dữ liệu, lưu trữ, xử lý sự kiện và ứng dụng trên Amazon EC2.

---

## 1. Tài khoản AWS

Bạn cần có một tài khoản AWS đang hoạt động để tạo và quản lý các dịch vụ được sử dụng trong workshop.

Tài khoản cần được kích hoạt đầy đủ và có phương thức thanh toán hợp lệ. Trong quá trình thực hành, một số tài nguyên có thể phát sinh chi phí, đặc biệt là:

- NAT Gateway.
- Amazon RDS for MySQL.
- Application Load Balancer.
- Amazon EC2.
- Amazon Location Service.
- Amazon Route 53 hoặc Amazon CloudFront nếu được sử dụng.

Nên theo dõi chi phí thường xuyên và thực hiện phần **Cleanup** sau khi hoàn thành workshop.

---

## 2. Chọn AWS Region

Toàn bộ tài nguyên trong workshop được triển khai trong cùng một AWS Region để đảm bảo khả năng kết nối giữa các dịch vụ.

Region được sử dụng:

```text
Asia Pacific (Singapore)
ap-southeast-1
```

Trước khi tạo tài nguyên, hãy kiểm tra Region ở góc trên bên phải của AWS Management Console.

Việc sử dụng đúng Region đặc biệt quan trọng đối với:

- Amazon VPC.
- Amazon EC2.
- Amazon RDS.
- Amazon S3.
- Amazon SQS.
- AWS Lambda.
- Amazon SES.
- Amazon Location Service.
- AWS Secrets Manager.

---

## 3. Quyền truy cập AWS

Tài khoản hoặc IAM user được sử dụng trong workshop cần có quyền tạo, cập nhật và xóa các tài nguyên liên quan.

Các dịch vụ chính cần quyền truy cập bao gồm:

- Amazon VPC.
- Amazon EC2.
- Elastic Load Balancing.
- Amazon EC2 Auto Scaling.
- Amazon RDS.
- AWS Secrets Manager.
- Amazon S3.
- Amazon SQS.
- AWS Lambda.
- Amazon SES.
- Amazon Location Service.
- AWS IAM.
- AWS Systems Manager.
- Amazon CloudWatch.
- AWS KMS.

Nếu sử dụng IAM user hoặc IAM role giới hạn quyền, hãy đảm bảo principal đó có đủ quyền thực hiện các Lab.

Trong môi trường thực tế, nên áp dụng nguyên tắc **quyền tối thiểu – Least Privilege**.

---

## 4. Công cụ cần thiết

Máy tính cần chuẩn bị các công cụ sau:

- Trình duyệt web hiện đại.
- Visual Studio Code.
- Git.
- AWS CLI.
- Terminal, PowerShell hoặc Git Bash.
- Trình giải nén tệp `.zip` hoặc `.tar.gz`.

Các công cụ này được sử dụng để:

- Quản lý mã nguồn.
- Chỉnh sửa cấu hình.
- Thực thi AWS CLI.
- Tải gói triển khai lên Amazon S3.
- Quản lý nội dung release.
- Kiểm tra và triển khai website báo cáo.

Có thể kiểm tra AWS CLI bằng lệnh:

```bash
aws --version
```

---

## 5. Cấu hình AWS CLI

Sau khi cài đặt AWS CLI, cấu hình thông tin đăng nhập bằng lệnh:

```bash
aws configure
```

Nhập các thông tin cần thiết:

```text
AWS Access Key ID
AWS Secret Access Key
Default region name: ap-southeast-1
Default output format: json
```

Không lưu Access Key trực tiếp trong source code hoặc các tệp được đẩy lên GitHub.

Đối với Amazon EC2 trong workshop, ứng dụng sử dụng IAM Instance Profile thay vì lưu Access Key trên máy chủ.

---

## 6. Mã nguồn và gói triển khai

Chuẩn bị mã nguồn hoặc gói phát hành của ứng dụng quản lý giao hàng.

Gói triển khai mẫu được sử dụng trong workshop:

```text
WedNightFury-linux-x64-v9.tar.gz
```

Ứng dụng sau khi triển khai được chạy từ đường dẫn:

```text
/opt/delivery/current/WedNightFury
```

Dịch vụ systemd quản lý ứng dụng:

```text
delivery.service
```

Gói release được lưu trong Amazon S3 và tải xuống EC2 trong quá trình triển khai.

Ví dụ vị trí lưu trữ:

```text
s3://delivery-dev-pod-nm2026a/deployments/
```

---

## 7. Quy ước đặt tên tài nguyên

Để tránh nhầm lẫn trong quá trình thực hành, workshop sử dụng các tên tài nguyên thống nhất.

| Tài nguyên | Tên sử dụng |
|---|---|
| VPC | `delivery-dev-vpc` |
| EC2 Security Group | `delivery-ec2-sg` |
| ALB Security Group | `delivery-alb-sg` |
| EC2 IAM Role | `delivery-ec2-role` |
| Launch Template | `delivery-ec2-lt` |
| Target Group | `delivery-app-tg` |
| Application Load Balancer | `delivery-alb` |
| Application Service | `delivery.service` |

Bạn nên sử dụng đúng các tên trên để nội dung giữa các Lab được nhất quán.

---

## 8. Chuẩn bị quản trị EC2 bằng AWS Systems Manager

Các Amazon EC2 instances của ứng dụng được triển khai trong private application subnets và không cần public IP.

Việc quản trị instance được thực hiện thông qua **AWS Systems Manager Session Manager**.

Để Session Manager hoạt động, cần đảm bảo:

- EC2 được gắn IAM Instance Profile phù hợp.
- IAM Role có quyền sử dụng Systems Manager.
- SSM Agent được cài đặt và đang hoạt động trên AMI.
- EC2 có đường truyền ra ngoài thông qua NAT Gateway hoặc các VPC Endpoints phù hợp.
- Instance xuất hiện trong danh sách Managed Nodes của Systems Manager.

Phương pháp này giúp hạn chế việc mở cổng SSH trực tiếp từ Internet.

---

## 9. Chuẩn bị địa chỉ email cho Amazon SES

Workshop sử dụng **Amazon Simple Email Service – Amazon SES** để gửi email thông báo.

Trước khi kiểm thử, cần chuẩn bị một địa chỉ email đang hoạt động để:

- Tạo Email Identity.
- Nhận email xác minh từ Amazon SES.
- Gửi và nhận email thử nghiệm.
- Kiểm tra chức năng thông báo của hệ thống.

Nếu tài khoản Amazon SES đang ở Sandbox, địa chỉ người gửi và người nhận có thể đều phải được xác minh.

---

## 10. Kiểm tra hạn mức và chi phí

Trước khi bắt đầu, hãy kiểm tra:

- Hạn mức Amazon EC2.
- Hạn mức Elastic IP.
- Hạn mức NAT Gateway.
- Hạn mức Amazon RDS.
- Trạng thái Amazon SES.
- Khả năng truy cập Amazon Location Service.
- Ngân sách dự kiến cho Auto Scaling Group.

Có thể tạo AWS Budget hoặc CloudWatch Billing Alarm để theo dõi chi phí.

---

## 11. Kiểm tra môi trường

Trước khi chuyển sang Lab đầu tiên, hãy xác nhận rằng:

- Đăng nhập thành công vào AWS Management Console.
- Đã chọn đúng Region `ap-southeast-1`.
- AWS CLI hoạt động bình thường.
- Tài khoản có đủ quyền tạo tài nguyên.
- Đã chuẩn bị Visual Studio Code, Git và Terminal.
- Đã có mã nguồn hoặc gói triển khai của ứng dụng.
- Đã chuẩn bị địa chỉ email để kiểm thử Amazon SES.
- Có thể truy cập AWS Systems Manager.
- Đã nắm được quy ước đặt tên tài nguyên.
- Đã hiểu các tài nguyên có thể phát sinh chi phí.

---

## Kết quả đạt được

Sau khi hoàn thành phần điều kiện tiên quyết, bạn đã:

- Chuẩn bị tài khoản AWS và quyền truy cập.
- Chọn đúng Region triển khai.
- Cài đặt các công cụ cần thiết.
- Cấu hình AWS CLI.
- Chuẩn bị mã nguồn và gói triển khai.
- Chuẩn bị môi trường quản trị EC2 bằng Session Manager.
- Chuẩn bị email để kiểm thử Amazon SES.
- Sẵn sàng bắt đầu xây dựng hạ tầng của hệ thống.

---

Bạn đã sẵn sàng chưa?

Sau khi hoàn thành các điều kiện trên, chúng ta sẽ bắt đầu **Lab 1: Network Infrastructure**, nơi VPC, subnets, Internet Gateway, NAT Gateway và Route Tables của hệ thống sẽ được triển khai.