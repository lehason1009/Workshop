---
title : "Điều kiện chuẩn bị"
date : 2026-01-01
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

### Mục tiêu

Chuẩn bị tài khoản AWS, môi trường Python/Docker và công cụ gọi API trước khi làm việc với CloudCV.

---

## 1. Công cụ cần chuẩn bị

Các tài nguyên trong báo cáo được tạo và quản lý trên AWS. Cần một tài khoản có quyền tạo EC2, S3, IAM và truy cập Amazon Bedrock; quyền gọi mô hình phải được cấp trước khi kiểm thử tích hợp.

Chuẩn bị các phần mềm sau:

- **Python 3.12** và môi trường cài thư viện Python.
- **Docker** để build và chạy container.
- **Git** để lấy mã nguồn và quản lý thay đổi.
- **Postman** hoặc **curl** để gọi REST API; trình duyệt có thể dùng Swagger UI.
- Một CV mẫu PDF hoặc DOCX, không lớn hơn giới hạn API 5 MB.

---

## 2. Các bước thực hiện

**Đăng nhập AWS Console:** Chọn Region phù hợp với quyền sử dụng Amazon Bedrock và xác nhận mô hình cần gọi khả dụng tại Region đó.

**Checkpoint:** Ghi lại Region dùng cho EC2 và Bedrock; hai dịch vụ phải được cấu hình nhất quán.

**Kiểm tra công cụ cục bộ:** Xác nhận Python, Git và Docker đã sẵn sàng.

```bash
python --version
git --version
docker --version
```

**Checkpoint:** Tất cả các lệnh đều trả về phiên bản hợp lệ.

**Chuẩn bị quyền truy cập:** Tạo ngân sách AWS để nhận cảnh báo chi phí và yêu cầu quyền sử dụng mô hình Bedrock trước khi chạy API.

---

## 3. Kết quả mong đợi

- Có môi trường Python 3.12, Docker và Git.
- Có quyền tạo tài nguyên cần thiết và gọi mô hình Bedrock.
- Có công cụ kiểm thử API cùng tệp CV mẫu.