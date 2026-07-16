---
title: "Các bài blogs đã đăng"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
---
Trong suốt chương trình **The First Cloud AI Journey**, tôi đã nghiên cứu, tổng hợp và chia sẻ các bài viết chuyên sâu từ AWS Blog nhằm nâng cao kiến thức về điện toán đám mây, bảo mật, trí tuệ nhân tạo và kiến trúc hệ thống trên AWS.

Các bài viết dưới đây tập trung vào những chủ đề thực tế như bảo mật thông tin xác thực cho AWS Lambda, giám sát hạ tầng bằng AI Agent và kết nối Amazon API Gateway với các tài nguyên riêng tư trong Amazon VPC. Thông qua quá trình tìm hiểu và trình bày lại nội dung, tôi đã củng cố khả năng đọc tài liệu kỹ thuật, phân tích kiến trúc AWS và chia sẻ kiến thức với cộng đồng.

###  [Blog 1 - Bảo mật thông tin xác thực cho AWS Lambda bằng AWS Secrets Manager](3.1-Blog1/)
Hướng dẫn quản lý an toàn thông tin đăng nhập database cho hàm Lambda, thay thế hoàn toàn việc lưu mật khẩu cứng (hardcode) trong mã nguồn.
- Luồng kiến trúc vận hành: API Gateway → Lambda → Secrets Manager → Amazon RDS.
- Lưu trữ thông tin xác thực an toàn bằng AWS Secrets Manager.
- Hỗ trợ tự động xoay vòng mật khẩu (Automatic Rotation).
- Tăng cường bảo mật cho kiến trúc Serverless.

**Nguồn:** [AWS Security Blog](https://aws.amazon.com/blogs/security/how-to-securely-provide-database-credentials-to-lambda-functions-by-using-aws-secrets-manager/)

###  [Blog 2 - AgentWatch: Giám sát chủ động hạ tầng AWS bằng Ambient Agents](3.2-Blog2/)
Bài viết giới thiệu AgentWatch – một giải pháp giám sát hạ tầng AWS sử dụng AI Agents để chủ động phát hiện, phân tích và xử lý các sự cố hệ thống.
- Theo dõi CloudWatch Metrics, Logs và Alarms theo thời gian thực.
- Phân tích dữ liệu bằng Amazon Bedrock AgentCore.
- Gửi báo cáo và cảnh báo trực tiếp đến Slack.
- Hỗ trợ DevOps tự động hóa quá trình giám sát hạ tầng.

**Nguồn:** [AWS Machine Learning Blog](https://aws.amazon.com/blogs/machine-learning/agentwatch-proactive-aws-monitoring-with-ambient-agents/)

###  [Blog 3 - Tìm hiểu VPC Links trong Amazon API Gateway Private Integrations](3.3-Blog3/)
Bài viết giải thích cơ chế hoạt động của VPC Link trong Amazon API Gateway, giúp kết nối API Gateway với các tài nguyên riêng tư trong Amazon VPC một cách an toàn mà không cần truy cập Internet công cộng.
- Hiểu sự khác nhau giữa Private API và Private Integration.
- Tìm hiểu AWS Hyperplane và AWS PrivateLink.
- Kết nối API Gateway với Network Load Balancer (NLB) hoặc Application Load Balancer (ALB).
- Xây dựng kiến trúc API bảo mật, linh hoạt và dễ mở rộng trên AWS.

**Nguồn:** [AWS Compute Blog](https://aws.amazon.com/blogs/compute/understanding-vpc-links-in-amazon-api-gateway-private-integrations/) 