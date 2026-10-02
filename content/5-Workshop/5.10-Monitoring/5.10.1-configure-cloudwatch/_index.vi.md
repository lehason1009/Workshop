---
title : "Xem log Docker và AWS Budgets"
date : 2026-01-01
weight : 1
chapter : false
pre : " <b> 5.10.1. </b> "
---

# Xem log Docker và AWS Budgets

## Log ứng dụng

CloudCV chạy trong container trên EC2. Dùng các lệnh sau để kiểm tra trạng thái và log khi xử lý sự cố:

```bash
docker ps
docker logs --tail 100 cloudcv
```

Không ghi API key, CV đầy đủ hoặc dữ liệu cá nhân vào log. Báo cáo không ghi nhận việc chuyển log sang CloudWatch; nếu cần lưu tập trung, phải cấu hình bổ sung và kiểm soát quyền truy cập log.

## Cảnh báo chi phí

AWS Budgets được tạo để gửi email khi có chi phí phát sinh. Kiểm tra budget và Billing thường xuyên; budget là cơ chế cảnh báo, không tự dừng tài nguyên. EC2 có thể được stop khi không sử dụng để giảm chi phí compute, nhưng EBS và Elastic IP vẫn có thể phát sinh phí.

## CloudWatch trong phạm vi dự án

CloudWatch là nội dung đã học trong chương trình, nhưng báo cáo không mô tả log group hay alarm CloudWatch dành cho ứng dụng CloudCV. Không giả định cấu hình ECS/CPU alarm của các trang cũ vẫn áp dụng.

## Kết quả mong đợi

Có thể kiểm tra log container và nhận cảnh báo chi phí; hiểu rằng cần cấu hình CloudWatch riêng nếu muốn giám sát tập trung.