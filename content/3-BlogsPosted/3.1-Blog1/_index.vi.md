---
title: "Docker đã chạy trên EC2 rồi, vậy Amazon ECS sinh ra để làm gì?"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

Trong quá trình học AWS, em bắt đầu với Amazon EC2. Sau khi tạo một EC2 instance và deploy project bằng Docker, em từng nghĩ quy trình triển khai chỉ cần dừng ở đó: mỗi khi có phiên bản mới thì SSH vào EC2, pull image mới và chạy lại container.

Tuy nhiên, trong nhiều kiến trúc mẫu của AWS, Amazon ECS lại xuất hiện thay vì chỉ chạy Docker trực tiếp trên EC2. Điều này khiến em đặt câu hỏi: nếu Docker đã chạy được trên EC2 thì tại sao AWS còn cần Amazon ECS?

## Docker và ECS giải quyết hai bài toán khác nhau

Docker giúp đóng gói ứng dụng cùng các dependency thành container image. Nhờ đó, ứng dụng có thể chạy nhất quán ở nhiều môi trường.

Nhưng khi số lượng container hoặc yêu cầu vận hành tăng lên, hệ thống bắt đầu cần:

- Luôn duy trì một số lượng container nhất định.
- Tự tạo lại workload khi container gặp lỗi.
- Tăng hoặc giảm số lượng container theo tải.
- Phân phối request qua load balancer.
- Triển khai phiên bản mới theo từng bước và hạn chế gián đoạn.
- Theo dõi trạng thái của nhiều container thay vì SSH vào từng máy.

Đây là bài toán **container orchestration**, không còn chỉ là bài toán đóng gói container.

Amazon ECS là dịch vụ điều phối container được AWS quản lý. Thay vì tự SSH vào từng EC2 và chạy lệnh Docker, người vận hành khai báo cấu hình cùng trạng thái mong muốn; ECS scheduler hỗ trợ sắp xếp và quản lý các workload container.

Ví dụ, nếu một ECS Service được đặt `desiredCount = 3`, Service sẽ cố gắng duy trì ba Task đang chạy. Khi một Task dừng hoặc bị đánh dấu không khỏe, ECS Service scheduler có thể khởi chạy Task thay thế để đưa hệ thống về trạng thái mong muốn.

## ECS chạy container ở đâu?

Hai lựa chọn thường gặp là:

- **Amazon EC2:** container vẫn chạy trên các EC2 instance thuộc ECS cluster. Nhóm vận hành quản lý capacity của EC2, còn ECS quản lý workload container.
- **AWS Fargate:** cung cấp compute serverless cho container; người dùng không phải trực tiếp quản lý máy chủ bên dưới.

Vì vậy, ECS không thay thế Docker và cũng không nhất thiết thay thế EC2. Docker tạo image; EC2 hoặc Fargate cung cấp compute; ECS điều phối việc triển khai và vận hành container trên compute đó.

## Khi nào chạy Docker trực tiếp trên EC2 vẫn phù hợp?

Với một project nhỏ, một container, ít thay đổi và chấp nhận vận hành thủ công, Docker trực tiếp trên EC2 có thể đơn giản hơn. Đây cũng là trạng thái production hiện tại của project Cloud E-Wallet em thực hiện.

Khi hệ thống cần nhiều container, tự phục hồi, rolling deployment, load balancing hoặc scaling, ECS trở nên hữu ích hơn vì giảm số thao tác thủ công và quản lý trạng thái tập trung.

## Kết luận

Điểm em rút ra là Docker và ECS bổ trợ cho nhau:

- **Docker:** đóng gói và chạy container.
- **Amazon ECS:** triển khai, quản lý và điều phối container ở quy mô hệ thống.

Hiểu sự khác nhau này giúp em lý giải vì sao một ứng dụng có thể bắt đầu bằng Docker trên EC2, rồi nghiên cứu chuyển sang ECS khi yêu cầu vận hành tăng lên.

## Tài liệu tham khảo

- [Amazon ECS Developer Guide](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html)
- [Bài đăng trên AWS Study Group](https://www.facebook.com/groups/awsstudygroupfcj/permalink/2224875461610747/)


