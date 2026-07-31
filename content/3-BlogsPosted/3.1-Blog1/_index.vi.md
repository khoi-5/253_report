---
title: "Docker đã chạy trên EC2 rồi, vậy Amazon ECS sinh ra để làm gì?"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

Trong quá trình học AWS, mình bắt đầu với EC2.

Sau khi tạo EC2 và deploy thành công project bằng Docker, mình nghĩ rằng quy trình triển khai chắc cũng chỉ đến đó. Mỗi lần cập nhật phiên bản mới thì chỉ cần SSH vào EC2, pull image mới rồi chạy lại container là xong.

Tuy nhiên, khi xem các kiến trúc mẫu và tài liệu của AWS, mình lại thấy rất nhiều hệ thống sử dụng Amazon ECS thay vì chỉ chạy Docker trực tiếp trên EC2.

Lúc đó mình khá thắc mắc.

Docker đã chạy được trên EC2 rồi, vậy tại sao AWS còn phát triển thêm Amazon ECS?

Sau khi tìm hiểu thì mình mới nhận ra Docker và ECS giải quyết hai bài toán hoàn toàn khác nhau.

Docker giúp mình đóng gói ứng dụng thành container để có thể chạy ở nhiều môi trường khác nhau.

Nhưng khi ứng dụng phát triển hơn, sẽ xuất hiện những nhu cầu như:

- Luôn duy trì một số lượng container nhất định.
- Tự động khởi động lại khi container bị lỗi.
- Scale số lượng container khi lượng truy cập tăng.
- Triển khai phiên bản mới của ứng dụng một cách thuận tiện hơn.

Đó không còn là bài toán của Docker nữa, mà là bài toán quản lý và điều phối container.

Đây cũng chính là mục đích của Amazon ECS (Elastic Container Service).

Có thể hiểu đơn giản, ECS là dịch vụ của AWS giúp quản lý các container đang chạy. Thay vì phải SSH vào từng EC2 và tự thực hiện các lệnh Docker, mình chỉ cần khai báo trạng thái mong muốn của hệ thống, còn ECS sẽ hỗ trợ duy trì trạng thái đó.

Ví dụ, nếu mình muốn luôn có 3 container backend hoạt động, khi một container gặp sự cố và dừng lại thì ECS sẽ tự tạo container mới để thay thế mà không cần mình can thiệp thủ công.

Trong quá trình tìm hiểu, mình cũng biết ECS có hai cách triển khai:

- **EC2 Launch Type:** mình vẫn sử dụng EC2 nhưng ECS sẽ quản lý các container chạy trên những EC2 đó.
- **AWS Fargate:** không cần quản lý EC2, chỉ cần khai báo container và AWS sẽ quản lý hạ tầng phía dưới.

Điều mình thấy thú vị là ECS không thay thế Docker.

Docker vẫn là công cụ để tạo container, còn ECS giúp quản lý những container đó khi ứng dụng bắt đầu lớn hơn và việc vận hành trở nên phức tạp hơn.

Sau khi đọc tài liệu, mình hiểu vì sao trong rất nhiều kiến trúc trên AWS, Docker và ECS thường đi cùng nhau. Một bên giúp đóng gói ứng dụng, còn một bên giúp triển khai và vận hành các container một cách hiệu quả hơn.

## Tài liệu tham khảo

- [Amazon Elastic Container Service Documentation](https://docs.aws.amazon.com/ecs/)

## Liên kết bài viết đã đăng

- [Xem bài viết trên AWS Study Group](https://www.facebook.com/groups/awsstudygroupfcj/permalink/2224875461610747/)