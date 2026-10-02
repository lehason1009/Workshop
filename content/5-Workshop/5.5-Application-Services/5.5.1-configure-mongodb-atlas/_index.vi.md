---
title : "Tích hợp Amazon Bedrock"
date : 2026-01-01
weight : 1
chapter : false
pre : " <b> 5.5.1. </b> "
---

## Tích hợp Amazon Bedrock

CloudCV gọi mô hình ngôn ngữ trên Amazon Bedrock để chuyển nội dung Markdown của CV thành JSON theo schema Pydantic. Báo cáo không nêu model ID cụ thể; cần chọn model đã được cấp quyền trong Region của tài khoản.

## Luồng gọi mô hình

Ứng dụng dùng Converse API của boto3. Nhiệt độ được đặt bằng `0` để giảm tính ngẫu nhiên. Prompt yêu cầu chỉ dùng thông tin có trong CV, không tự điền dữ liệu còn thiếu và chuẩn hóa ngày tháng về dạng năm-tháng.

## Kiểm tra phản hồi

Chuyển nội dung phản hồi thành JSON rồi xác thực bằng Pydantic trước khi lưu hoặc trả kết quả. Nếu JSON không khớp schema, ứng dụng thử lại một lần với thông báo lỗi xác thực. Gọi mô hình bằng IAM Role của EC2; không nhúng AWS access key trong mã nguồn.

## Kết quả mong đợi

EC2 có quyền gọi đúng model và ứng dụng nhận được kết quả JSON hợp lệ theo schema CloudCV.