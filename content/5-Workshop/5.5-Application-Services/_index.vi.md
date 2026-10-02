---
title : "Dịch vụ ứng dụng"
date : 2026-01-01
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

### Mục tiêu

Cấu hình ba dịch vụ AWS chính mà CloudCV sử dụng: Bedrock, S3 và IAM.

---

## 1. Tổng quan

CloudCV dùng Amazon Bedrock để trích xuất dữ liệu CV, Amazon S3 để lưu CV gốc/kết quả JSON và IAM Role gắn vào EC2 để cấp quyền gọi Bedrock cũng như truy cập bucket. Dự án không dùng MongoDB Atlas hay AWS Secrets Manager theo báo cáo.

---

## 2. Nội dung thực hành

Thực hiện lần lượt các phần sau:

- **5.5.1 Tích hợp Amazon Bedrock**
- **5.5.2 Cấu hình Amazon S3**
- **5.5.3 IAM Role cho EC2**

---

## 3. Kết quả mong đợi

Sau khi hoàn thành chương này, bạn sẽ có:

- Nắm được vai trò của Bedrock, S3 và IAM trong luồng xử lý.
- Quyền EC2 được giới hạn vào bucket và mô hình cần dùng.
- Tệp CV và kết quả được lưu trong bucket riêng tư.