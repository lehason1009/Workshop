---
title : "Đóng gói ứng dụng"
date : 2026-01-01
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

### Mục tiêu

Đóng gói API FastAPI, Docling và các thư viện cần thiết thành Docker image để chạy trên EC2.

---

## 1. Tổng quan

CloudCV dùng Python 3.12. Image cài Docling cùng bản PyTorch chỉ chạy CPU và tải trước các model phân tích bố cục cần cho Docling. Báo cáo triển khai image trực tiếp trên EC2, không dùng Amazon ECR.

---

## 2. Nội dung thực hành

Thực hiện lần lượt các phần sau:

- **5.6.1 Build Docker Image**
- **5.6.2 Chuẩn bị container chạy trên EC2**

---

## 3. Kết quả mong đợi

Sau khi hoàn thành chương này, bạn sẽ có:

- Docker image đóng gói API và phụ thuộc xử lý tài liệu.
- Model Docling có sẵn khi container khởi động.
- Cấu hình runtime sẵn sàng cho triển khai trực tiếp trên EC2.