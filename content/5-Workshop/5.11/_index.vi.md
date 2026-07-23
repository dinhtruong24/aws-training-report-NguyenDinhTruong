---
title : "Dọn dẹp tài nguyên"
date : 2024-01-01
weight : 11
chapter : false
pre : " <b>5.11. </b> "
---

Sau khi hoàn thành toàn bộ Workshop và xác nhận hệ thống hoạt động đúng như mong đợi, bước cuối cùng là **Cleanup**. Mục đích của bước này là dọn dẹp các tài nguyên AWS đã tạo trong quá trình thực hành để tránh phát sinh chi phí không cần thiết.

Việc xóa các tài nguyên không còn sử dụng cũng giúp giữ môi trường AWS gọn gàng và sẵn sàng cho các lần triển khai tiếp theo.

---

## Mục tiêu

Sau khi hoàn thành phần này, bạn sẽ có thể:

- Xóa các tài nguyên AWS không còn sử dụng.
- Giảm thiểu chi phí phát sinh sau khi hoàn thành Workshop.
- Đảm bảo môi trường AWS được dọn dẹp hoàn toàn.
- Chuẩn bị tài khoản AWS cho các dự án hoặc Workshop tiếp theo.

---

## Các tài nguyên cần kiểm tra

Trong quá trình Cleanup, cần kiểm tra và xóa các tài nguyên đã tạo trong Workshop, bao gồm:

- Amazon EC2 Instances.
- Auto Scaling Group.
- Application Load Balancer.
- Target Group.
- Launch Template.
- Amazon S3 Buckets (nếu không còn sử dụng).
- Amazon CloudWatch Alarms.
- Amazon API Gateway.
- AWS Lambda Functions.
- Amazon Location Service resources.
- IAM Roles hoặc Policies được tạo riêng cho Workshop (nếu không còn sử dụng).

---

## Quy trình Cleanup

Thực hiện các bước sau:

1. Xóa hoặc dừng các Amazon EC2 instances.
2. Xóa Auto Scaling Group.
3. Xóa Application Load Balancer.
4. Xóa Target Group.
5. Xóa Launch Template.
6. Xóa các tài nguyên AWS khác được tạo trong Workshop nếu không còn cần thiết.
7. Kiểm tra lại tài khoản AWS để đảm bảo không còn tài nguyên phát sinh chi phí.

---

## Lưu ý

Trước khi xóa tài nguyên, hãy đảm bảo rằng:

- Không còn dữ liệu cần lưu trữ.
- Không còn dịch vụ nào đang sử dụng các tài nguyên này.
- Đã sao lưu dữ liệu quan trọng nếu cần.

Việc Cleanup nên được thực hiện sau khi hoàn thành toàn bộ quá trình kiểm thử và xác nhận hệ thống hoạt động ổn định.

---

## Kết quả đạt được

Sau khi hoàn thành Cleanup:

- Tất cả các tài nguyên không còn sử dụng đã được xóa.
- Tài khoản AWS được dọn dẹp gọn gàng.
- Không phát sinh chi phí không cần thiết.
- Workshop được hoàn thành đầy đủ và môi trường sẵn sàng cho các lần triển khai tiếp theo.Cleanup là một phần bắt buộc của workshop. Trước khi xóa, phải lưu evidence, backup dữ liệu cần giữ và ghi rõ tài nguyên nào đã xóa, giữ lại hoặc chưa từng tạo.

5.11.1. Nguyên tắc an toàn
Xác nhận đúng AWS account và đúng region; CloudFront/WAF là tài nguyên có phạm vi global hoặc scope riêng.
Ngừng producer và thao tác nghiệp vụ mới trước khi xử lý SQS, Lambda và database.
Archive ảnh chụp, log, migration history, queue/DLQ state và dữ liệu cần nộp ra ngoài tài nguyên sắp xóa.
Không purge queue/DLQ khi chưa kiểm tra message; purge là thao tác không thể hoàn tác.
RDS phải có final snapshot/logical backup nếu còn yêu cầu khôi phục.
Không force-delete secret; sử dụng recovery window.

