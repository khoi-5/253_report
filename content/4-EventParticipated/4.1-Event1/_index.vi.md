---
title: "Cuộc thi kiến thức AWS dành cho thực tập sinh"
date: 2026-06-20
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---



## Thông tin sự kiện

- **Thời gian:** Ngày 20/06/2026
- **Đơn vị tổ chức:** First Cloud AI Journey (FCAJ)
- **Đối tượng tham gia:** Các sinh viên đang thực tập trong chương trình FCAJ
- **Vai trò của em:** Khán giả theo dõi cuộc thi
- **Quy mô:** 8 đội tham gia

## Mục đích của sự kiện

- Tạo sân chơi giúp các thực tập sinh ôn tập và vận dụng kiến thức AWS đã học.
- Kiểm tra khả năng phân tích kiến trúc, lựa chọn dịch vụ và xử lý tình huống cloud.
- Giúp người tham dự quan sát cách các đội thảo luận, thống nhất quyết định và chịu trách nhiệm với đáp án chung.
- Tạo cơ hội giao lưu và học hỏi giữa các nhóm thực tập sinh.

## Hình thức thi đấu

Cuộc thi có 8 đội tham gia và được tổ chức theo các vòng đấu loại trực tiếp. Ngày em tham dự diễn ra phần còn lại của **vòng tứ kết** và **vòng bán kết**. Mỗi vòng gồm **10 câu hỏi trắc nghiệm** về AWS; các thành viên trong đội có thời gian đọc đề, phân tích lựa chọn và thống nhất một đáp án đại diện. Em tham dự với vai trò khán giả, theo dõi cách các đội xử lý câu hỏi và đối chiếu đáp án với kiến thức đã học.

Các câu hỏi được xây dựng theo hai nhóm kiến thức có độ khó khác nhau:

- Nhóm kiến thức nền tảng, tương ứng với nội dung thường gặp trong **AWS Certified Cloud Practitioner**.
- Nhóm câu hỏi kiến trúc và tình huống có độ khó cao hơn, gần với nội dung của **AWS Certified Solutions Architect**.

Hai nhóm câu hỏi giúp cuộc thi vừa kiểm tra kiến thức AWS cơ bản, vừa yêu cầu người tham gia vận dụng nhiều dịch vụ để phân tích một kiến trúc hoặc tình huống thực tế.

## Nội dung nổi bật

### Kiến thức AWS và Cloud

Các câu hỏi bao phủ nhiều chủ đề đã được học trước sự kiện, gồm:

- Mô hình trách nhiệm chung và các nguyên tắc cơ bản của AWS Cloud.
- IAM, phân quyền và bảo mật tài khoản.
- Amazon EC2, container và lựa chọn dịch vụ compute.
- Amazon S3, cơ sở dữ liệu và các hình thức lưu trữ.
- VPC, subnet, định tuyến và kết nối mạng.
- Khả năng mở rộng, tính sẵn sàng cao và tối ưu chi phí.
- AWS Organizations, Service Control Policy và cách quản trị nhiều tài khoản.

Một số câu hỏi mô tả kiến trúc hoặc sự cố cụ thể. Qua việc theo dõi, em nhận thấy các đội không thể chỉ ghi nhớ tên dịch vụ mà phải xác định yêu cầu, loại trừ phương án chưa phù hợp và chọn giải pháp đáp ứng tốt nhất các điều kiện của đề bài.

### Quan sát quá trình thảo luận và thống nhất đáp án

Mỗi thành viên có thể hiểu câu hỏi theo một hướng khác nhau. Vì vậy, đội cần trình bày ngắn gọn cơ sở lựa chọn, lắng nghe ý kiến phản biện và thống nhất đáp án trước khi hết thời gian. Khi xuất hiện nhiều phương án gần giống nhau, việc dựa vào từ khóa và điều kiện trong đề giúp cuộc thảo luận tập trung hơn.

Qua việc quan sát, em nhận ra rằng làm việc nhóm không đơn thuần là chọn đáp án theo số đông. Một quyết định chung cần có lý do rõ ràng, đồng thời các thành viên phải sẵn sàng thay đổi lựa chọn khi có lập luận thuyết phục hơn.

## Những gì học được

### Củng cố kiến thức

