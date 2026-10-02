---
title : "Chuẩn bị EC2 và địa chỉ truy cập"
date : 2026-01-01
weight : 1
chapter : false
pre : " <b> 5.7.1. </b> "
---

## Cấu hình EC2

Báo cáo triển khai CloudCV trên Amazon Linux 2023 với instance `t3.medium` và ổ EBS 20 GB. Tạo hoặc chọn key pair, gắn IAM Role có quyền S3/Bedrock, đặt instance trong public subnet và gắn Elastic IP để địa chỉ không đổi khi khởi động lại.

## Quy tắc Security Group

| Cổng | Nguồn | Mục đích |
| --- | --- | --- |
| 22 | IP công khai của quản trị viên | SSH |
| 8000 | Client kiểm thử | REST API |

Chỉ cho phép SSH từ IP quản trị. Cổng 8000 được dùng trong cấu hình báo cáo; giới hạn nguồn ở môi trường thực tế nếu có thể.

## Kiểm tra trước khi cài đặt

- Instance ở trạng thái running và có Elastic IP gắn đúng.
- IAM Role được gắn qua instance profile.
- Có thể SSH đến EC2 từ IP đã cho phép.
- Security Group cho phép API trên cổng 8000.

## Kết quả mong đợi

EC2 có địa chỉ ổn định, quyền truy cập AWS qua IAM Role và kết nối mạng cần thiết để cài/chạy container.