5.11.2. Thứ tự cleanup theo dependency

| Thứ tự | Nhóm tài nguyên | Thao tác |
|---|---|---|
| 0 | Đóng băng thay đổi và lưu evidence | Ngừng tạo dữ liệu mới; export log, screenshot, queue/DLQ state; backup dữ liệu cần nộp. |
| 1 | Edge (nếu đã tạo) | Disable CloudFront, chờ deploy xong; gỡ WAF; xóa distribution/OAC theo dependency. Nếu chưa triển khai thì ghi `N/A`. |
| 2 | Compute | Đặt ASG desired/min về 0 hoặc xóa ASG; terminate EC2 sau khi lưu log và gói release cần giữ. |
| 3 | Load Balancing | Xóa listener/rule, ALB rồi Target Group. |
| 4 | Serverless và Messaging | Disable SQS trigger trước; xóa Lambda; kiểm tra DLQ; xóa main queue rồi DLQ. |
| 5 | Storage | Archive POD/evidence; xóa object versions và delete markers nếu có; xóa bucket khi chắc chắn. |
| 6 | Database | Tạo final snapshot và logical backup; xóa RDS; chỉ xóa snapshot khi không còn yêu cầu khôi phục. |
| 7 | Secrets | Schedule deletion sau khi ứng dụng dừng và snapshot RDS đã an toàn; dùng recovery window. |
| 8 | Monitoring | Export log/alarm evidence; xóa alarms, dashboards, log groups, trail/topic nếu không còn dùng. |
| 9 | Network | Xóa VPC endpoints → NAT Gateway → release EIP → route tables → subnets → SG → detach/xóa IGW → VPC. |
| 10 | IAM/KMS và chi phí | Xóa policy/role không còn gắn; chỉ schedule KMS key deletion khi không còn dữ liệu phụ thuộc; kiểm tra Cost Explorer/Budgets. |

5.11.3. Lệnh/checklist tham khảo
```bash
# Compute / service evidence
sudo systemctl status delivery.service --no-pager -l
sudo journalctl -u delivery.service -n 200 --no-pager

# Queue state
aws sqs get-queue-attributes --queue-url <QUEUE_URL> --attribute-names All --region ap-southeast-1

# Kiểm tra tài nguyên còn phát sinh chi phí
aws ec2 describe-nat-gateways --region ap-southeast-1
aws elbv2 describe-load-balancers --region ap-southeast-1
aws rds describe-db-instances --region ap-southeast-1
```

5.11.4. Checklist network teardown
- [ ] VPC endpoints đã xóa.
- [ ] NAT Gateway ở trạng thái Deleted.
- [ ] Elastic IP của NAT đã được release riêng.
- [ ] Không còn route `0.0.0.0/0` trỏ vào NAT đã xóa và không có route blackhole.
- [ ] Custom route tables, subnets và security groups không còn dependency.
- [ ] Internet Gateway đã detach rồi mới xóa.
- [ ] VPC đã xóa hoặc được ghi rõ giữ lại.

5.11.5. Biên bản cleanup

| Tài nguyên | Trạng thái | Evidence/Ghi chú |
|---|---|---|
| CloudFront/WAF | N/A / DELETED / RETAINED | |
| ASG/EC2 | N/A / DELETED / RETAINED | |
| ALB/Target Group | N/A / DELETED / RETAINED | |
| Lambda/SQS/DLQ | N/A / DELETED / RETAINED | |
| S3 | N/A / DELETED / RETAINED | Ghi rõ dữ liệu đã archive. |
| RDS/Snapshot | N/A / DELETED / RETAINED | Ghi final snapshot identifier. |
| Secrets Manager | N/A / SCHEDULED / RETAINED | Không ghi secret value. |
| CloudWatch/CloudTrail | N/A / DELETED / RETAINED | |
| NAT/EIP/VPC | N/A / DELETED / RETAINED | |
| IAM/KMS | N/A / DELETED / RETAINED | |