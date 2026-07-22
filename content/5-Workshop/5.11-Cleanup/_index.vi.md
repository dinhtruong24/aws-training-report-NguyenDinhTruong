---
title : "Cleanup"
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
- Workshop được hoàn thành đầy đủ và môi trường sẵn sàng cho các lần triển khai tiếp theo.