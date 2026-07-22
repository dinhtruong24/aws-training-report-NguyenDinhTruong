---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

#### Tổng quan

Hội thảo này hướng dẫn xây dựng **VietAI Scholar Assistant** – một nền tảng hỗ trợ nghiên cứu học thuật ứng dụng Trí tuệ nhân tạo (AI) và các dịch vụ điện toán đám mây của AWS. Hệ thống cho phép người dùng tải lên một hoặc nhiều tài liệu PDF để tự động phân tích, dịch thuật, tóm tắt nội dung và đặt câu hỏi trực tiếp với tài liệu thông qua mô hình Retrieval-Augmented Generation (RAG).

Trong quá trình triển khai, người thực hiện sẽ tìm hiểu cách kết hợp nhiều dịch vụ AWS hiện đại để xây dựng một ứng dụng AI hoàn chỉnh, từ lưu trữ dữ liệu, xử lý tài liệu, điều phối quy trình bằng kiến trúc Serverless đến triển khai hệ thống Multi-Agent AI trên Amazon Bedrock.

Ngoài việc xử lý văn bản, hệ thống còn hỗ trợ nhận diện công thức toán học, mô tả biểu đồ, xử lý hình ảnh và xuất kết quả dưới định dạng Markdown hoặc HTML, giúp người học và nhà nghiên cứu tiếp cận tài liệu chuyên ngành thuận tiện hơn. :contentReference[oaicite:0]{index=0}

#### Điểm nổi bật về kiến trúc

- **Giao diện người dùng:** Được xây dựng bằng React, lưu trữ trên Amazon S3 và phân phối qua Amazon CloudFront.
- **Backend:** Amazon API Gateway kết hợp AWS Lambda để tiếp nhận yêu cầu và điều phối luồng xử lý theo kiến trúc Serverless.
- **AI Processing:** Amazon Bedrock Agents điều phối Supervisor Agent, Document Agent và Researcher Agent để xử lý tài liệu học thuật.
- **Xử lý đa phương thức:** Claude 3.5 Sonnet hỗ trợ trích xuất văn bản, dịch ngữ cảnh, nhận diện công thức toán học và mô tả biểu đồ.
- **OCR dự phòng:** Amazon Textract được sử dụng khi tài liệu là bản scan chất lượng thấp hoặc có bố cục phức tạp.
- **Retrieval-Augmented Generation:** Titan Text Embeddings kết hợp Amazon S3 Vectors hỗ trợ tìm kiếm ngữ nghĩa và hỏi đáp theo nội dung tài liệu.
- **Lưu trữ:** Amazon S3 lưu PDF gốc, kết quả Markdown/HTML và dữ liệu vector; Amazon DynamoDB lưu metadata và trạng thái xử lý.
- **Bảo mật:** AWS IAM, Amazon Cognito, S3 Bucket Policy và AWS KMS giúp kiểm soát quyền truy cập và mã hóa dữ liệu.
- **Tự động hóa:** S3 Event Notifications kích hoạt Lambda Orchestrator ngay sau khi người dùng tải tài liệu lên. :contentReference[oaicite:1]{index=1} :contentReference[oaicite:2]{index=2}

#### Quy trình hoạt động tổng quát

Người dùng tải tài liệu PDF lên giao diện React. Ứng dụng gọi Amazon API Gateway để nhận presigned URL, sau đó tải tệp trực tiếp lên Amazon S3.
Khi tệp mới được tạo, S3 Event Notification kích hoạt AWS Lambda Orchestrator. Lambda gửi thông tin tài liệu đến Supervisor Agent trên Amazon Bedrock để đánh giá độ phức tạp và lựa chọn luồng xử lý phù hợp.
Đối với tài liệu thông thường, Document Agent sử dụng Claude 3.5 Sonnet để xử lý văn bản, bảng biểu, công thức toán học và hình ảnh. Đối với tài liệu scan chất lượng thấp, Supervisor Agent gọi Amazon Textract làm phương án dự phòng.
Sau khi xử lý, kết quả được đóng gói dưới dạng JSON, chuyển về Lambda Orchestrator, lưu thành tệp Markdown hoặc HTML trên Amazon S3 và cập nhật trạng thái xử lý trong Amazon DynamoDB. Kết quả được gửi về giao diện thông qua WebSocket hoặc REST API. :contentReference[oaicite:3]{index=3} :contentReference[oaicite:4]{index=4}

#### Nội dung

1. [Tổng quan về workshop](5.1-Workshop-overview/)
2. [Chuẩn bị](5.2-Prerequiste/)
3. [Truy cập đến S3 từ VPC](5.3-S3-vpc/)
4. [Truy cập đến S3 từ TTDL On-premises](5.4-S3-onprem/)
5. [VPC Endpoint Policies (làm thêm)](5.5-Policy/)
6. [Dọn dẹp tài nguyên](5.6-Cleanup/)

<p align="center">
  <img
    src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/Workshop.png"
    width="850"
    alt="Kiến trúc VietAI Scholar Assistant trên AWS">
</p>