---
title: "Amazon ECS và Amazon EKS khác nhau như thế nào?"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

Trong quá trình tìm hiểu các dịch vụ container trên AWS, em nhận thấy AWS có cả Amazon ECS và Amazon EKS. Cả hai đều giúp triển khai và quản lý container, nhưng chúng dựa trên hai nền tảng orchestration khác nhau.

## Amazon ECS

Amazon Elastic Container Service là dịch vụ điều phối container do AWS phát triển và quản lý. ECS tích hợp trực tiếp với các dịch vụ như IAM, CloudWatch, Elastic Load Balancing và Amazon ECR.

Một số đặc điểm:

- Mô hình tài nguyên tập trung vào Cluster, Task Definition, Task và Service.
- Không yêu cầu người dùng vận hành Kubernetes control plane.
- Phù hợp khi workload chủ yếu chạy trên AWS và nhóm muốn sử dụng mô hình điều phối AWS-native.
- Có thể dùng EC2 capacity hoặc AWS Fargate.

## Amazon EKS

Amazon Elastic Kubernetes Service là dịch vụ Kubernetes được AWS quản lý. Với EKS Standard, AWS quản lý Kubernetes control plane; người dùng vẫn làm việc với Kubernetes API và hệ sinh thái Kubernetes. EKS cũng cung cấp những lựa chọn quản lý hạ tầng cao hơn như EKS Auto Mode.

Một số đặc điểm:

- Sử dụng các khái niệm và API Kubernetes như Pod, Deployment, Service và ConfigMap.
- Tương thích với nhiều công cụ, manifest và plugin trong hệ sinh thái Kubernetes.
- Phù hợp khi tổ chức đã có kỹ năng Kubernetes, cần Kubernetes-native tooling hoặc muốn duy trì tính tương thích của workload.
- Workload có thể chạy trên EC2 hoặc AWS Fargate, tùy cấu hình hỗ trợ.

## Bảng so sánh

| Tiêu chí | Amazon ECS | Amazon EKS |
| --- | --- | --- |
| Nền tảng điều phối | AWS-native | Kubernetes |
| Đơn vị workload | Task | Pod |
| Quản lý ứng dụng dài hạn | ECS Service | Kubernetes Deployment/Service |
| Độ phức tạp học ban đầu | Thường thấp hơn nếu chỉ dùng AWS | Cần kiến thức Kubernetes |
| Hệ sinh thái | Tích hợp sâu với AWS | AWS và hệ sinh thái Kubernetes |
| Compute phổ biến | EC2, Fargate | EC2, Fargate |
| Tính tương thích Kubernetes | Không | Có |

## Nên chọn dịch vụ nào?

ECS thường phù hợp khi:

- Hệ thống tập trung trên AWS.
- Nhóm muốn bắt đầu nhanh với mô hình ít khái niệm hơn Kubernetes.
- Không có yêu cầu bắt buộc dùng Kubernetes API hoặc công cụ Kubernetes-native.

EKS thường phù hợp khi:

- Dự án hoặc tổ chức đã chuẩn hóa trên Kubernetes.
- Nhóm cần công cụ, operator, manifest hoặc quy trình Kubernetes hiện có.
- Khả năng tương thích Kubernetes là một yêu cầu kiến trúc.

Việc sử dụng Kubernetes không tự động bảo đảm một ứng dụng có thể chuyển sang mọi môi trường mà không thay đổi; networking, storage, IAM và các dịch vụ managed vẫn có thể phụ thuộc nền tảng. Vì vậy, quyết định nên dựa trên năng lực đội ngũ, yêu cầu kỹ thuật, chi phí và độ phức tạp vận hành.

## Kết luận

ECS và EKS đều giải quyết bài toán quản lý container, nhưng cung cấp hai mô hình điều phối khác nhau. ECS ưu tiên trải nghiệm AWS-native, còn EKS cung cấp Kubernetes được AWS quản lý. Không có lựa chọn luôn tốt hơn; lựa chọn phù hợp phụ thuộc vào kiến trúc và kinh nghiệm của nhóm.

## Tài liệu tham khảo

- [Amazon ECS documentation](https://docs.aws.amazon.com/ecs/)
- [What is Amazon EKS?](https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html)
- [Bài đăng trên AWS Study Group](https://www.facebook.com/groups/awsstudygroupfcj/permalink/2225042811594012/)


