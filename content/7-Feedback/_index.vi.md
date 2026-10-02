---
title: "Chia sẻ, đóng góp ý kiến"
date: 2026-09-27
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

# Chia sẻ, đóng góp ý kiến

## Nhận xét về chương trình

Điều tôi thấy hợp lý nhất ở chương trình FCAJ là trình tự học: mỗi tuần thêm một lớp kiến thức, và đến dự án cuối thì mọi thứ đã học đều có chỗ dùng. Nhờ đó tôi quen dần với cách làm một bài toán trên đám mây theo từng bước: làm rõ yêu cầu, phác kiến trúc, chọn dịch vụ, dựng từng phần, kiểm thử rồi mới vận hành.

Chọn một máy ảo EC2 và ít dịch vụ là phù hợp với quy mô một dự án học tập. Hệ thống dễ hình dung, dễ tìm lỗi, và buộc tôi phải hiểu rõ máy ảo, mạng, phân quyền và lưu trữ trước khi nghĩ tới những mô hình phức tạp hơn.

## Liên hệ giữa lý thuyết và thực tế

- **Mạng máy tính:** địa chỉ IP, cổng và tường lửa trở nên rất cụ thể khi cấu hình subnet và Security Group, và khi phải tìm vì sao API không gọi được từ bên ngoài.
- **Hệ điều hành:** hiểu vì sao container bị tắt khi máy hết RAM và cách xem tài nguyên trên máy chủ Linux.
- **An toàn thông tin:** áp dụng nguyên tắc cấp quyền tối thiểu bằng IAM Role thay vì để khoá truy cập trên máy.
- **Công nghệ phần mềm:** thiết kế REST API (phương thức, mã trạng thái, kiểm tra đầu vào).
- **Trích xuất thông tin:** dùng LLM kèm schema ràng buộc. Mô hình dù mạnh vẫn cần một lớp kiểm tra đầu ra thì mới đưa được vào hệ thống thật.

## Đề xuất

**Về chương trình:** thêm một buổi góp ý kiến trúc vào giữa kỳ. Nếu mentor nhận xét bản thiết kế trước khi triển khai, thực tập sinh sẽ tránh được nhiều lần làm lại.

**Về hướng phát triển CloudCV:**

- Đưa API lên HTTPS và gắn tên miền (Nginx hoặc Application Load Balancer); thay khoá dùng chung bằng xác thực theo từng người dùng.
- Xử lý bất đồng bộ bằng hàng đợi và tiến trình nền.
- Bỏ thao tác tay qua SSH: script triển khai hoặc Infrastructure as Code (CloudFormation, Terraform) kết hợp GitHub Actions.
- Giám sát bằng Amazon CloudWatch: thu log và đặt cảnh báo.
- Lập bộ CV có gán nhãn để đo chất lượng trích xuất theo từng trường.
