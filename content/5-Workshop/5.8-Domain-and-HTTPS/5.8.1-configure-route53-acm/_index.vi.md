---
title : "Xác thực request và quản lý cấu hình"
date : 2026-01-01
weight : 1
chapter : false
pre : " <b> 5.8.1. </b> "
---

## Xác thực API

Mọi endpoint trừ `GET /health` yêu cầu header `X-API-Key`. Thiếu khóa hoặc gửi giá trị sai phải trả HTTP 401. Bảo vệ khóa API như credential: chỉ truyền qua cấu hình runtime, không commit vào Git, log hoặc image.

## Biến môi trường

Ứng dụng nhận API key và tên bucket qua biến môi trường. Tên biến cụ thể phụ thuộc vào mã nguồn; kiểm tra cấu hình dự án trước khi chạy. AWS credentials không cần đưa vào biến môi trường vì EC2 dùng IAM Role.

## Phạm vi mạng và HTTPS

Báo cáo dùng Elastic IP và cổng 8000 để kiểm thử API; không ghi nhận Route 53, ACM, HTTPS hay ALB. Không coi endpoint HTTP công khai là cấu hình production. Khi mở rộng, cần bổ sung TLS và giới hạn truy cập theo yêu cầu triển khai.

## Kết quả mong đợi

API key được xác thực đúng, cấu hình nhạy cảm không nằm trong mã nguồn và phạm vi bảo vệ mạng hiện tại được hiểu rõ.