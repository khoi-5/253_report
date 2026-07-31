---
title: "Task và Service trong Amazon ECS khác nhau như thế nào?"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

Trong quá trình tìm hiểu về Amazon ECS, mình nhận thấy hai khái niệm thường xuyên xuất hiện là Task và Service. Thoạt nhìn, cả hai đều liên quan đến việc chạy container nên khá dễ nhầm lẫn. Tuy nhiên, sau khi đọc tài liệu của AWS, mình nhận ra chúng được thiết kế để giải quyết hai nhu cầu hoàn toàn khác nhau trong quá trình vận hành ứng dụng.

Để hiểu rõ sự khác biệt, trước tiên cần biết rằng mọi container trên Amazon ECS đều được khởi tạo từ Task Definition. Đây là nơi định nghĩa toàn bộ cấu hình cần thiết như container image, CPU, bộ nhớ, cổng mạng, biến môi trường, IAM Role hay các volume được sử dụng. Có thể xem Task Definition như một “bản thiết kế”, còn Task là một lần thực thi của bản thiết kế đó.

Khi tạo một Task, Amazon ECS sẽ khởi chạy container theo đúng cấu hình đã được định nghĩa. Sau khi Task hoàn thành hoặc bị dừng, ECS sẽ không tự động tạo lại một Task mới. Nói cách khác, Task chỉ đại diện cho một phiên chạy của ứng dụng tại một thời điểm nhất định.

Chính vì đặc điểm này, Task thường được sử dụng cho các tác vụ ngắn hạn hoặc chỉ cần thực hiện một lần, chẳng hạn như xử lý dữ liệu theo lô (batch processing), chạy migration cơ sở dữ liệu, thực hiện các tác vụ định kỳ hoặc các công việc nền không yêu cầu duy trì liên tục.

Trong khi đó, Service được xây dựng để giải quyết bài toán duy trì trạng thái mong muốn của hệ thống. Thay vì chỉ khởi chạy container, Service sẽ liên tục theo dõi các Task và đảm bảo số lượng Task đang hoạt động luôn đúng với cấu hình đã khai báo.

Ví dụ, nếu một Service được cấu hình duy trì ba Task thì Amazon ECS sẽ luôn cố gắng đảm bảo có đúng ba Task đang chạy. Khi một Task gặp sự cố hoặc dừng hoạt động, Service sẽ tự động tạo một Task mới để thay thế mà không cần sự can thiệp của người quản trị. Đây cũng là cơ chế giúp nhiều ứng dụng web duy trì khả năng phục vụ liên tục ngay cả khi một container gặp lỗi.

Ngoài việc duy trì số lượng Task, Service còn tích hợp với nhiều tính năng khác của AWS như Application Load Balancer (ALB), Auto Scaling hay Rolling Deployment. Nhờ đó, khi triển khai phiên bản mới của ứng dụng, ECS có thể thay thế các Task cũ bằng Task mới theo từng bước, giảm thiểu thời gian gián đoạn dịch vụ và hạn chế ảnh hưởng đến người dùng.

Nếu nhìn dưới góc độ vận hành, có thể xem Task là đơn vị thực thi ứng dụng, còn Service là thành phần chịu trách nhiệm quản lý vòng đời của các Task đó. Service không trực tiếp chạy container mà giám sát, khởi tạo và thay thế Task khi cần thiết để hệ thống luôn đạt trạng thái mong muốn.

Đây cũng là lý do vì sao trong hầu hết các ứng dụng web hoặc API triển khai trên Amazon ECS, Service gần như luôn được sử dụng thay vì chỉ chạy các Task riêng lẻ. Ngược lại, đối với những công việc chỉ cần thực hiện một lần hoặc chạy theo lịch, việc tạo một Task độc lập sẽ đơn giản và phù hợp hơn.

Sau khi tìm hiểu, mình nhận thấy Task và Service không phải là hai cách khác nhau để chạy container mà là hai thành phần bổ trợ lẫn nhau trong kiến trúc của Amazon ECS. Task chịu trách nhiệm thực thi khối lượng công việc, còn Service đảm bảo các Task đó luôn được duy trì đúng số lượng, sẵn sàng phục vụ và có thể tự động phục hồi khi xảy ra sự cố. Hiểu rõ vai trò của từng thành phần sẽ giúp việc triển khai và vận hành ứng dụng trên Amazon ECS trở nên dễ dàng và hiệu quả hơn.

## Tài liệu tham khảo

- [Amazon ECS Services](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ecs_services.html)
- [Amazon ECS Tasks](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ecs_tasks.html)

## Liên kết bài viết đã đăng

- [Xem bài viết trên AWS Study Group](https://www.facebook.com/groups/awsstudygroupfcj/permalink/2226867424744884/)