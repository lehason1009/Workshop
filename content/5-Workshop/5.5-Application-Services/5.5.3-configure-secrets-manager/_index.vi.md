---
title : "IAM Role cho EC2"
date : 2026-01-01
weight : 3
chapter : false
pre : " <b> 5.5.3. </b> "
---

## IAM Role cho EC2

CloudCV không dùng access key dài hạn trên máy chủ. Gắn IAM Role vào EC2 để ứng dụng nhận thông tin xác thực tạm thời và gọi dịch vụ AWS theo quyền được cấp.

## Quyền cần thiết

| Tài nguyên | Quyền trong báo cáo |
| --- | --- |
| Bucket S3 của dự án | Liệt kê bucket; đọc, ghi và xóa object trong đúng bucket |
| Amazon Bedrock | Gọi đúng mô hình dùng cho trích xuất |

Giới hạn policy vào ARN bucket/object và model cần thiết; tránh quyền `*` nếu không bắt buộc. Không đưa access key vào image Docker, Git hoặc biến môi trường lâu dài.

## Gắn và kiểm tra Role

Gắn role vào instance profile của EC2, sau đó kiểm tra từ ứng dụng rằng có thể ghi/đọc một object thử trong bucket và gọi model. Nếu gặp lỗi AccessDenied, đối chiếu policy, bucket ARN, model ID và Region.

## Kết quả mong đợi

EC2 dùng credentials tạm thời từ IAM Role với quyền cần thiết cho S3 và Bedrock, không cần AWS access key tĩnh.