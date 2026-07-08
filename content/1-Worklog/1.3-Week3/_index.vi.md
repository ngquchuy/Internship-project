---
title: "Worklog Tuần 3"
date: 2026-05-09
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


### Mục tiêu tuần 3:

- Tìm hiểu nhóm dịch vụ Compute VM trên AWS, trọng tâm là Amazon EC2.
- Nắm được các thành phần quan trọng của EC2 như instance type, AMI, key pair, EBS, instance store, user data và metadata.
- Hiểu vai trò của EC2 Auto Scaling trong việc mở rộng tài nguyên compute.
- Tìm hiểu thêm các dịch vụ liên quan như EFS, FSx, Lightsail và AWS MGN.
- Thực hành triển khai hạ tầng, tạo backup plan và kiểm tra hoạt động theo Lab13.
- Thực hành sử dụng AWS Storage Gateway để kết nối lưu trữ giữa môi trường on-premise và AWS theo Lab24.
- Thực hành triển khai static website trên Amazon S3 và các thao tác quản lý object theo Lab57.
- Biết cách kiểm tra kết quả và dọn dẹp tài nguyên sau khi hoàn thành lab.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành |
| --- | --- | --- | --- |
| 6 | Tìm hiểu dịch vụ Compute VM trên AWS, Amazon EC2, instance type, AMI, key pair và các thành phần cơ bản của EC2 | 01/05/2026 | 01/05/2026 |
| 2 | Tìm hiểu EBS, instance store, backup trên EC2 và thực hành Lab13 về triển khai hạ tầng, backup plan | 04/05/2026 | 04/05/2026 |
| 3 | Tìm hiểu user data, metadata, EC2 Auto Scaling, EFS, FSx, Lightsail, MGN và hoàn thiện kiểm tra/dọn dẹp Lab13 | 05/05/2026 | 05/05/2026 |
| 4 | Thực hành Lab24 về S3 Bucket, EC2 cho Storage Gateway, tạo Storage Gateway và File Shares | 06/05/2026 | 06/05/2026 |
| 5 | Thực hành Lab57 về static website trên S3, bucket versioning, di chuyển/sao chép object và tổng hợp kết quả tuần 3 | 07/05/2026 | 07/05/2026 |

### Kết quả đạt được tuần 3:

- Nắm được vai trò của nhóm dịch vụ Compute VM trên AWS trong việc cung cấp máy chủ ảo cho hệ thống.
- Hiểu được vai trò của Amazon EC2 trong việc triển khai máy chủ ảo trên AWS.
- Phân biệt được các loại EC2 instance type và ý nghĩa của việc lựa chọn cấu hình phù hợp với nhu cầu sử dụng.
- Hiểu được vai trò của AMI trong việc tạo EC2 instance từ image hệ điều hành hoặc image đã cấu hình sẵn.
- Nắm được vai trò của key pair trong quá trình xác thực và kết nối đến EC2 instance.
- Hiểu được sự khác nhau giữa EBS và instance store trong lưu trữ dữ liệu cho EC2.
- Nắm được vai trò của EBS volume trong việc cung cấp block storage gắn với EC2 instance.
- Hiểu được mục đích sử dụng user data để tự động hóa một số bước cấu hình khi EC2 instance khởi tạo.
- Hiểu được vai trò của instance metadata trong việc cung cấp thông tin cấu hình và thông tin liên quan đến EC2 instance.
- Nắm được vai trò của EC2 Auto Scaling trong việc tự động điều chỉnh số lượng instance theo nhu cầu tải.
- Nhận biết được vai trò cơ bản của EFS và FSx trong nhóm dịch vụ file storage trên AWS.
- Nhận biết được vai trò của Lightsail như một lựa chọn đơn giản để triển khai máy chủ hoặc ứng dụng nhỏ.
- Nhận biết được vai trò của AWS Application Migration Service (MGN) trong việc hỗ trợ di chuyển workload lên AWS.
- Triển khai được hạ tầng theo các bước chuẩn bị trong Lab13.
- Tạo được backup plan theo nội dung Lab13.
- Kiểm tra được hoạt động của backup plan sau khi cấu hình.
- Thực hiện cleanup tài nguyên sau Lab13 để hạn chế phát sinh chi phí.
- Tạo được S3 bucket phục vụ cho nội dung thực hành Storage Gateway trong Lab24.
- Tạo được EC2 instance dùng cho môi trường Storage Gateway theo yêu cầu lab.
- Tạo được Storage Gateway theo nội dung Lab24.
- Tạo được File Shares để kết nối lưu trữ giữa môi trường on-premise và AWS.
- Kết nối được File Shares ở máy on-premise theo nội dung thực hành.
- Thực hiện cleanup tài nguyên sau Lab24.
- Bật được tính năng Static Website Hosting trên S3 theo nội dung Lab57.
- Cấu hình được Block Public Access và quyền truy cập public object phù hợp với yêu cầu static website.
- Kiểm tra được website tĩnh được host trên Amazon S3.
- Thực hiện được thao tác tăng tốc static website host trên S3 theo nội dung lab.
- Bật và sử dụng được tính năng bucket versioning.
- Thực hiện được thao tác di chuyển object trong S3.
- Thực hiện được thao tác sao chép S3 object sang region khác.
- Thực hiện cleanup tài nguyên sau Lab57.
- Hoàn thành các lab chính trong tuần 3 gồm Lab13, Lab24 và Lab57.
- Hình thành thói quen kiểm tra trạng thái tài nguyên, kết quả lab và dọn dẹp tài nguyên sau khi thực hành.


