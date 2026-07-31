---
title: "Week 8 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 objectives

- Expand my knowledge of DNS, email, and operational security.
- Deploy and validate Cloud E-Wallet end to end in the production environment.

### Work completed

| Day | Work item | Start date | Completion date | Reference |
| --- | --- | --- | --- | --- |
| Monday | Study DNS, domains, Cloudflare, and how a domain points to CloudFront. | 20/07/2026 | 20/07/2026 | AWS Study Group – FCJ 2025 and AWS documentation |
| Tuesday | Study SMTP, STARTTLS, sender-domain verification, and the application's email flow. | 21/07/2026 | 21/07/2026 | AWS Study Group – FCJ 2025 and AWS documentation |
| Wednesday | Review security principles: least privilege, secret separation, Security Group chains, and cost control. | 22/07/2026 | 22/07/2026 | AWS Study Group – FCJ 2025 and AWS documentation |
| Thursday | Deploy the Dockerized backend to EC2 and connect it to RDS and SES; deploy the frontend to S3 and CloudFront. | 23/07/2026 | 23/07/2026 | Cloud E-Wallet source code and documentation |
| Friday | Create the ALB and Target Group, configure `/api/*`, verify that targets are Healthy, perform smoke tests, and block direct access to EC2 on port `8080`. | 24/07/2026 | 24/07/2026 | Cloud E-Wallet source code and documentation |

### Outcomes

- I completed the Cloudflare DNS → CloudFront → S3/ALB → EC2 → RDS flow.
- The email flow and main business workflows were validated in the production environment.
- I completed validation of the access path through CloudFront, ALB, Auto Scaling Group, EC2, RDS, and Amazon SES.
