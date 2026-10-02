---
title: "Worklog Tuần 5"
date: 2026-09-20
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

# Tuần 5: ELB, Auto Scaling, Docker và triển khai CloudCV

**Thời gian:** 20/09/2026 – 27/09/2026

### Mục tiêu tuần 5:

* Tìm hiểu Elastic Load Balancer, Auto Scaling, ECS và Docker cơ bản.
* Đưa dự án CloudCV lên AWS.

### Các công việc đã thực hiện:

| Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- |
| Viết Dockerfile (Python 3.12, Docling, PyTorch CPU, tải sẵn mô hình) | 20/09/2026 | 27/09/2026 | https://cloudjourney.awsstudygroup.com/ |
| Tạo bucket S3 riêng tư, IAM Role cho EC2, xin quyền mô hình Amazon Bedrock | 20/09/2026 | 27/09/2026 | https://cloudjourney.awsstudygroup.com/ |
| Tạo EC2 t3.medium (Amazon Linux 2023, EBS 20 GB), Security Group cổng 22/8000, Elastic IP | 20/09/2026 | 27/09/2026 | https://cloudjourney.awsstudygroup.com/ |
| Cài Docker, build và chạy container tự khởi động lại; gọi Bedrock bằng Converse API | 20/09/2026 | 27/09/2026 | https://cloudjourney.awsstudygroup.com/ |
| Kiểm thử API bằng Postman/curl; theo dõi chi phí bằng AWS Budgets | 20/09/2026 | 27/09/2026 | https://cloudjourney.awsstudygroup.com/ |

### Kết quả đạt được tuần 5:

* CloudCV chạy trên EC2 bằng Docker, lưu dữ liệu trên S3, gọi LLM qua Bedrock.
* Kiểm thử thành công các trường hợp 201/400/401/404/413.
* ECS mới ở mức tìm hiểu, chưa thực hành.
