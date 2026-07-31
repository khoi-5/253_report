---
title: "Nhật ký tuần 8"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8

- Bổ sung kiến thức về DNS, email và bảo mật vận hành.
- Triển khai end-to-end và kiểm tra Cloud E-Wallet trên production.

### Công việc thực hiện

| Thứ | Nội dung công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | Tìm hiểu DNS, domain, Cloudflare và cách domain trỏ đến CloudFront. | 20/07/2026 | 20/07/2026 | AWS Study Group – FCJ 2025 và tài liệu AWS |
| 3 | Tìm hiểu SMTP, STARTTLS, sender domain verification và luồng gửi email của ứng dụng. | 21/07/2026 | 21/07/2026 | AWS Study Group – FCJ 2025 và tài liệu AWS |
| 4 | Ôn lại security best practices: least privilege, tách secret, Security Group chain và kiểm soát chi phí. | 22/07/2026 | 22/07/2026 | AWS Study Group – FCJ 2025 và tài liệu AWS |
| 5 | Deploy backend Docker lên EC2, kết nối RDS/Resend; deploy frontend lên S3/CloudFront. | 23/07/2026 | 23/07/2026 | Source và tài liệu Cloud E-Wallet |
| 6 | Tạo ALB/target group, cấu hình `/api/*`, kiểm tra target Healthy, smoke test và chặn direct EC2:8080. | 24/07/2026 | 24/07/2026 | Source và tài liệu Cloud E-Wallet |

### Kết quả đạt được

- Em hoàn thành kiến trúc Cloudflare → CloudFront → S3/ALB → EC2 → RDS.
- Các luồng email và nghiệp vụ chính đã được kiểm tra trên production.
- Em ghi nhận rõ giới hạn một EC2 target, chưa có Auto Scaling, ECS hoặc CI/CD.

