---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---


# Bảo vệ thông tin đăng nhập Amazon RDS cho AWS Lambda bằng AWS Secrets Manager

Trong các ứng dụng Serverless, AWS Lambda thường cần truy cập cơ sở dữ liệu để đọc hoặc xử lý dữ liệu. Một cách triển khai không an toàn là lưu trực tiếp tên đăng nhập và mật khẩu trong mã nguồn hoặc biến môi trường của Lambda. Cách làm này có thể khiến thông tin nhạy cảm bị lộ khi mã nguồn được chia sẻ, nhật ký được kiểm tra hoặc cấu hình ứng dụng bị truy cập trái phép.

Giải pháp phù hợp hơn là lưu trữ thông tin đăng nhập trong **AWS Secrets Manager**. Khi Lambda cần kết nối đến Amazon RDS, hàm sẽ gọi API của Secrets Manager để lấy bí mật tại thời điểm thực thi. Nhờ đó, mật khẩu không cần xuất hiện trực tiếp trong mã nguồn.

## Kiến trúc giải pháp

Luồng xử lý của hệ thống được thực hiện như sau:

1. Người dùng gửi yêu cầu đến REST API được triển khai bằng Amazon API Gateway.
2. API Gateway kích hoạt hàm AWS Lambda.
3. Lambda sử dụng IAM Role để yêu cầu thông tin đăng nhập từ AWS Secrets Manager.
4. Secrets Manager trả về tên người dùng và mật khẩu đã được bảo vệ.
5. Lambda sử dụng thông tin này để kết nối đến Amazon RDS for MySQL.
6. Kết quả truy vấn được gửi ngược lại cho người dùng thông qua API Gateway.

## Các thành phần chính
### Amazon API Gateway

Amazon API Gateway cung cấp REST API để nhận yêu cầu từ người dùng và chuyển yêu cầu đến Lambda. Dịch vụ này đóng vai trò là điểm truy cập của ứng dụng nhưng không trực tiếp lưu trữ thông tin đăng nhập cơ sở dữ liệu.

### AWS Lambda

Lambda chứa logic xử lý của ứng dụng. Trước khi truy vấn cơ sở dữ liệu, Lambda gọi API GetSecretValue của Secrets Manager để lấy thông tin xác thực.
IAM Role của Lambda chỉ nên được cấp quyền truy cập đúng bí mật cần sử dụng theo nguyên tắc đặc quyền tối thiểu.

### AWS Secrets Manager

Secrets Manager lưu trữ tên đăng nhập và mật khẩu của cơ sở dữ liệu dưới dạng bí mật được mã hóa. Lambda chỉ lấy bí mật trong thời gian chạy, thay vì lưu mật khẩu trong mã nguồn hoặc biến môi trường.

### Amazon RDS

Amazon RDS for MySQL lưu trữ dữ liệu của ứng dụng. Cơ sở dữ liệu được cấu hình không cho phép truy cập công khai và chỉ chấp nhận kết nối từ các tài nguyên được cấp quyền.

### AWS CloudFormation

CloudFormation được sử dụng để triển khai tự động các tài nguyên như:

- Amazon RDS.
- AWS Secrets Manager.
- AWS Lambda.
- Amazon API Gateway.
- IAM Roles và IAM Policies.

CloudFormation sử dụng dynamic reference để lấy mật khẩu từ Secrets Manager khi tạo cơ sở dữ liệu. Giá trị mật khẩu không bị ghi trực tiếp vào template hoặc nhật ký triển khai.

### Quản lý và xoay vòng bí mật

Một lợi ích quan trọng của AWS Secrets Manager là khả năng tự động xoay vòng mật khẩu.

Trong giải pháp này, lịch xoay vòng có thể được cấu hình theo chu kỳ, ví dụ 30 ngày. Khi đến thời điểm xoay vòng, một Lambda rotation function sẽ:

1. Tạo mật khẩu mới.
2. Cập nhật mật khẩu trong Amazon RDS.
3. Cập nhật giá trị mới trong Secrets Manager.
4. Kiểm tra thông tin đăng nhập mới.
5. Đánh dấu phiên bản bí mật mới là phiên bản hiện tại.

Ứng dụng không cần chỉnh sửa mã nguồn sau khi mật khẩu thay đổi, vì Lambda luôn lấy giá trị mới nhất từ Secrets Manager.

### Kiểm tra giải pháp

Sau khi triển khai CloudFormation stack, có thể kiểm tra bằng cách mở API endpoint được tạo trong phần Outputs.

Khi gửi yêu cầu đến endpoint:

- API Gateway kích hoạt Lambda.
- Lambda lấy bí mật từ Secrets Manager.
- Lambda kết nối đến RDS MySQL.
- Câu truy vấn được thực hiện.
- Kết quả được trả về trình duyệt.

Ngoài ra, trong phần biến môi trường của Lambda sẽ không xuất hiện mật khẩu cơ sở dữ liệu. Lambda chỉ lưu các thông tin không nhạy cảm như tên secret, địa chỉ RDS, tên database và tên người dùng.

### Lợi ích của giải pháp
- Không lưu mật khẩu trực tiếp trong mã nguồn.
- Hạn chế lộ thông tin qua biến môi trường.
- Tự động xoay vòng thông tin xác thực.
- Quản lý quyền truy cập bằng IAM.
- Tự động triển khai hạ tầng bằng CloudFormation.
- Phù hợp với các ứng dụng Serverless cần truy cập cơ sở dữ liệu.
- Giảm khối lượng công việc quản lý mật khẩu thủ công.

### Kết luận

Việc kết hợp AWS Lambda, AWS Secrets Manager và Amazon RDS giúp ứng dụng truy cập cơ sở dữ liệu an toàn hơn. Secrets Manager quản lý vòng đời của thông tin xác thực, trong khi Lambda chỉ lấy bí mật khi cần sử dụng.

Giải pháp này giúp loại bỏ mật khẩu hardcode, hỗ trợ tự động xoay vòng và tăng khả năng kiểm soát quyền truy cập trong hệ thống AWS.

<p align="center">
  <img
    src="https://dinhtruong24.github.io/aws-training-report-NguyenDinhTruong/images/3-BlogsPosted/blog1-architecture.png"
    width="700"
    alt="Kiến trúc AWS Secrets Manager">
</p>

<p align="center">
  <em>Hình 1. Kiến trúc quản lý an toàn thông tin xác thực cơ sở dữ liệu Amazon RDS bằng AWS Secrets Manager.</em>
</p>

<p align="center">
  <strong>Bài viết tham khảo:</strong>
  <a href="https://aws.amazon.com/blogs/security/how-to-securely-provide-database-credentials-to-lambda-functions-by-using-aws-secrets-manager/">
    AWS Security Blog
  </a>
</p>

<p align="center">
  <strong>Bài đăng cộng đồng:</strong>
  <a href="https://www.facebook.com/groups/awsstudygroupfcj/posts/2187144322050528">
    AWS Study Group – Facebook
  </a>
</p>