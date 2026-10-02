---
title : "Tổng quan Workshop"
date : 2026-01-01
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

### Mục tiêu

Giới thiệu kiến trúc, luồng xử lý và kết quả triển khai **CloudCV**: một REST API backend phân tích CV bằng Docling và mô hình ngôn ngữ trên Amazon Bedrock.

## 1. Bài toán và giải pháp

Client gửi tệp PDF hoặc DOCX đến API. **FastAPI** kiểm tra yêu cầu, **Docling** chuyển tài liệu thành Markdown, sau đó ứng dụng gửi nội dung cùng prompt đến mô hình trên **Amazon Bedrock**. Dữ liệu trích xuất được kiểm tra theo schema **Pydantic** trước khi trả về cho client.

Đây là dịch vụ backend, không có giao diện người dùng. Các thao tác được thực hiện qua Postman, curl hoặc Swagger UI do FastAPI cung cấp.

## 2. Kiến trúc và lưu trữ

- Một container Docker chạy API trên máy ảo **Amazon EC2**.
- **Amazon S3** lưu tệp CV gốc và kết quả JSON; bucket được cấu hình riêng tư.
- **Amazon Bedrock** cung cấp mô hình ngôn ngữ để trích xuất thông tin.
- **IAM Role** gắn với EC2 cấp quyền giới hạn để truy cập đúng bucket và gọi mô hình.
- **VPC/Security Group** kiểm soát kết nối đến máy ảo; AWS Budgets cảnh báo chi phí.

## 3. Luồng xử lý

1. Client gửi CV cùng header `X-API-Key` đến `POST /cvs`.
2. API xác thực khóa, kiểm tra định dạng và giới hạn dung lượng tệp.
3. Docling chuyển PDF/DOCX thành Markdown có cấu trúc.
4. Ứng dụng gửi nội dung đến Bedrock; Pydantic xác thực kết quả JSON.
5. CV gốc và JSON được lưu trên S3; API trả mã CV và kết quả.
6. Các endpoint khác liệt kê, truy xuất hoặc xóa CV đã xử lý.

## 4. Phạm vi triển khai

Báo cáo ghi nhận EC2, Docker, FastAPI, Docling, Bedrock, S3, IAM, VPC/Security Group, GitHub và AWS Budgets. ECS/Fargate, ECR, ALB, Route 53, ACM, CodeBuild và MongoDB Atlas không thuộc kiến trúc CloudCV đã triển khai.

## 5. Kết quả

API xử lý được CV PDF và DOCX; kiểm thử ghi nhận phản hồi 201 khi thành công, 401 khi API key thiếu/sai, 400 với định dạng không hỗ trợ, 413 với tệp trên 5 MB và 404 với mã CV không tồn tại. Chất lượng trích xuất mới được so sánh thủ công trên một tập CV mẫu nhỏ, chưa có đánh giá định lượng.