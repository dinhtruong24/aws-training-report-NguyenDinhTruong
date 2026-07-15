---
title: "Worklog Tuần 9"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9:

* Làm chủ các dịch vụ AI ứng dụng thông qua việc tích lũy kinh nghiệm thực hành với nhóm dịch vụ xử lý âm thanh của AWS (Chuyển đổi văn bản thành giọng nói và ngược lại) cùng các công cụ thị giác máy tính.
* Tìm hiểu sâu về Trí tuệ nhân tạo tạo sinh (Generative AI) cùng các Mô hình ngôn ngữ lớn (LLM), đồng thời nắm bắt phương thức đưa LLM vào vận hành trong các hệ thống doanh nghiệp thực tế.
* Nghiên cứu nền tảng học máy toàn diện Amazon SageMaker và làm quen với không gian làm việc Jupyter Notebook để tiến hành xây dựng cũng như huấn luyện các mô hình ML.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Khảo sát các giải pháp xử lý ngôn ngữ và âm thanh với Amazon Polly và Amazon Transcribe; học cách ứng dụng Polly để chuyển đổi dữ liệu chữ viết thành giọng đọc tự nhiên với nhiều tùy chọn ngôn ngữ, đồng thời sử dụng Transcribe nhằm bóc tách và chuyển các tệp tin âm thanh, lời nói thành văn bản một cách chính xác.  | 29/06/2026   | 29/06/2026      | https://000072.awsstudygroup.com/ https://000073.awsstudygroup.com/ |
| 3   | - Nghiên cứu các mô hình kiến trúc tích hợp LLM trong doanh nghiệp; tìm hiểu các giải pháp kỹ thuật để nhúng các Mô hình ngôn ngữ lớn (LLMs) vào các phần mềm thực tế, đồng thời nghiên cứu sâu kỹ thuật RAG (Retrieval-Augmented Generation) giúp khai thác an toàn và bảo mật các kho tri thức nội bộ.   | 30/06/2026   | 30/06/2026      | https://000105.awsstudygroup.com/ https://000106.awsstudygroup.com/ |
| 4   | - Phân tích cấu trúc hệ thống của Amazon SageMaker; tiếp cận giải pháp học máy khép kín E2E, tập trung tìm hiểu các cấu phần cốt lõi bao gồm không gian SageMaker Studio, các thực thể Notebook Instances, các thuật toán được tối ưu sẵn và quy trình triển khai Endpoint để phục vụ dự đoán. | 01/07/2026   | 01/07/2026      | https://000200.awsstudygroup.com/ |
| 5   | - Tự động hóa quy trình phân loại và dán nhãn hình ảnh bằng Python phối hợp với Amazon Rekognition; viết mã nguồn Python kết nối trực tiếp với kho lưu trữ Amazon S3, gọi API của Rekognition để quét và tự động tạo các thẻ mô tả (tags) cho hàng loạt ảnh cùng lúc.    | 02/07/2026   | 02/07/2026      | https://000200.awsstudygroup.com/ |
| 6   | - Hoàn thành nội dung Blog 1 & Blog 2; đồng thời thực hành quy trình huấn luyện mô hình trên SageMaker Notebook; khởi tạo một Notebook Instance, thao tác trong môi trường Jupyter để làm sạch và tiền xử lý tập dữ liệu mẫu, sau đó tiến hành chạy thực tế quy trình huấn luyện một mô hình phân loại cơ bản.      | 03/07/2026   | 03/07/2026      | https://000200.awsstudygroup.com/ |


### Kết quả đạt được tuần 9:

* Ứng dụng thành thạo dịch vụ âm thanh & Thị giác máy tính: Làm chủ quy trình chuyển đổi song hướng giữa văn bản và giọng nói thông qua Polly và Transcribe, đồng thời xây dựng thành công mã nguồn Python tự động hóa việc quét và gán nhãn dữ liệu hình ảnh quy mô lớn dựa trên Amazon Rekognition.

* Nắm bắt tư duy GenAI & Kiến trúc RAG: Thấu suốt phương pháp luận khi tích hợp LLM vào hệ thống doanh nghiệp, hiểu rõ cách vận hành của kỹ thuật RAG nhằm tối ưu hóa việc truy xuất dữ liệu nội bộ bảo mật mà không làm rò rỉ thông tin.

* Vận hành công cụ Machine Learning chuyên sâu: Làm chủ các thao tác nền tảng trên Amazon SageMaker, hiện thực hóa việc chuẩn bị dữ liệu và huấn luyện thành công mô hình phân loại trên môi trường Jupyter Notebook, đồng thời hoàn tất nội dung tài liệu kỹ thuật cho hai bài Blog chuyên ngành.

### Đánh giá tuần 9:
* Trong ngày Thứ Sáu, khi thực hiện tiền xử lý một tập dữ liệu lớn trực tiếp bên trong SageMaker Notebook Instance để chuẩn bị huấn luyện mô hình, hệ thống ban đầu đã bị treo và báo lỗi tràn bộ nhớ (Out of Memory) do dung lượng của Instance được cấu hình mặc định ở mức thấp. Đây là một bài học kinh nghiệm thực tiễn đắt giá về việc ước lượng tài nguyên tính toán cho các tác vụ Data Science. Tôi đã xử lý triệt để bằng cách tạm dừng Instance, thực hiện nâng cấp cấu hình phần cứng (Instance Type) lên dòng tối ưu hơn, đồng thời tối ưu lại mã nguồn bằng cách chia nhỏ tập dữ liệu thành các lô (batches) nhỏ hơn khi xử lý.


