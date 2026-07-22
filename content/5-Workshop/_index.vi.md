---
title: "Hội Thảo"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

#### Tổng quan

Workshop này hướng dẫn triển khai **VietAI Scholar Assistant** – một nền tảng hỗ trợ nghiên cứu học thuật được xây dựng trên nền tảng điện toán đám mây AWS và ứng dụng các mô hình Trí tuệ nhân tạo (AI) hiện đại. Hệ thống cho phép người dùng tải lên một hoặc nhiều tài liệu PDF để tự động phân tích nội dung, dịch thuật, tóm tắt, đặt câu hỏi theo ngữ cảnh và tạo bộ câu hỏi ôn tập dựa trên tài liệu.

Trong workshop, người học sẽ từng bước xây dựng toàn bộ quy trình xử lý tài liệu, từ lưu trữ dữ liệu, trích xuất nội dung, xử lý bằng Large Language Models (LLMs), tạo dữ liệu Embedding, xây dựng hệ thống Retrieval-Augmented Generation (RAG) cho đến triển khai các AI Agents trên Amazon Bedrock để tự động hóa quá trình xử lý.

Bên cạnh đó, workshop còn giới thiệu cách kết hợp nhiều dịch vụ AWS theo kiến trúc Serverless nhằm tối ưu khả năng mở rộng, tăng hiệu năng xử lý và giảm chi phí vận hành. Toàn bộ quy trình đều được triển khai trên nền tảng AWS và có thể mở rộng để phục vụ các hệ thống AI trong thực tế.

---

#### Điểm nổi bật về kiến trúc

- **Frontend:** Giao diện người dùng được xây dựng bằng React, cho phép tải lên tài liệu PDF, xem kết quả xử lý và tương tác với hệ thống AI.
- **Document Storage:** Amazon S3 được sử dụng để lưu trữ tài liệu gốc, kết quả xử lý và các tệp trung gian trong toàn bộ quy trình.
- **Backend:** Amazon API Gateway kết hợp AWS Lambda tiếp nhận yêu cầu từ người dùng và điều phối toàn bộ luồng xử lý của hệ thống.
- **AI Processing:** Amazon Bedrock cùng các AI Agents thực hiện phân tích tài liệu, dịch thuật, tóm tắt và trả lời câu hỏi dựa trên nội dung tài liệu.
- **OCR & Document Understanding:** Hệ thống hỗ trợ xử lý các tài liệu có bố cục phức tạp, hình ảnh và công thức nhằm đảm bảo kết quả phân tích đầy đủ và chính xác.
- **Retrieval-Augmented Generation (RAG):** Dữ liệu sau khi xử lý được chuyển thành Embedding và sử dụng để xây dựng hệ thống tìm kiếm ngữ nghĩa, giúp AI trả lời các câu hỏi theo đúng nội dung tài liệu.
- **Database:** Amazon DynamoDB lưu trữ trạng thái xử lý, metadata của tài liệu và các thông tin phục vụ quá trình truy xuất.
- **Security:** AWS IAM và Amazon Cognito quản lý quyền truy cập, xác thực người dùng và bảo vệ tài nguyên AWS.
- **Automation:** Toàn bộ quy trình xử lý được tự động kích hoạt thông qua các sự kiện của Amazon S3 và AWS Lambda.

---

#### Nội dung

1. [Tổng quan về workshop](5.1-Workshop-overview/)
2. [Chuẩn bị](5.2-Prerequiste/)
3. [Truy cập đến S3 từ VPC](5.3-S3-vpc/)
4. [Truy cập đến S3 từ TTDL On-premises](5.4-S3-onprem/)
5. [VPC Endpoint Policies (làm thêm)](5.5-Policy/)
6. [Dọn dẹp tài nguyên](5.6-Cleanup/)

---

## Mục tiêu đạt được

Sau khi hoàn thành workshop, người học có thể:

- Hiểu quy trình xây dựng một hệ thống AI xử lý tài liệu trên nền tảng AWS.
- Triển khai hệ thống lưu trữ tài liệu bằng Amazon S3.
- Sử dụng Amazon Bedrock để xây dựng các AI Agents phục vụ phân tích tài liệu.
- Xây dựng hệ thống Retrieval-Augmented Generation (RAG) để hỗ trợ hỏi đáp theo ngữ cảnh.
- Quản lý dữ liệu và trạng thái xử lý bằng Amazon DynamoDB.
- Áp dụng các dịch vụ bảo mật của AWS để bảo vệ hệ thống.
- Hiểu quy trình triển khai một ứng dụng AI hiện đại trên kiến trúc Serverless.

---

## Kiến trúc hệ thống

<p align="center">
  <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/Workshop.png" width="900">
</p>