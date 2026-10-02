---
title : "Bảo vệ API và cấu hình"
date : 2026-01-01
weight : 8
chapter : false
pre : " <b> 5.8. </b> "
---

### Mục tiêu

Cấu hình xác thực API và truyền thông tin chạy CloudCV an toàn.

---

## 1. Tổng quan

CloudCV xác thực các endpoint bằng header `X-API-Key`, ngoại trừ `/health`. Khóa API và tên bucket được truyền vào container qua biến môi trường. Báo cáo truy cập API qua địa chỉ EC2 và cổng 8000; không ghi nhận tên miền, chứng chỉ ACM hay HTTPS.

---

## 2. Nội dung thực hành

Thực hiện phần sau:

- **5.8.1 Xác thực request và quản lý cấu hình**

---

## 3. Kết quả mong đợi

Sau khi hoàn thành chương này, bạn sẽ có:

- Request thiếu/sai API key bị từ chối với mã 401.
- Bí mật không được ghi cứng trong mã nguồn hoặc Docker image.
- Nắm rõ giới hạn hiện tại: báo cáo không triển khai HTTPS/domain.