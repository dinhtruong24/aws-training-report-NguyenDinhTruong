---
title: "Blog 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---


# AGENTWATCH – GIÁM SÁT CHỦ ĐỘNG HẠ TẦNG AWS BẰNG AMBIENT AGENTS TRÊN AMAZON BEDROCK

Trong môi trường điện toán đám mây, số lượng Metrics, Logs và Alarms tăng rất nhanh khi hệ thống mở rộng. Việc theo dõi toàn bộ hạ tầng bằng phương pháp thủ công khiến đội ngũ vận hành mất nhiều thời gian và dễ bỏ sót các sự cố quan trọng. AgentWatch là giải pháp giám sát thông minh kết hợp Amazon Bedrock, AWS Lambda và Amazon CloudWatch để tự động phân tích dữ liệu vận hành và hỗ trợ phát hiện sự cố sớm.

## Tổng quan

AgentWatch hoạt động như một AI Agent chạy nền (Ambient Agent), liên tục thu thập dữ liệu từ Amazon CloudWatch và sử dụng Generative AI để phân tích tình trạng hệ thống. Thay vì phải kiểm tra từng Dashboard hoặc từng Alarm, kỹ sư vận hành sẽ nhận được các báo cáo tổng hợp cùng với những đề xuất xử lý phù hợp.

## Kiến trúc giải pháp

Giải pháp sử dụng nhiều dịch vụ AWS kết hợp với nhau:

- Amazon EventBridge lập lịch giám sát.
- AWS Lambda điều phối toàn bộ quy trình.
- Amazon Cognito xác thực yêu cầu.
- Amazon Bedrock AgentCore phân tích dữ liệu bằng AI.
- Amazon CloudWatch cung cấp Metrics, Logs và Alarms.
- Slack nhận báo cáo giám sát.

Kiến trúc này giúp tự động hóa quá trình giám sát mà không cần người quản trị theo dõi liên tục.

## Quy trình hoạt động

Quy trình giám sát gồm 5 bước chính.

### Bước 1 – Kích hoạt giám sát

Amazon EventBridge tự động kích hoạt AWS Lambda theo chu kỳ để bắt đầu quá trình giám sát.

### Bước 2 – Thu thập dữ liệu

Lambda lấy Metrics, Logs và Alarms từ Amazon CloudWatch để thu thập trạng thái hoạt động của hệ thống.

### Bước 3 – Phân tích bằng Amazon Bedrock

Dữ liệu được gửi đến Amazon Bedrock AgentCore để AI phân tích sức khỏe hệ thống, phát hiện bất thường và xác định nguyên nhân có thể xảy ra.

### Bước 4 – Tạo báo cáo

Sau khi phân tích, Lambda tạo báo cáo bao gồm:

- Tình trạng hạ tầng.
- Các cảnh báo quan trọng.
- Nguyên nhân có thể xảy ra.
- Đề xuất hướng xử lý.

Báo cáo được gửi trực tiếp đến Slack để đội ngũ DevOps theo dõi.

### Bước 5 – Xác nhận của người quản trị

Đối với các thao tác có ảnh hưởng đến hệ thống, AgentWatch yêu cầu người quản trị phê duyệt trước khi thực hiện nhằm đảm bảo an toàn.

## Lợi ích

Giải pháp mang lại nhiều lợi ích:

- Tự động phân tích Metrics, Logs và Alarms.
- Phát hiện sớm các dấu hiệu bất thường.
- Giảm công việc giám sát thủ công.
- Rút ngắn thời gian xử lý sự cố.
- Ứng dụng Generative AI trong vận hành hệ thống.
- Hỗ trợ đội ngũ DevOps đưa ra quyết định nhanh hơn.

## Kết luận

AgentWatch là ví dụ điển hình về việc ứng dụng Amazon Bedrock trong giám sát hạ tầng AWS. Bằng cách kết hợp AI với các dịch vụ như Lambda, CloudWatch và EventBridge, giải pháp giúp tự động phân tích dữ liệu vận hành, phát hiện sự cố sớm và nâng cao hiệu quả quản trị hệ thống, đồng thời vẫn đảm bảo sự kiểm soát của con người đối với các thao tác quan trọng.

<p align="center">
  <img src="https://dinhtruong24.github.io/aws-training-report-NguyenDinhTruong/images/3-BlogsPosted/blog2-agentwatch.png" width="700" alt="Kiến trúc AgentWatch">
</p>

<p align="center">
<i>Hình 2. Kiến trúc AgentWatch giám sát chủ động hạ tầng AWS bằng Amazon Bedrock.</i>
</p>

<p align="center">
<strong>Bài viết tham khảo:</strong>
<a href="https://aws.amazon.com/blogs/machine-learning/agentwatch-proactive-aws-monitoring-with-ambient-agents/">
AWS Machine Learning Blog
</a>
</p>

<p align="center">
<strong>Bài đăng cộng đồng:</strong>
<a href="https://www.facebook.com/groups/awsstudygroupfcj/posts/2190168085081485">
AWS Study Group – Facebook
</a>
</p>