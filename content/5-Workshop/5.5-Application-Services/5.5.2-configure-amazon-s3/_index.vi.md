---
title : "Cấu hình Amazon S3"
date : 2026-01-01
weight : 2
chapter : false
pre : " <b> 5.5.2. </b> "
---

## Cấu hình Amazon S3

CloudCV dùng Amazon S3 để lưu tệp CV gốc và kết quả JSON. Bucket được giữ riêng tư; ứng dụng truy cập bằng IAM Role của EC2.

---

## Tạo S3 Bucket

Tạo bucket trong Region phù hợp với EC2 và đặt tên duy nhất toàn cục. Giữ **Block Public Access** bật và không bật quyền public cho dữ liệu CV.

| Thuộc tính | Giá trị |
|------------|----------|
| Bucket name | *your-bucket-name* |
| AWS Region | Cùng Region dự kiến dùng cho ứng dụng |
| Object Ownership | ACLs disabled |
| Block Public Access | Enabled |

Kiểm tra lại cấu hình và chọn **Create bucket**.

## Dữ liệu được lưu

API lưu bản CV tải lên và JSON đã phân tích vào bucket. Mỗi CV được tham chiếu bằng mã CV để các endpoint liệt kê, đọc và xóa có thể thao tác với dữ liệu tương ứng. Tên key/prefix cụ thể phụ thuộc mã nguồn dự án.

## Kiểm tra truy cập

Gắn IAM Role phù hợp cho EC2 và xác nhận ứng dụng có thể ghi, đọc, liệt kê và xóa object trong đúng bucket. Không cấp quyền public; không đặt access key tĩnh trên máy chủ.

---

## Kết quả mong đợi

Sau khi hoàn thành phần này, bạn sẽ có:

- Bucket riêng tư dùng cho CV gốc và kết quả JSON.
- EC2 truy cập được đúng bucket theo quyền IAM được cấp.