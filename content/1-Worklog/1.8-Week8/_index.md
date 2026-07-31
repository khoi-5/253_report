---
title: "Week 8 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 objectives

- Study DNS, email, and operational security.
- Deploy and validate Cloud E-Wallet end to end in production.

### Work completed

| Day | Work item | Start date | Completion date | Reference |
| --- | --- | --- | --- | --- |
| 2 | Study DNS, domains, Cloudflare, and routing a domain to CloudFront. | 20/07/2026 | 20/07/2026 | AWS Study Group – FCJ 2025 and AWS documentation |
| 3 | Study SMTP, STARTTLS, sender-domain verification, and application email flow. | 21/07/2026 | 21/07/2026 | AWS Study Group – FCJ 2025 and AWS documentation |
| 4 | Review least privilege, secret separation, security-group chains, and cost control. | 22/07/2026 | 22/07/2026 | AWS Study Group – FCJ 2025 and AWS documentation |
| 5 | Deploy the Docker backend to EC2 with RDS/Resend and the frontend to S3/CloudFront. | 23/07/2026 | 23/07/2026 | Cloud E-Wallet source and documentation |
| 6 | Create the ALB/target group, configure `/api/*`, verify Healthy status, smoke test, and block direct EC2:8080. | 24/07/2026 | 24/07/2026 | Cloud E-Wallet source and documentation |

### Outcomes

- I completed the Cloudflare → CloudFront → S3/ALB → EC2 → RDS architecture.
- Email and main business workflows were validated in production.
- I documented the one-target limitation and the absence of Auto Scaling, ECS, and CI/CD.

