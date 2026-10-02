---
title : "Kiểm thử"
date : 2024-01-01
weight : 11
chapter : false
pre : " <b> 5.11. </b> "
---

# 5.11. Kiểm thử API CloudCV

API được kiểm thử bằng Postman và curl từ máy client; Swagger UI có thể mở tại `/docs`. Dịch vụ không có giao diện website. Các kết quả dưới đây là những trường hợp được ghi nhận trong báo cáo.

## Ma trận kiểm thử

| Trường hợp | Kết quả mong đợi/ghi nhận |
| --- | --- |
| `GET /health` | Kiểm tra trạng thái dịch vụ |
| `POST /cvs` với PDF hợp lệ | HTTP 201, trả mã CV và JSON |
| `POST /cvs` với DOCX hợp lệ | HTTP 201, trả mã CV và JSON |
| Endpoint cần xác thực, thiếu/sai `X-API-Key` | HTTP 401 |
| Tải tệp không phải PDF/DOCX | HTTP 400 |
| Tải tệp lớn hơn 5 MB | HTTP 413 |
| `GET /cvs/{cvId}` với mã không tồn tại | HTTP 404 |
| Khởi động lại EC2/container | Container tự chạy lại; dữ liệu cũ vẫn đọc được từ S3 |

## Kiểm tra dữ liệu

So sánh JSON với nội dung CV để xác nhận các trường liên hệ, học vấn, kinh nghiệm, kỹ năng, ngoại ngữ và chứng chỉ. Báo cáo chỉ đánh giá thủ công trên một tập mẫu nhỏ; chưa có bộ dữ liệu gán nhãn hay chỉ số độ chính xác định lượng.

## Kiểm tra thao tác lưu trữ

Sau khi tạo CV, dùng `GET /cvs` và `GET /cvs/{cvId}` để xác nhận kết quả có thể truy xuất. `DELETE /cvs/{cvId}` xóa CV và JSON tương ứng trên S3; chỉ thực hiện với dữ liệu thử nghiệm có thể xóa.

## Kết luận kiểm thử

Các trường hợp đã ghi nhận xác nhận luồng API cơ bản, xác thực, kiểm tra tệp và tính bền vững dữ liệu qua S3. Độ chính xác trích xuất cần được đánh giá thêm trên tập CV lớn hơn.

## Demo chức năng Parse CV

Ngoài CloudCV, tôi tham gia phát triển chức năng **Parse CV** (`POST /v3/resume/cv`) trong một hệ thống trích xuất thông tin CV khác, tách biệt với CloudCV. Phạm vi của tôi chỉ là chức năng này; các nhóm chức năng khác của hệ thống (Matching, Vector, JD Builder, JD) không thuộc phần việc của tôi. Endpoint nhận một hoặc nhiều tệp (PDF, DOCX...), gộp lại để phân tích và trả về JSON có cấu trúc.

![Gọi thử endpoint Parse CV trên Swagger UI (thông tin cá nhân đã được che)](/images/5-Workshop/demo-parse-cv.png)
