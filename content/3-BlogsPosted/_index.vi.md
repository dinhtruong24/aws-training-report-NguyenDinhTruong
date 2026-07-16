---
title: "Các bài blogs đã đăng"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
---


# TÌM HIỂU VPC LINK TRONG PRIVATE INTEGRATIONS CỦA AMAZON API GATEWAY

Trong các hệ thống hiện đại, nhiều ứng dụng triển khai dịch vụ backend bên trong Amazon VPC nhằm tăng cường bảo mật và hạn chế truy cập trực tiếp từ Internet. Tuy nhiên, các ứng dụng này vẫn cần cung cấp API cho người dùng hoặc các hệ thống khác. Amazon API Gateway VPC Link là giải pháp giúp kết nối an toàn giữa API Gateway và các dịch vụ backend trong VPC mà không cần công khai hạ tầng nội bộ.

## Tổng quan

Amazon API Gateway VPC Link cho phép API Gateway tích hợp với các ứng dụng chạy trên Amazon EC2, Amazon ECS, Amazon EKS hoặc các dịch vụ khác trong Amazon VPC. Thay vì để người dùng truy cập trực tiếp vào backend, mọi yêu cầu sẽ được chuyển tiếp thông qua API Gateway và VPC Link, giúp tăng cường bảo mật và cô lập mạng.

## Kiến trúc giải pháp

Tùy theo loại API được sử dụng, Amazon API Gateway hỗ trợ các kiến trúc VPC Link khác nhau.

### VPC Link cho REST API

Đối với REST API, Amazon API Gateway sử dụng AWS PrivateLink kết hợp với Network Load Balancer (NLB) để tạo kết nối riêng đến các dịch vụ backend trong Amazon VPC. Kiến trúc này phù hợp với các hệ thống REST truyền thống yêu cầu khả năng bảo mật cao và truy cập đến tài nguyên nội bộ.

### Private API với Private Integrations

Private API chỉ cho phép các tài nguyên trong Amazon VPC được cấp quyền truy cập thông qua Interface VPC Endpoint. Khi kết hợp với VPC Link, cả API và backend đều hoạt động trong môi trường riêng tư, giúp tăng cường bảo mật cho các ứng dụng nội bộ của doanh nghiệp.


### VPC Link cho HTTP API

Đối với HTTP API, Amazon API Gateway sử dụng công nghệ AWS Hyperplane thay vì AWS PrivateLink. Kiến trúc này hỗ trợ nhiều loại Integration Target như Application Load Balancer (ALB), Network Load Balancer (NLB) và AWS Cloud Map. So với REST API, HTTP API có cấu hình đơn giản hơn, độ trễ thấp hơn và chi phí vận hành tối ưu hơn.

## Quy trình triển khai

Giải pháp được triển khai theo năm bước chính.

### Bước 1 – Triển khai Backend

Triển khai ứng dụng trên Amazon EC2, Amazon ECS hoặc Amazon EKS bên trong các Private Subnet.

### Bước 2 – Cấu hình Load Balancer

Tạo Application Load Balancer hoặc Network Load Balancer để tiếp nhận lưu lượng từ Amazon API Gateway.

### Bước 3 – Tạo VPC Link

Tạo VPC Link trong Amazon API Gateway và liên kết với Load Balancer đã cấu hình.

### Bước 4 – Cấu hình API Gateway

Tạo các Route và cấu hình Private Integration để API Gateway chuyển tiếp yêu cầu đến backend thông qua VPC Link.

### Bước 5 – Kiểm tra kết nối

Thực hiện gửi yêu cầu đến API Gateway và xác nhận backend nhận được yêu cầu thành công thông qua kết nối riêng.

## Lợi ích

Amazon API Gateway VPC Link mang lại nhiều lợi ích cho hệ thống:

- Giữ các dịch vụ backend luôn ở chế độ riêng tư.
- Ngăn chặn truy cập trực tiếp từ Internet.
- Tăng cường bảo mật cho hạ tầng AWS.
- Hỗ trợ cả REST API và HTTP API.
- Tích hợp với ALB, NLB và AWS Cloud Map.
- Đơn giản hóa việc triển khai Private API.
- Hỗ trợ kiến trúc có khả năng mở rộng và tính sẵn sàng cao.
- Giảm chi phí và công sức quản trị hệ thống.

## Kết luận

Amazon API Gateway VPC Link là giải pháp hiệu quả để kết nối API với các dịch vụ backend bên trong Amazon VPC. Việc sử dụng REST API cùng AWS PrivateLink hoặc HTTP API cùng AWS Hyperplane giúp doanh nghiệp xây dựng hệ thống API an toàn, linh hoạt và có khả năng mở rộng cao, đồng thời vẫn bảo vệ được toàn bộ hạ tầng nội bộ khỏi truy cập trực tiếp từ Internet.

<p align="center">
<img src="https://dinhtruong24.github.io/aws-training-report-NguyenDinhTruong/images/3-BlogsPosted/blog3-rest-api.png" width="700">
</p>

<p align="center">
<i>Hình 3.1. Kiến trúc VPC Link dành cho Amazon API Gateway REST API.</i>
</p>

<br>

<p align="center">
<img src="https://dinhtruong24.github.io/aws-training-report-NguyenDinhTruong/images/3-BlogsPosted/blog3-private-api.png" width="700">
</p>

<p align="center">
<i>Hình 3.2. Kiến trúc Private API sử dụng Private Integrations.</i>
</p>

<br>

<p align="center">
<img src="https://dinhtruong24.github.io/aws-training-report-NguyenDinhTruong/images/3-BlogsPosted/blog3-http-api.png" width="700">
</p>

<p align="center">
<i>Hình 3.3. Kiến trúc VPC Link dành cho Amazon API Gateway HTTP API.</i>
</p>

---

<p align="center">
<strong>Bài viết tham khảo:</strong>
<a href="https://aws.amazon.com/vi/blogs/compute/understanding-vpc-links-in-amazon-api-gateway-private-integrations/">
AWS Compute Blog
</a>
</p>

<p align="center">
<strong>Bài đăng cộng đồng:</strong>
<a href="https://www.facebook.com/groups/awsstudygroupfcj/posts/2194084638023163">
AWS Study Group – Facebook
</a>
</p>