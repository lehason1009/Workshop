---
title : "Triển khai ứng dụng"
date : 2026-01-01
weight : 7
chapter : false
pre : " <b> 5.7. </b> "
---

### Mục tiêu

Triển khai container CloudCV trên máy ảo Amazon EC2.

---

## 1. Tổng quan

CloudCV chạy trong Docker trên Amazon Linux 2023. Báo cáo sử dụng instance `t3.medium`, EBS 20 GB và Elastic IP; đây là cấu hình của dự án được mô tả, không phải yêu cầu cố định cho mọi triển khai. EC2 gắn IAM Role để truy cập S3/Bedrock.

---

## 2. Nội dung thực hành

Thực hiện lần lượt các phần sau:

- **5.7.1 Chuẩn bị EC2 và địa chỉ truy cập**
- **5.7.2 Build và chạy CloudCV**

---

## 3. Kết quả mong đợi

Sau khi hoàn thành chương này, bạn sẽ có:

- EC2 chạy container CloudCV với chính sách tự khởi động lại.
- API `/health` phản hồi qua Elastic IP trên cổng 8000.
- Dữ liệu được lưu trên S3 và quyền dịch vụ đến từ IAM Role.