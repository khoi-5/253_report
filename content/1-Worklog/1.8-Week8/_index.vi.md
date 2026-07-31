---
title: "Nhật ký tuần 8"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8

- Bổ sung kiến thức về DNS, email và bảo mật vận hành.
- Triển khai end-to-end và kiểm tra Cloud E-Wallet trên môi trường production.

### Công việc thực hiện

| Thứ | Nội dung công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | Tìm hiểu DNS, domain, Cloudflare và cách domain trỏ đến CloudFront. | 20/07/2026 | 20/07/2026 | AWS Study Group – FCJ 2025 và tài liệu AWS |
| 3 | Tìm hiểu SMTP, STARTTLS, xác minh domain gửi và luồng gửi email của ứng dụng. | 21/07/2026 | 21/07/2026 | AWS Study Group – FCJ 2025 và tài liệu AWS |
| 4 | Ôn lại các nguyên tắc bảo mật: cấp quyền tối thiểu, tách thông tin bí mật, chuỗi Security Group và kiểm soát chi phí. | 22/07/2026 | 22/07/2026 | AWS Study Group – FCJ 2025 và tài liệu AWS |
| 5 | Triển khai backend bằng Docker lên EC2, kết nối RDS/SES; triển khai frontend lên S3/CloudFront. | 23/07/2026 | 23/07/2026 | Source và tài liệu Cloud E-Wallet |
| 6 | Tạo ALB/Target Group, cấu hình `/api/*`, kiểm tra target ở trạng thái Healthy, thực hiện smoke test và chặn truy cập trực tiếp đến EC2 qua port `8080`. | 24/07/2026 | 24/07/2026 | Source và tài liệu Cloud E-Wallet |

### Kết quả đạt được

- Em hoàn thành luồng Cloudflare DNS → CloudFront → S3/ALB → EC2 → RDS.
- Các luồng email và nghiệp vụ chính đã được kiểm tra trên môi trường production.
- Em hoàn thiện việc kiểm tra luồng truy cập qua CloudFront, ALB, Auto Scaling Group, EC2, RDS và Amazon SES.
