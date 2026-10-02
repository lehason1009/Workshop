---
title : "Chuẩn bị container chạy trên EC2"
date : 2026-01-01
weight : 2
chapter : false
pre : " <b> 5.6.2. </b> "
---

## Chuẩn bị container chạy trên EC2

Báo cáo triển khai trực tiếp trên EC2 nên không cần ECR. Sau khi cài Docker trên Amazon Linux 2023 và lấy mã nguồn từ GitHub, build image trên máy chủ:

```bash
docker build -t cloudcv .
```

## Cấu hình runtime

Truyền API key và tên bucket bằng biến môi trường khi chạy container. Tên biến chính xác cần lấy từ mã nguồn; không commit giá trị bí mật vào Git. EC2 lấy quyền S3/Bedrock qua IAM Role, không dùng access key dài hạn.

Ví dụ cấu trúc lệnh (điều chỉnh cổng và tệp cấu hình theo dự án):

```bash
docker run -d --restart unless-stopped --name cloudcv -p 8000:8000 --env-file <runtime-env-file> cloudcv
```

## Kiểm tra container

Xác nhận container ở trạng thái chạy, xem log khởi động và gọi `/health` qua cổng 8000. Chính sách restart giúp container chạy lại sau khi Docker/EC2 khởi động lại.

## Kết quả mong đợi

Image được build và chạy trên EC2; ứng dụng nhận cấu hình khi khởi chạy, còn quyền AWS được lấy từ IAM Role.