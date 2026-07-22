---
title: "Worklog Tuần 5"
date: 2026-05-23
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


### Mục tiêu tuần 5:

- Tìm hiểu các dịch vụ bảo mật trên AWS và mô hình trách nhiệm chia sẻ giữa AWS và người dùng.
- Nắm được vai trò của IAM trong quản lý định danh, phân quyền và kiểm soát truy cập.
- Tìm hiểu Amazon Cognito, AWS Organizations, AWS Identity Center, KMS và Security Hub.
- Thực hành bật Security Hub và kiểm tra điểm đánh giá theo bộ tiêu chuẩn bảo mật.
- Thực hành quản lý tag, resource group và sử dụng tag với AWS CLI.
- Thực hành tạo IAM user, policy, role, switch role và kiểm tra quyền truy cập.
- Thực hành giới hạn quyền người dùng IAM bằng restriction policy.
- Thực hành mã hóa dữ liệu với KMS, lưu trữ trên S3, ghi log bằng CloudTrail và truy vấn log bằng Athena.
- Thực hành giới hạn switch role theo IP và thời gian.
- Thực hành so sánh cách sử dụng access key và IAM role trong truy cập tài nguyên AWS.
- Biết cách kiểm tra kết quả và dọn dẹp tài nguyên sau khi hoàn thành lab.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 6 | Tìm hiểu Shared Responsibility Model, IAM, Cognito, Organizations, Identity Center, KMS, Security Hub và thực hành Lab18 | 15/05/2026 | 15/05/2026 | <https://000018.awsstudygroup.com/> |
| 2 | Thực hành Lab22 về tối ưu chi phí EC2 với Lambda, Slack webhook, tag instance, start/stop EC2 và kiểm tra kết quả | 18/05/2026 | 18/05/2026 | <https://000022.awsstudygroup.com/> |
| 3 | Thực hành Lab27 và Lab28 về quản lý tag, resource group, IAM user, policy, role, switch role và kiểm tra policy | 19/05/2026 | 19/05/2026 | <https://000027.awsstudygroup.com/><br><https://000028.awsstudygroup.com/> |
| 4 | Thực hành Lab30 và Lab33 về restriction policy, IAM limited user, KMS, S3, CloudTrail, Athena và dữ liệu mã hóa | 20/05/2026 | 20/05/2026 | <https://000030.awsstudygroup.com/><br><https://000033.awsstudygroup.com/> |
| 5 | Thực hành Lab44 và Lab48 về IAM group, users, permissions, admin role, switch role, access key, IAM role và tổng hợp tuần 5 | 21/05/2026 | 21/05/2026 | <https://000044.awsstudygroup.com/><br><https://000048.awsstudygroup.com/> |

### Kết quả đạt được tuần 5:

- Nắm được mô hình Shared Responsibility Model trong bảo mật trên AWS.
- Phân biệt được phần trách nhiệm bảo mật thuộc về AWS và phần trách nhiệm thuộc về người dùng.
- Nắm được vai trò của IAM trong quản lý định danh và phân quyền truy cập trên AWS.
- Hiểu được các thành phần chính của IAM như user, group, policy và role.
- Nắm được vai trò của Amazon Cognito trong quản lý xác thực người dùng cho ứng dụng.
- Nắm được vai trò của AWS Organizations trong quản lý nhiều tài khoản AWS.
- Nắm được vai trò của AWS Identity Center trong quản lý truy cập tập trung.
- Nắm được vai trò của AWS Key Management Service trong quản lý khóa mã hóa.
- Nắm được vai trò của AWS Security Hub trong tổng hợp và đánh giá trạng thái bảo mật.
- Kích hoạt được AWS Security Hub theo nội dung Lab18.
- Kiểm tra được điểm đánh giá theo từng bộ tiêu chuẩn bảo mật trong Security Hub.
- Thực hiện cleanup tài nguyên sau Lab18.
- Tạo được VPC, Security Group và EC2 instance phục vụ nội dung Lab22.
- Cấu hình được Incoming Webhooks Slack để nhận thông báo theo nội dung lab.
- Tạo được tag cho EC2 instance.
- Tạo được IAM role cho Lambda.
- Tạo được Lambda function để stop EC2 instance.
- Tạo được Lambda function để start EC2 instance.
- Kiểm tra được kết quả start/stop instance sau khi chạy Lambda function.
- Thực hiện cleanup tài nguyên sau Lab22.
- Tạo được EC2 instance có gắn tag theo nội dung Lab27.
- Quản lý được tag trong AWS Resources.
- Lọc được tài nguyên theo tag.
- Sử dụng được tag với AWS CLI.
- Tạo được Resource Group dựa trên tag.
- Thực hiện cleanup tài nguyên sau Lab27.
- Tạo được IAM user theo nội dung Lab28.
- Tạo được IAM Policy để kiểm soát quyền truy cập.
- Tạo được IAM Role và thực hiện Switch Roles.
- Kiểm tra được quyền truy cập EC2 console ở các region khác nhau.
- Kiểm tra được trường hợp tạo EC2 instance khi không có tag phù hợp.
- Chỉnh sửa được Resource Tag trên EC2 instance.
- Thực hiện được Policy Check để kiểm tra chính sách truy cập.
- Thực hiện cleanup tài nguyên sau Lab28.
- Tạo được Restriction Policy theo nội dung Lab30.
- Tạo được IAM Limited User.
- Kiểm tra được giới hạn quyền của IAM User sau khi áp dụng policy.
- Thực hiện cleanup tài nguyên sau Lab30.
- Tạo được Policy và Role theo yêu cầu của Lab33.
- Tạo được Group và User phục vụ bài lab bảo mật.
- Tạo được Key Management Service key.
- Tạo được S3 bucket và upload dữ liệu lên S3.
- Tạo được CloudTrail để ghi nhận hoạt động trong tài khoản.
- Kiểm tra được log được ghi vào CloudTrail.
- Tạo được Amazon Athena để truy vấn dữ liệu log.
- Truy xuất được dữ liệu với Athena theo nội dung lab.
- Kiểm tra và chia sẻ được dữ liệu mã hóa trên S3.
- Thực hiện cleanup tài nguyên sau Lab33.
- Tạo được IAM Group theo nội dung Lab44.
- Tạo được IAM Users và kiểm tra permissions.
- Tạo được Admin IAM Role.
- Cấu hình được Switch Role.
- Giới hạn được Switch Role theo địa chỉ IP.
- Giới hạn được Switch Role theo thời gian.
- Thực hiện cleanup tài nguyên sau Lab44.
- Tạo được EC2 instance và S3 bucket phục vụ Lab48.
- Tạo được IAM user và access key.
- Sử dụng được access key để truy cập tài nguyên AWS theo nội dung lab.
- Tạo được IAM role và sử dụng IAM role để truy cập tài nguyên AWS.
- Phân biệt được cách sử dụng access key và IAM role trong thực hành truy cập tài nguyên.
- Thực hiện cleanup tài nguyên sau Lab48.
- Hoàn thành các lab chính trong tuần 5 gồm Lab18, Lab22, Lab27, Lab28, Lab30, Lab33, Lab44 và Lab48.
- Hình thành thói quen kiểm tra quyền truy cập, đánh giá rủi ro bảo mật và dọn dẹp tài nguyên sau khi thực hành.