- Ôn lại các dịch vụ AWS và kiến thức cloud đã học trong thời gian trước sự kiện.
- Hiểu rõ hơn mối liên hệ giữa IAM, Organizations, networking, compute, storage và database trong một kiến trúc.
- Luyện cách đọc câu hỏi tình huống, xác định yêu cầu chính và loại trừ đáp án không phù hợp.
- Nhận ra những phần kiến thức còn nhầm lẫn để tiếp tục tìm hiểu sau cuộc thi.

### Ví dụ câu hỏi và bài học về Service Control Policy

Một câu hỏi xuất hiện trong cuộc thi mô tả tình huống: doanh nghiệp quản lý nhiều tài khoản bằng **AWS Organizations**, một tài khoản mới được thêm vào Organizational Unit (OU) và đã được áp dụng Service Control Policy (SCP) để từ chối một số thao tác Amazon ECS. Tuy nhiên, các thao tác đó vẫn được thực hiện thông qua một **service-linked role**. Câu hỏi yêu cầu xác định nguyên nhân.

**Đáp án đúng:** SCP không ảnh hưởng đến service-linked role.

Service-linked role là IAM role được một dịch vụ AWS định nghĩa và sử dụng để thay mặt người dùng thực hiện các tác vụ cần thiết. AWS Organizations không dùng SCP để hạn chế quyền của service-linked role. Vì vậy, thao tác do role này thực hiện vẫn có thể xảy ra dù SCP đã từ chối cùng hành động đối với IAM user hoặc role thông thường trong tài khoản.

Các phương án còn lại không phù hợp vì:

- Một policy cho phép ở OU cấp cao hơn không thể ghi đè một lệnh `Deny` rõ ràng; explicit deny luôn được ưu tiên.
- SCP áp dụng theo tài khoản và OU trong AWS Organizations, không mất hiệu lực chỉ vì dịch vụ chạy ở Region khác.
- SCP mặc định `FullAWSAccess` không cấp quyền và cũng không ghi đè policy từ chối; SCP chỉ thiết lập giới hạn quyền tối đa cho tài khoản thành viên.

Qua câu hỏi này, em phân biệt rõ hơn giữa **IAM policy**, **SCP** và **service-linked role**, đồng thời hiểu rằng khi phân tích quyền trên AWS cần xác định chính xác principal nào đang thực hiện hành động.
### Bài học về làm việc nhóm

Qua việc quan sát các đội thi, em học được cách trình bày ý kiến ngắn gọn, lắng nghe và so sánh các lập luận trước khi đưa ra quyết định chung. Các đội phối hợp tốt không chỉ dựa vào kiến thức của một cá nhân mà còn biết phân chia thời gian, giữ bình tĩnh và thống nhất phương án khi câu hỏi có độ khó cao.

## Trải nghiệm trong sự kiện

Không khí thi đấu ở vòng tứ kết và bán kết tạo áp lực rõ rệt vì số câu hỏi và thời gian đều giới hạn. Những câu kiến thức nền tảng giúp các đội khởi động và kiểm tra khả năng ghi nhớ, trong khi các câu tình huống khó yêu cầu họ phân tích kỹ kiến trúc và quyền hạn của từng dịch vụ AWS.

Giá trị lớn nhất đối với em nằm ở việc theo dõi quá trình các đội trao đổi để đi đến quyết định. Dù không trực tiếp thi đấu, em vẫn có thể tự phân tích từng câu hỏi, so sánh với đáp án của các đội và hệ thống lại kiến thức đã học. Sự kiện giúp em rèn luyện tư duy phản biện và hiểu rằng trong công việc kỹ thuật, một phương án tốt cần được giải thích bằng yêu cầu và dữ kiện cụ thể.

## Hình ảnh minh chứng

{{< report-image src="images/4-EventParticipated/4.1-Event1/image.png" alt="Teams answering AWS questions during the competition" >}}

<p style="text-align: center;"><em>Hình 4.1. Câu hỏi tình huống về AWS Organizations và Service Control Policy tại cuộc thi.</em></p>

## Tổng kết

Cuộc thi do FCAJ tổ chức đã giúp em củng cố kiến thức AWS và Cloud theo hình thức thực tế, có tính tương tác cao. Bên cạnh việc ôn tập các dịch vụ và kiến trúc, em còn học được cách phân tích nhanh, giải thích lựa chọn và quan sát cách các đội phối hợp để thống nhất quyết định trong thời gian giới hạn.
