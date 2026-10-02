---
title: "Đề xuất"
date: 2026-08-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# CloudCV

## First Cloud AI Journey – Capstone Project CloudCV

---

# 1. Tóm tắt

**CloudCV** là một REST API backend tự động phân tích CV. API nhận tệp CV dạng PDF hoặc DOCX, chuyển nội dung sang Markdown bằng **Docling**, gọi mô hình ngôn ngữ lớn (LLM) trên **Amazon Bedrock** để trích xuất thông tin và trả về JSON có cấu trúc.

Ứng dụng viết bằng **FastAPI**, đóng gói trong một container **Docker** chạy trên **Amazon EC2**. Tệp CV gốc và kết quả JSON được lưu trong **Amazon S3**. Máy ảo truy cập S3 và Bedrock qua **IAM Role** với quyền tối thiểu, mạng được kiểm soát bằng **VPC** và **Security Group**, còn **AWS Budgets** cảnh báo khi phát sinh chi phí.

Dự án được thực hiện trong 5 tuần (01/08/2026 – 27/09/2026) thuộc chương trình First Cloud AI Journey tại Công ty TNHH Amazon Web Services Việt Nam.

---

# 2. Vấn đề và giải pháp

## Vấn đề

CV có nhiều định dạng và bố cục khác nhau (một cột, hai cột, có bảng...). Đọc và nhập tay thông tin từ CV tốn thời gian. Nếu chỉ rút chuỗi ký tự thô từ PDF thì nội dung các cột thường bị trộn vào nhau.

## Giải pháp

- **Docling** chuyển CV sang Markdown mà vẫn giữ các tiêu đề mục, gạch đầu dòng và bảng.
- **LLM trên Amazon Bedrock** trích xuất thông tin theo một schema cố định. Prompt quy định chỉ lấy thông tin có trong CV; trường nào không có thì để null hoặc danh sách rỗng.
- **Pydantic** kiểm tra kết quả. Nếu sai schema, ứng dụng gọi lại mô hình một lần kèm thông báo lỗi.
- Kiến trúc được giữ ở mức tối giản, xoay quanh một máy ảo EC2, để hiểu kỹ các dịch vụ nền tảng của AWS.

---

# 3. Kiến trúc giải pháp

![Sơ đồ kiến trúc tổng thể CloudCV](/images/2-Proposal/kien-truc-cloudcv.png)

Toàn bộ ứng dụng nằm trong một container Docker chạy trên EC2, gồm ba phần nối tiếp nhau:

1. **Lớp API (FastAPI):** nhận và kiểm tra yêu cầu.
2. **Docling:** chuyển tệp CV sang Markdown.
3. **Trích xuất:** gọi LLM trên Bedrock, sau đó dùng Pydantic để kiểm tra lại kết quả.

Tệp CV và kết quả JSON đều được ghi vào một bucket S3 riêng tư, nên không cần cơ sở dữ liệu riêng.

![Luồng xử lý một yêu cầu phân tích CV](/images/2-Proposal/luong-xu-ly-cv.png)

API hoạt động đồng bộ: client gửi tệp lên và nhận kết quả ngay trong cùng yêu cầu đó.

## Dịch vụ AWS sử dụng

| Dịch vụ AWS | Vai trò trong hệ thống |
| --- | --- |
| Amazon EC2 | Máy ảo chạy container Docker chứa API FastAPI và Docling |
| Amazon S3 | Lưu tệp CV gốc và kết quả JSON (bucket riêng tư) |
| Amazon Bedrock | Cung cấp LLM trích xuất thông tin CV thành JSON |
| AWS IAM | IAM user thay cho root; IAM Role gắn cho EC2 theo nguyên tắc least privilege |
| Amazon VPC, Security Group | Public subnet cho máy ảo; chỉ mở cổng 22 và 8000 |
| AWS Budgets | Cảnh báo khi phát sinh chi phí |

---

# 4. Triển khai kỹ thuật

## Các endpoint

Trừ `/health`, mọi lời gọi phải kèm header `X-API-Key`. Thiếu hoặc sai khoá thì API trả về mã 401.

