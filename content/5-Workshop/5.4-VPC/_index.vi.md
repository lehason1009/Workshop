---
title : "Hạ tầng mạng"
date : 2026-01-01
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

### Mục tiêu

Mô tả cách EC2 của CloudCV kết nối Internet và cách Security Group giới hạn lưu lượng vào máy chủ.

---

## 1. Tổng quan

CloudCV chạy trên một EC2 instance trong public subnet để client có thể gọi API. Elastic IP giữ địa chỉ máy chủ ổn định; Security Group cho phép SSH từ IP quản trị và cổng 8000 cho API. Báo cáo không nêu CIDR, Region hay cấu hình NAT/ALB, vì vậy các trang con tập trung vào những lựa chọn đã được ghi nhận thay vì đưa ra thông số mạng giả định.

---

---

## 3. Nội dung thực hành

Tham khảo các phần sau:

- **5.4.1 Tạo VPC**
- **5.4.2 Cấu hình mạng**

---

## 4. Kết quả mong đợi

Sau khi hoàn thành chương này, bạn sẽ có:

- Nắm được vai trò của VPC/public subnet trong đường truy cập đến EC2.
- Hiểu Security Group cần giới hạn SSH và cho phép cổng API.
- Ghi lại CIDR, Region và quy tắc thực tế của tài khoản trước khi triển khai.