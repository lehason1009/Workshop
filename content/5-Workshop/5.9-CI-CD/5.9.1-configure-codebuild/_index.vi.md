---
title : "Quy trình phát hành thủ công"
date : 2026-01-01
weight : 1
chapter : false
pre : " <b> 5.9.1. </b> "
---

## Quy trình phát hành được ghi nhận

1. Cập nhật và kiểm tra mã nguồn, sau đó đẩy thay đổi lên GitHub.
2. Kết nối đến EC2 qua SSH.
3. Lấy phiên bản mã nguồn cần triển khai.
4. Build lại image Docker theo Dockerfile của dự án.
5. Khởi động container với cấu hình runtime và kiểm tra `/health`.

Container được chạy với chính sách restart để tự khởi động lại cùng Docker. API key phải được cung cấp bên ngoài repository; IAM Role của EC2 cấp quyền S3/Bedrock.

## Giới hạn

Các bước trên là thao tác thủ công. Báo cáo không ghi nhận webhook, AWS CodeBuild, ECR hay tự động rollback. Trước khi thay đổi, cần giữ lại image đang chạy hoặc ghi nhận phiên bản commit để có thể quay lại khi cần.

## Kết quả mong đợi

Mã nguồn và phiên bản triển khai có thể đối chiếu được; container mới chạy ổn định trước khi coi lần phát hành hoàn tất.