+++
title = "Dọn dẹp tài nguyên"
date = 2024-01-01
weight = 12
chapter = false
pre = "<b>5.12. </b>"
+++

# 5.12. Dọn dẹp tài nguyên CloudCV

## Lưu ý trước khi xóa

Các bước này là checklist dọn tài nguyên, không phải xác nhận rằng báo cáo đã xóa chúng. Sao lưu CV/kết quả cần giữ trước khi xóa bucket; thao tác làm rỗng S3 là không thể khôi phục nếu không có bản sao.

## Thứ tự dọn dẹp

1. Dừng container và xác nhận không còn cần API.
2. Trong EC2, terminate instance CloudCV. Chọn cách xử lý volume EBS theo chính sách lưu giữ dữ liệu.
3. Release Elastic IP sau khi tháo khỏi instance; địa chỉ public chưa gắn có thể bị tính phí.
4. Nếu không cần dữ liệu nữa, xóa object trong bucket CloudCV rồi xóa bucket.
5. Gỡ IAM Role khỏi EC2; chỉ xóa role/policy riêng của dự án khi không còn dịch vụ nào sử dụng.
6. Xóa Security Group, subnet, Internet Gateway và VPC chỉ khi chúng được tạo riêng cho CloudCV và không còn phụ thuộc.
7. Thu hồi API key đã dùng và rà soát các quyền gọi Bedrock trong IAM policy.
8. Kiểm tra Billing/AWS Budgets để xác nhận không còn tài nguyên gây chi phí. Có thể giữ budget để theo dõi tài khoản.

## Xác nhận

Kiểm tra EC2 instance đã terminate, Elastic IP đã release, bucket đã được xử lý theo quyết định lưu giữ, và các quyền IAM dư thừa đã được gỡ. Không xóa tài nguyên dùng chung hoặc dữ liệu cần lưu trữ.