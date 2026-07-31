---
title: "Task và Service trong Amazon ECS khác nhau như thế nào?"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

Trong quá trình tìm hiểu Amazon ECS, em thường gặp hai khái niệm Task và Service. Cả hai đều liên quan đến container nhưng giải quyết hai nhu cầu khác nhau.

## Bắt đầu từ Task Definition

Container trong ECS được cấu hình bằng **Task Definition**. Đây là bản thiết kế khai báo container image, CPU, bộ nhớ, port, biến môi trường, IAM Role, logging và volume.

Có thể hiểu:

- **Task Definition:** bản thiết kế có version/revision.
- **Task:** một lần chạy của Task Definition.
- **Service:** bộ điều khiển duy trì các Task theo trạng thái mong muốn.

## Task là gì?

Task là một instance đang chạy của Task Definition trong ECS cluster. Task có thể chứa một hoặc nhiều container được định nghĩa cùng nhau.

Khi chạy một standalone Task, ECS khởi tạo workload theo Task Definition. Khi Task dừng, không có ECS Service nào duy trì `desiredCount` để tự động thay thế nó. Việc chạy lại cần được kích hoạt bởi người dùng hoặc một cơ chế khác, chẳng hạn Amazon EventBridge Scheduler.

Standalone Task phù hợp với:

- Batch processing.
- Database migration.
- Tác vụ một lần.
- Công việc chạy theo lịch.
- Worker có vòng đời hữu hạn.

Task không nhất thiết phải là tác vụ ngắn; điểm quan trọng là nó không được một ECS Service quản lý để duy trì số lượng mong muốn.

## Service là gì?

ECS Service chạy và duy trì một số lượng Task Definition instances trong cluster. Giá trị `desiredCount` cho biết số Task mà Service cần cố gắng duy trì.

Ví dụ, với `desiredCount = 3`:

1. Service scheduler cố gắng giữ ba Task hoạt động.
2. Nếu một Task dừng hoặc không khỏe, scheduler khởi chạy Task thay thế.
3. Quá trình tiếp tục cho đến khi trạng thái thực tế trở về số lượng mong muốn.

Service phù hợp với Web application, REST API hoặc stateless application cần chạy lâu dài. Service có thể tích hợp với:

- Application, Network hoặc Gateway Load Balancer tùy trường hợp hỗ trợ.
- Service Auto Scaling.
- Rolling deployment và các deployment strategy/controller được ECS hỗ trợ.
- Health check của container hoặc target group.
- Service Connect và service discovery.

## So sánh Task và Service

| Tiêu chí | Task | Service |
| --- | --- | --- |
| Vai trò | Đơn vị thực thi workload | Quản lý vòng đời của Task |
| Nguồn cấu hình | Task Definition | Task Definition và Service configuration |
| Duy trì số lượng | Không với standalone Task | Có qua `desiredCount` |
| Tự thay thế khi lỗi | Không do Service quản lý | Service scheduler có thể thay thế |
| Trường hợp phổ biến | Batch, migration, scheduled job | Web/API/stateless long-running app |
| Load balancer | Không phải mô hình duy trì backend target | Tích hợp trực tiếp với ECS Service |
| Deployment | Chạy một revision được chọn | Quản lý thay Task khi cập nhật revision |

## Liên hệ với Cloud E-Wallet

Backend Cloud E-Wallet hiện chạy bằng `docker run` trên một EC2 và chưa dùng ECS. Nếu nghiên cứu chuyển backend sang ECS, mô hình phù hợp sẽ là ECS Service vì API cần chạy liên tục, duy trì Task và kết nối với ALB. Database migration hoặc cleanup job có thể phù hợp hơn với standalone/scheduled Task.

## Kết luận

Task và Service không phải hai cách tương đương để chạy container:

- **Task** là đơn vị thực thi một Task Definition.
- **Service** duy trì và quản lý các Task dài hạn theo trạng thái mong muốn.

Hiểu rõ quan hệ Task Definition → Task → Service giúp lựa chọn đúng mô hình cho từng workload và tránh nhầm lẫn giữa chạy một lần với vận hành ứng dụng liên tục.

## Tài liệu tham khảo

- [Amazon ECS Tasks](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ecs_tasks.html)
- [Amazon ECS Services](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ecs_services.html)
- [Bài đăng trên AWS Study Group](https://www.facebook.com/groups/awsstudygroupfcj/permalink/2226867424744884/)


