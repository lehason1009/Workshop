---
title: "Tự đánh giá"
date: 2026-09-27
weight: 6
chapter: false
pre: " <b> 6. </b> "
---

# Tự đánh giá

Trong 5 tuần thực tập (01/08/2026 – 27/09/2026) theo chương trình **First Cloud AI Journey** tại Công ty TNHH Amazon Web Services Việt Nam, tôi học các dịch vụ nền tảng của AWS và hoàn thành dự án Capstone **CloudCV**.

## Đối chiếu mục tiêu học tập (CLO) và kết quả

| CLO | Mục tiêu | Kết quả đạt được |
| --- | --- | --- |
| CLO1 – Áp dụng kiến thức chuyên môn | Đưa một ứng dụng do mình viết lên chạy trên AWS | API CloudCV chạy trên Amazon EC2, dùng IAM, VPC/Security Group, EC2, S3, Bedrock và Budgets |
| CLO2 – Phân tích và giải quyết vấn đề | Tự tìm nguyên nhân và cách xử lý khi hệ thống gặp lỗi | Tự xử lý các sự cố: máy ảo thiếu bộ nhớ, đầy ổ đĩa, API không gọi được từ Internet, bị từ chối quyền khi gọi Bedrock, LLM trả JSON sai schema |
| CLO3 – Giao tiếp, báo cáo, thuyết trình | Ghi chép công việc và trình bày cho người khác hiểu | Có nhật ký theo tuần, sơ đồ kiến trúc, tài liệu API và báo cáo thực tập; trao đổi với mentor ở các buổi học |
| CLO4 – Đạo đức và an toàn nghề nghiệp | Làm việc đúng quy tắc bảo mật | Không dùng root cho việc hằng ngày, root có MFA; EC2 dùng IAM Role thay vì access key; SSH chỉ mở cho IP cá nhân; API có khoá truy cập; dữ liệu thử là CV mẫu |
| CLO5 – Làm việc nhóm, phối hợp | Phối hợp với mentor và các bạn cùng chương trình | Dự đủ 7/7 buổi học tại văn phòng, hỏi đáp trong cộng đồng FCAJ; dự án làm một mình nên còn ít kinh nghiệm làm việc nhóm |
| CLO6 – Sử dụng công cụ kỹ thuật | Dùng quen các công cụ của kỹ sư cloud | AWS Management Console, SSH, Docker, Postman, Git/GitHub, Visual Studio Code, draw.io |
| CLO7 – Tự nhận xét và phát triển nghề nghiệp | Nhìn lại bản thân và vạch hướng đi tiếp | Tự đánh giá điểm mạnh, điểm yếu và lập kế hoạch học tiếp, thi chứng chỉ AWS |

## Điểm mạnh

- Đọc tài liệu kỹ thuật tiếng Anh khá nhanh, tự giải quyết phần lớn vướng mắc bằng tài liệu gốc của AWS và Docling.
- Có nền Python từ trước nên viết API và chuỗi xử lý CV không mất nhiều thời gian.
- Khi máy chủ lỗi, chịu khó đọc log và thử từng giả thuyết cho tới khi tìm ra nguyên nhân.
- Chú ý bảo mật và chi phí ngay từ đầu: IAM user và MFA, IAM Role, giới hạn cổng, AWS Budgets, tắt máy ảo khi không dùng.

## Điểm cần cải thiện

- Hiểu biết về bảo mật hệ thống mới ở mức nhập môn.
- Serverless, Load Balancer, Auto Scaling và ECS mới biết qua tài liệu và lab.
- Việc triển khai vẫn làm bằng tay, chưa có CI/CD.
- Dự án chưa có giao diện người dùng và chưa có bộ dữ liệu đủ lớn để đánh giá chất lượng trích xuất.
- Làm một mình nên gần như chưa rèn được kỹ năng làm việc nhóm.
- Chia thời gian chưa khéo: phần triển khai bị dồn vào hai tuần cuối.

## Kế hoạch tiếp theo (3–6 tháng)

- Thi chứng chỉ AWS Certified Cloud Practitioner, sau đó chuẩn bị cho AWS Certified Solutions Architect – Associate.
- Nâng cấp CloudCV: HTTPS, xử lý bất đồng bộ, giám sát và triển khai tự động.
- Thực hành Lambda, Load Balancer, Auto Scaling, ECS và đưa dự án vào hồ sơ năng lực.

Về lâu dài, tôi muốn trở thành kỹ sư backend/cloud: vừa viết phần mềm phía máy chủ vừa vận hành hạ tầng đám mây cho phần mềm đó.