| Phương thức | Đường dẫn | Chức năng |
| --- | --- | --- |
| GET | `/health` | Kiểm tra tình trạng dịch vụ |
| POST | `/cvs` | Nhận tệp CV (multipart/form-data), phân tích và trả về mã CV cùng kết quả JSON |
| GET | `/cvs` | Liệt kê các CV đã phân tích |
| GET | `/cvs/{cvId}` | Lấy lại kết quả JSON của một CV |
| DELETE | `/cvs/{cvId}` | Xoá tệp CV và kết quả trên S3 |

## Schema JSON kết quả

| Trường | Kiểu dữ liệu | Ý nghĩa |
| --- | --- | --- |
| full_name | chuỗi | Họ và tên ứng viên |
| email, phone, address | chuỗi hoặc null | Thông tin liên hệ |
| summary | chuỗi hoặc null | Đoạn giới thiệu/mục tiêu nghề nghiệp |
| education | danh sách | Trường, chuyên ngành, bằng cấp, thời gian |
| experience | danh sách | Công ty, vị trí, thời gian, mô tả công việc |
| skills | danh sách chuỗi | Kỹ năng chuyên môn |
| languages | danh sách | Ngoại ngữ và trình độ |
| certifications | danh sách | Chứng chỉ, đơn vị cấp, năm |

## Hạ tầng

- **EC2:** t3.medium, Amazon Linux 2023, ổ EBS 20 GB, đặt trong public subnet, gắn Elastic IP.
- **Security Group:** cổng 22 chỉ mở cho IP cá nhân, cổng 8000 cho API.
- **Docker:** image dựa trên Python 3.12, có Docling, PyTorch bản CPU và các mô hình tải sẵn. Container được đặt chế độ tự khởi động lại.
- **IAM Role của EC2:** đọc/ghi/xoá/liệt kê object trong đúng bucket của dự án và gọi (InvokeModel) đúng mô hình trích xuất trên Bedrock.
- **Bedrock:** gọi qua Converse API của boto3, temperature = 0.

---

# 5. Lộ trình thực hiện

| Tuần | Nội dung | Kết quả |
| --- | --- | --- |
| 1 (01/08 – 14/08) | Bức tranh chung về AWS; mở tài khoản thực hành | Hoàn thành |
| 2 (15/08 – 28/08) | Dịch vụ cốt lõi: EC2, S3, IAM | Hoàn thành |
| 3 (29/08 – 11/09) | Mạng trên AWS: VPC, Subnet, Internet Gateway | Hoàn thành |
| 4 (12/09 – 19/09) | Lambda, Serverless; CloudWatch, CloudTrail | Hoàn thành (mức tìm hiểu) |
| 5 (20/09 – 27/09) | ELB, Auto Scaling, ECS, Docker; làm dự án tổng hợp | Hoàn thành (trừ thực hành ECS) |

---

# 6. Rủi ro và giới hạn

- API xử lý đồng bộ, nên một máy ảo chỉ đáp ứng được ít yêu cầu cùng lúc.
- API chạy qua HTTP, chưa có HTTPS và tên miền.
- Xác thực chỉ dựa vào một khoá dùng chung.
- CV dạng ảnh quét cần thêm bước OCR nên chậm và kém chính xác hơn.
- Chất lượng trích xuất mới được kiểm tra thủ công trên một số ít CV mẫu.
- Để giữ chi phí thấp, máy ảo được tắt khi không dùng và chi tiêu được theo dõi bằng AWS Budgets.

---

# 7. Hướng phát triển

- Đưa API lên HTTPS và gắn tên miền (Nginx hoặc Application Load Balancer), xác thực theo từng người dùng.
- Xử lý bất đồng bộ bằng hàng đợi và tiến trình nền.
- Dùng Infrastructure as Code (CloudFormation, Terraform) kết hợp GitHub Actions.
- Giám sát bằng Amazon CloudWatch.
- Lập bộ CV có gán nhãn để đo chất lượng trích xuất theo từng trường.
