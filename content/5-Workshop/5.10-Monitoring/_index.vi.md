---
title : "Log và kiểm soát chi phí"
date : 2026-01-01
weight : 10
chapter : false
pre : " <b> 5.10. </b> "
---

### Mục tiêu

Theo dõi log container và thiết lập cảnh báo chi phí AWS cho CloudCV.

---

## 1. Tổng quan

Khi vận hành, dùng Docker logs trên EC2 để xem log khởi động và lỗi ứng dụng. AWS Budgets gửi cảnh báo khi tài khoản phát sinh chi phí. Báo cáo có học CloudWatch nhưng không ghi nhận việc cấu hình CloudWatch Logs hoặc alarm cho CloudCV.

---

## 2. Nội dung thực hành

Thực hiện phần sau:

- **5.10.1 Xem log Docker và AWS Budgets**

---

## 3. Kết quả mong đợi

Sau khi hoàn thành chương này, bạn sẽ có:

- Có thể đọc log container trực tiếp trên EC2.
- AWS Budgets được dùng để nhận cảnh báo chi phí.
- Không nhầm cấu hình CloudWatch ECS cũ với kiến trúc EC2 hiện tại.