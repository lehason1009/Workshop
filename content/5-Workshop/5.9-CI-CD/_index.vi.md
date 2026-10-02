---
title : "Mã nguồn và phát hành thủ công"
date : 2026-01-01
weight : 9
chapter : false
pre : " <b> 5.9. </b> "
---

### Mục tiêu

Mô tả cách quản lý mã CloudCV trên GitHub và triển khai thủ công lên EC2.

---

## 1. Tổng quan

GitHub được dùng để quản lý mã nguồn; báo cáo không triển khai AWS CodeBuild hay pipeline CI/CD. Quy trình ghi nhận là kết nối EC2 qua SSH, lấy mã nguồn, build Docker image và khởi động lại container.

---

## 2. Nội dung thực hành

Thực hiện phần sau:

- **5.9.1 Quy trình phát hành thủ công**

---

## 3. Kết quả mong đợi

Sau khi hoàn thành chương này, bạn sẽ có:

- Thay đổi mã được quản lý trên GitHub.
- Quy trình triển khai thủ công có thể lặp lại trên EC2.
- Không nhầm quy trình này với CI/CD tự động.