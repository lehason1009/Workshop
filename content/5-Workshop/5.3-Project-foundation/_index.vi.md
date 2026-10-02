---
title : "Chuẩn bị dự án"
date : 2026-01-01
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

## Nền tảng dự án CloudCV

CloudCV là REST API viết bằng **FastAPI**. Hãy lấy mã nguồn của dự án từ kho GitHub tương ứng và cài các thư viện theo tệp dependency của chính dự án; báo cáo không ghi lại URL kho mã nguồn hoặc lệnh cài đặt cụ thể.

## Hợp đồng API

| Phương thức | Đường dẫn | Chức năng |
| --- | --- | --- |
| `GET` | `/health` | Kiểm tra trạng thái dịch vụ |
| `POST` | `/cvs` | Nhận CV, phân tích và trả mã CV cùng JSON |
| `GET` | `/cvs` | Liệt kê CV đã phân tích |
| `GET` | `/cvs/{cvId}` | Lấy kết quả của một CV |
| `DELETE` | `/cvs/{cvId}` | Xóa CV và kết quả lưu trên S3 |

Ngoại trừ `/health`, các endpoint yêu cầu header `X-API-Key`. Yêu cầu tải CV dùng `multipart/form-data`; API chấp nhận PDF/DOCX tối đa 5 MB.

## Schema kết quả

Pydantic xác thực JSON gồm các nhóm `full_name`, `email`, `phone`, `address`, `summary`, `education`, `experience`, `skills`, `languages` và `certifications`. Prompt yêu cầu chỉ trích xuất dữ kiện có trong CV, không tự suy đoán trường thiếu, và chuẩn hóa ngày tháng về năm-tháng. Trường không có dữ liệu được biểu diễn bằng `null` hoặc danh sách rỗng theo schema.

## Cấu hình và xác thực

Đưa khóa API, tên bucket và cấu hình cần thiết vào môi trường chạy thay vì ghi trong mã nguồn. Trên EC2, dùng IAM Role để truy cập S3 và Bedrock; không lưu AWS access key tĩnh trong tệp cấu hình ứng dụng. Không đưa khóa API hoặc thông tin CV thật vào Git.

## Kết quả mong đợi

Nắm được các endpoint, schema JSON và cách quản lý cấu hình an toàn trước khi đóng gói dịch vụ.