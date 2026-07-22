---
title : "Workshop Overview"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

## Giới thiệu

Trong workshop này, chúng ta sẽ triển khai **VietAI Scholar Assistant** – một hệ thống hỗ trợ nghiên cứu học thuật được xây dựng trên nền tảng điện toán đám mây AWS kết hợp với các công nghệ Trí tuệ nhân tạo (Artificial Intelligence - AI). Mục tiêu của dự án là xây dựng một nền tảng có khả năng tự động phân tích tài liệu học thuật, hỗ trợ dịch thuật, tóm tắt nội dung, trả lời câu hỏi theo ngữ cảnh và hỗ trợ người học tiếp cận tài liệu một cách nhanh chóng và hiệu quả.

Hệ thống được thiết kế để tiếp nhận một hoặc nhiều tài liệu PDF từ người dùng. Sau khi tài liệu được tải lên, hệ thống sẽ tự động thực hiện quá trình phân tích, xử lý và lưu trữ dữ liệu. Kết quả cuối cùng bao gồm bản tóm tắt nội dung, bản dịch, khả năng hỏi đáp theo nội dung tài liệu và các thông tin hỗ trợ học tập khác.

Toàn bộ quy trình xử lý được triển khai trên nền tảng AWS theo kiến trúc Serverless nhằm giảm chi phí vận hành, tăng khả năng mở rộng và đơn giản hóa quá trình quản lý hạ tầng.

---

## Mục tiêu của Workshop

Sau khi hoàn thành workshop này, người thực hiện có thể:

- Hiểu được quy trình xây dựng một hệ thống AI xử lý tài liệu học thuật trên nền tảng AWS.
- Triển khai hệ thống lưu trữ tài liệu bằng Amazon S3.
- Xây dựng quy trình xử lý tài liệu bằng AWS Lambda và Amazon Bedrock.
- Hiểu cách hoạt động của mô hình Multi-Agent trong việc xử lý tài liệu.
- Xây dựng hệ thống Retrieval-Augmented Generation (RAG) phục vụ tìm kiếm và hỏi đáp theo ngữ cảnh.
- Quản lý dữ liệu và trạng thái xử lý bằng Amazon DynamoDB.
- Áp dụng các dịch vụ bảo mật của AWS để bảo vệ tài nguyên và dữ liệu người dùng.

---

## Kiến trúc hệ thống

Dự án sử dụng kiến trúc Serverless kết hợp với các dịch vụ AI của AWS để xây dựng một hệ thống xử lý tài liệu học thuật hoàn chỉnh.

Người dùng truy cập ứng dụng Web để tải lên tài liệu PDF. Sau khi tài liệu được lưu vào Amazon S3, sự kiện tải lên sẽ kích hoạt AWS Lambda thực hiện toàn bộ quy trình xử lý.

AWS Lambda đóng vai trò điều phối, gửi yêu cầu đến Amazon Bedrock để thực hiện phân tích nội dung tài liệu. Trong quá trình này, hệ thống sử dụng nhiều AI Agent nhằm xử lý các nhiệm vụ khác nhau như phân tích nội dung, dịch thuật, tóm tắt tài liệu và trả lời câu hỏi theo ngữ cảnh.

Sau khi hoàn thành xử lý, kết quả sẽ được lưu trở lại Amazon S3, đồng thời trạng thái xử lý và thông tin của tài liệu được lưu trong Amazon DynamoDB để phục vụ việc truy xuất và quản lý.

---

## Các dịch vụ AWS sử dụng

Workshop sử dụng các dịch vụ AWS sau:

- Amazon S3
- Amazon API Gateway
- AWS Lambda
- Amazon Bedrock
- Amazon DynamoDB
- Amazon Cognito
- AWS IAM
- Amazon CloudFront
- AWS KMS

Mỗi dịch vụ đảm nhận một vai trò riêng trong hệ thống nhằm đảm bảo khả năng mở rộng, bảo mật và tự động hóa toàn bộ quy trình xử lý tài liệu.

---

## Kiến thức đạt được

Sau khi hoàn thành workshop, người học sẽ nắm được:

- Kiến trúc Serverless trên AWS.
- Quy trình lưu trữ và xử lý tài liệu bằng Amazon S3.
- Cách sử dụng AWS Lambda để điều phối quy trình xử lý.
- Cách triển khai AI Agent trên Amazon Bedrock.
- Quy trình xây dựng hệ thống Retrieval-Augmented Generation (RAG).
- Cách quản lý dữ liệu bằng Amazon DynamoDB.
- Các cơ chế bảo mật cơ bản trên AWS.

---

## Kiến trúc tổng thể

<p align="center">
  <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.1-Workshop-overview/overview5.1.png" width="1000">
</p>

<p align="center">
<i>Hình 5.1. Kiến trúc tổng thể của hệ thống VietAI Scholar Assistant trên nền tảng AWS.</i>
</p>

---

Sau khi hoàn thành phần **Workshop Overview**, chúng ta sẽ tiếp tục chuẩn bị môi trường và các tài nguyên cần thiết trước khi triển khai hệ thống trong phần **Prerequisites**.
