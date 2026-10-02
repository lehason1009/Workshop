---
title : "Cấu hình mạng"
date : 2026-01-01
weight : 2
chapter : false
pre : " <b> 5.4.2. </b> "
---

## Đường truy cập đến EC2

Trong cấu hình được mô tả ở báo cáo, EC2 nằm trong public subnet và dùng Elastic IP để client có thể tiếp cận API trên cổng `8000`. Route từ subnet ra Internet cần Internet Gateway. Không cần tạo private subnet, NAT Gateway hay ALB cho kiến trúc CloudCV đã triển khai.

## Security Group

Security Group gắn với EC2 có các quy tắc inbound sau:

| Giao thức/cổng | Nguồn | Mục đích |
| --- | --- | --- |
| TCP 22 | Địa chỉ IP quản trị | SSH để cài đặt và vận hành máy |
| TCP 8000 | Client cần gọi API | Truy cập FastAPI |

Trong báo cáo, cổng 22 chỉ mở cho IP của người triển khai; cổng 8000 được mở để kiểm thử API. Với môi trường dùng thực tế, nên giới hạn nguồn truy cập API theo yêu cầu và đặt thêm lớp bảo vệ phù hợp. Không mở SSH cho `0.0.0.0/0`.

## Kiểm tra kết nối

- Xác nhận EC2 ở đúng VPC/public subnet và có Elastic IP được gắn.
- Kiểm tra route ra Internet và trạng thái instance.
- Từ máy client, gọi `http://<EC2_PUBLIC_IP>:8000/health`.
- Nếu không kết nối được, kiểm tra Security Group, địa chỉ IP và trạng thái ứng dụng/container.

## Kết quả mong đợi

Máy chủ EC2 có thể được quản trị qua SSH từ IP cho phép và API có thể được gọi qua cổng 8000. Các CIDR và địa chỉ cụ thể cần lấy từ tài khoản đang triển khai.