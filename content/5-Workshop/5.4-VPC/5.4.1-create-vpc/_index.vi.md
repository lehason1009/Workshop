---
title : "Tạo VPC"
date : 2026-01-01
weight : 1
chapter : false
pre : " <b> 5.4.1. </b> "
---

## Tạo VPC

CloudCV sử dụng VPC của AWS để đặt EC2 trong một public subnet. Báo cáo không ghi lại CIDR hoặc tên VPC, vì vậy hãy dùng VPC đã chọn cho tài khoản và ghi lại dải địa chỉ thực tế thay vì sao chép một CIDR ví dụ.

---

## Tạo Virtual Private Cloud

Trong AWS Console, mở **VPC → Your VPCs** để xem VPC khả dụng. Nếu cần tạo VPC mới, chọn một IPv4 CIDR không xung đột với mạng hiện có và bật DNS resolution/hostnames nếu cấu hình EC2 cần phân giải DNS. Ghi lại VPC ID, CIDR và Region dùng cho các bước tiếp theo.

---

## Kiểm tra VPC

Truy cập:

**AWS Console → VPC → Your VPCs**

Chọn VPC dự định sử dụng và kiểm tra:

| Thuộc tính | Giá trị mong đợi |
|------------|------------------|
| Trạng thái | Available |
| IPv4 CIDR | Khớp dải đã chọn, không chồng lấn |
| DNS Resolution | Enabled |
| DNS Hostnames | Enabled |

Xác nhận VPC đã được tạo thành công trước khi chuyển sang bước cấu hình mạng.

## Kết quả mong đợi

Sau khi hoàn thành phần này, bạn sẽ có:

- Một VPC được xác định cho EC2.
- VPC ID, Region và CIDR thực tế được ghi lại.
- DNS Resolution và DNS Hostnames được bật.
- VPC sẵn sàng để cấu hình Subnet và các tài nguyên mạng ở bước tiếp theo.