---
title: "Amazon ECS và Amazon EKS khác nhau như thế nào?"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

Trong quá trình tìm hiểu về các dịch vụ container trên AWS, mình nhận thấy AWS cung cấp hai dịch vụ là Amazon ECS (Elastic Container Service) và Amazon EKS (Elastic Kubernetes Service). Ban đầu mình khá thắc mắc vì cả hai đều được giới thiệu là dịch vụ giúp triển khai và quản lý container, vậy điểm khác nhau giữa chúng là gì và trong trường hợp nào nên sử dụng từng dịch vụ?

Sau khi đọc tài liệu của AWS, mình nhận ra rằng điểm khác biệt lớn nhất không nằm ở việc chạy container, mà nằm ở nền tảng orchestration mà mỗi dịch vụ sử dụng.

Amazon ECS là dịch vụ orchestration container do chính AWS phát triển. ECS được thiết kế để tích hợp chặt chẽ với hệ sinh thái AWS, vì vậy việc kết nối với các dịch vụ như IAM, CloudWatch, Auto Scaling hay Application Load Balancer tương đối đơn giản. Nếu ứng dụng chủ yếu được triển khai trên AWS thì ECS thường là lựa chọn dễ tiếp cận vì không cần phải học thêm Kubernetes mà vẫn có thể quản lý container hiệu quả.

Trong khi đó, Amazon EKS là dịch vụ Kubernetes được AWS quản lý. Thay vì sử dụng nền tảng orchestration do AWS xây dựng, EKS sử dụng Kubernetes – nền tảng mã nguồn mở đang được sử dụng rất phổ biến trong nhiều doanh nghiệp. AWS sẽ chịu trách nhiệm quản lý control plane của Kubernetes, giúp giảm bớt khối lượng công việc so với việc tự triển khai một Kubernetes cluster.

Sau khi tìm hiểu, mình tóm tắt sự khác nhau như sau:

### Amazon ECS

- Dịch vụ orchestration container do AWS phát triển.
- Tích hợp chặt chẽ với các dịch vụ trong hệ sinh thái AWS.
- Tương đối dễ học và triển khai nếu ứng dụng chỉ chạy trên AWS.
- Có thể triển khai trên EC2 hoặc AWS Fargate.

### Amazon EKS

- Dịch vụ Kubernetes được AWS quản lý.
- Sử dụng Kubernetes thay vì nền tảng orchestration riêng của AWS.
- Phù hợp với các dự án đã sử dụng Kubernetes hoặc cần tận dụng hệ sinh thái Kubernetes.
- Cũng có thể triển khai trên EC2 hoặc AWS Fargate.

Điều mình thấy thú vị là ECS và EKS không phải là hai dịch vụ cạnh tranh trực tiếp. Chúng đều giải quyết bài toán quản lý container nhưng hướng đến những nhu cầu khác nhau.

Nếu hệ thống chủ yếu triển khai trên AWS và mong muốn một giải pháp đơn giản, tích hợp tốt với các dịch vụ của AWS thì ECS là một lựa chọn phù hợp. Ngược lại, nếu dự án đã sử dụng Kubernetes hoặc cần tính linh hoạt để triển khai trên nhiều môi trường khác nhau thì EKS sẽ là lựa chọn phù hợp hơn.

Sau khi tìm hiểu, mình thấy AWS không tạo ra ECS và EKS để một dịch vụ thay thế dịch vụ còn lại. Thay vào đó, AWS cung cấp hai lựa chọn nhằm đáp ứng những nhu cầu triển khai khác nhau của người dùng. Việc lựa chọn ECS hay EKS sẽ phụ thuộc vào kiến trúc hệ thống, công nghệ mà dự án đang sử dụng cũng như yêu cầu về khả năng mở rộng và vận hành trong thực tế.

## Tài liệu tham khảo

- [Amazon ECS](https://docs.aws.amazon.com/ecs/)
- [Amazon EKS](https://docs.aws.amazon.com/eks/)

## Liên kết bài viết đã đăng

- [Xem bài viết trên AWS Study Group](https://www.facebook.com/groups/awsstudygroupfcj/permalink/2225042811594012/)