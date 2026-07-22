---
title : "Lab 1: Xây dựng nền tảng mạng"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b>5.3. </b> "
---

Lab đầu tiên tập trung vào việc xây dựng hạ tầng mạng cho toàn bộ hệ thống trên AWS. Đây là bước quan trọng nhằm tạo ra một môi trường mạng riêng biệt, an toàn và có khả năng mở rộng cho các thành phần của ứng dụng.

Trong Lab này, chúng ta sẽ triển khai một **Amazon Virtual Private Cloud (VPC)** với kiến trúc nhiều lớp, bao gồm các Public Subnets và Private Subnets được phân bố trên hai Availability Zones nhằm tăng tính sẵn sàng và khả năng chịu lỗi của hệ thống.

<p align="center">
    <img src="/aws-training-report-NguyenDinhTruong/images/5-Workshop/5.3-network/5.3-network-plan.png" width="900">
</p>

<p align="center">
<i>Hình 5.3. Kiến trúc mạng và kế hoạch phân chia CIDR của hệ thống.</i>
</p>

---

## Mục tiêu của Lab

Sau khi hoàn thành Lab này, bạn sẽ thực hiện được các nội dung sau:

- Tạo Amazon VPC cho hệ thống.
- Cấu hình DNS Resolution và DNS Hostnames.
- Tạo các Public Subnets và Private Subnets.
- Cấu hình Internet Gateway.
- Tạo các Route Tables cho từng tầng mạng.
- Triển khai NAT Gateway để các Private Subnets có thể truy cập Internet.
- Kiểm tra toàn bộ cấu hình mạng trước khi triển khai các dịch vụ AWS tiếp theo.

---

## Nội dung của Lab

Lab được chia thành các phần nhỏ theo trình tự sau:

1. **5.3.1 Configure VPC**
   - Tạo VPC.
   - Kiểm tra cấu hình VPC.
   - Bật DNS Resolution và DNS Hostnames.

2. **5.3.2 Create Subnets**
   - Tạo Public Subnets.
   - Tạo Private Application Subnets.
   - Tạo Private Database Subnets.

3. **5.3.3 Configure Internet Gateway**
   - Tạo Internet Gateway.
   - Gắn Internet Gateway vào VPC.

4. **5.3.4 Configure Route Tables**
   - Tạo Public Route Table.
   - Tạo Private Application Route Table.
   - Tạo Database Route Table.
   - Associate Route Tables với các Subnets.

5. **5.3.5 Create NAT Gateway**
   - Tạo NAT Gateway.
   - Kiểm tra kết nối Internet cho Private Subnets.

---

Sau khi hoàn thành Lab 1, toàn bộ hạ tầng mạng sẽ sẵn sàng để triển khai các thành phần bảo mật, lưu trữ và tính toán trong các Lab tiếp theo.