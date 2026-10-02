---
title : "Build và chạy CloudCV"
date : 2026-01-01
weight : 2
chapter : false
pre : " <b> 5.7.2. </b> "
---

## Cài đặt Docker và lấy mã nguồn

Kết nối EC2 qua SSH, cài Docker trên Amazon Linux 2023 và clone repository CloudCV từ GitHub. Build image theo Dockerfile của dự án:

```bash
docker build -t cloudcv .
```

## Khởi chạy API

Truyền khóa API và tên bucket qua biến môi trường, sau đó chạy container với chính sách tự khởi động lại. Tên biến phải khớp với mã nguồn; không ghi bí mật vào Dockerfile hoặc Git. EC2 lấy quyền S3/Bedrock từ IAM Role.

```bash
docker run -d --restart unless-stopped --name cloudcv -p 8000:8000 --env-file <runtime-env-file> cloudcv
```

## Kiểm tra triển khai

- Xem trạng thái container bằng `docker ps`.
- Đọc log bằng `docker logs cloudcv`.
- Gọi `http://<EC2_PUBLIC_IP>:8000/health` từ máy client.
- Mở Swagger UI tại `/docs` để kiểm tra endpoint.

## Kết quả mong đợi

Container tự chạy lại sau khi EC2 khởi động; API phản hồi trên cổng 8000 và có thể truy cập S3/Bedrock bằng IAM Role.