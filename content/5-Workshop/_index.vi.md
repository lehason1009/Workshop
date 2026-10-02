---
title: "Workshop"
date: 2026-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# CloudCV: API phân tích CV trên AWS

#### Tổng quan

Phần này trình bày quá trình xây dựng và triển khai **CloudCV**, một REST API backend nhận CV định dạng PDF hoặc DOCX, trích xuất nội dung và trả về dữ liệu JSON có cấu trúc.

Ứng dụng được viết bằng **FastAPI**, dùng **Docling** chuyển tài liệu thành Markdown và gọi mô hình ngôn ngữ trên **Amazon Bedrock** để trích xuất thông tin. Một container Docker chạy trên **Amazon EC2**; **Amazon S3** lưu CV gốc và kết quả JSON. EC2 sử dụng IAM Role với quyền giới hạn để truy cập bucket và gọi mô hình. **AWS Budgets** được dùng để cảnh báo chi phí.

Nội dung đi theo các bước chuẩn bị dự án, thiết kế API và schema dữ liệu, cấu hình S3/IAM/Bedrock, đóng gói Docker, triển khai thủ công trên EC2 và kiểm thử API. Báo cáo không triển khai ECS, ECR, tên miền/HTTPS hay pipeline CI/CD; các trang tương ứng trong cấu trúc cũ được điều chỉnh để giải thích đúng phạm vi và không mô tả chúng như thành phần đã có.

#### Nội dung

1. [Tổng quan CloudCV](5.1-Workshop-overview/)
2. [Điều kiện chuẩn bị](5.2-Prerequiste/)
3. [Nền tảng dự án và API](5.3-Project-foundation/)
4. [EC2 và cấu hình mạng](5.4-VPC/)
5. [S3, Bedrock và IAM](5.5-Application-Services/)
6. [Đóng gói ứng dụng bằng Docker](5.6-Containerization/)
7. [Triển khai trên EC2](5.7-Deploy-Application/)
8. [Bảo vệ API và cấu hình](5.8-Domain-and-HTTPS/)
9. [Mã nguồn và quy trình phát hành](5.9-CI-CD/)
10. [Log và kiểm soát chi phí](5.10-Monitoring/)
11. [Kiểm thử API](5.11-Testing/)
12. [Dọn dẹp tài nguyên](5.12-Cleanup/)