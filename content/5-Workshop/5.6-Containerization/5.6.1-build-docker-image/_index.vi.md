---
title : "Build Docker Image"
date : 2026-01-01
weight : 1
chapter : false
pre : " <b> 5.6.1. </b> "
---

## Build Docker Image

CloudCV được đóng gói trong image dựa trên Python 3.12. Vì Docling phụ thuộc vào thư viện xử lý tài liệu và model bố cục, image cài bản PyTorch CPU và tải trước các model cần dùng.

---

## Tạo Dockerfile

Dockerfile của dự án cần cài dependencies Python, sao chép mã nguồn và chuẩn bị model Docling trong image. Báo cáo không cung cấp nội dung Dockerfile đầy đủ, vì vậy hãy dùng Dockerfile trong kho mã nguồn thay vì chép một ví dụ không khớp.

---

## Build Docker Image

Sau khi tạo Dockerfile, mở Terminal tại thư mục gốc của dự án và thực hiện build Docker Image.

Chạy lệnh sau:

```bash
docker build -t cloudcv .
```

Trong quá trình build, Docker sẽ thực hiện các bước sau:

1. Tải Python 3.12 base image nếu chưa có.
2. Cài các thư viện của API và Docling, gồm bản PyTorch CPU.
3. Sao chép mã nguồn và tải trước model phân tích bố cục.
4. Đóng gói dịch vụ thành Docker image.

Sau khi build thành công, Docker sẽ hiển thị thông báo tương tự:

```text
Successfully built <IMAGE_ID>
Successfully tagged cloudcv:latest
```

Để kiểm tra Docker Image vừa tạo, chạy lệnh:

```bash
docker images
```

Lệnh này sẽ hiển thị danh sách Docker Image trên máy. Xác nhận Docker Image vừa build xuất hiện với tag **latest**.

---

## Kết quả mong đợi

Sau khi hoàn thành phần này, bạn sẽ có:

- Image `cloudcv:latest` được build thành công.
- Container có thể khởi động mà không cần tải model Docling lần đầu.