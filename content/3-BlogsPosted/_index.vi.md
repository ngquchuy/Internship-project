---
title: "Các bài blogs đã đăng"
date: 2026-06-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

{{% notice warning %}}  
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

Tại đây sẽ là phần liệt kê và giới thiệu các blog em đã đăng trong quá trình thực tập, liên quan đến AWS, Cloud Computing, Backend, Database và Generative AI.

### [Blog 1 - XÁC THỰC NGƯỜI DÙNG VÀ QUẢN LÝ SESSION VỚI AMAZON AURORA DSQL](3.1-Blog1/)

Blog này giới thiệu cách xây dựng hệ thống xác thực người dùng và quản lý session bằng Amazon Aurora DSQL. Nội dung tập trung vào bài toán backend authentication trong môi trường cần khả năng mở rộng, tính nhất quán mạnh và bảo mật tốt. Giải pháp sử dụng Aurora DSQL kết hợp với Amazon ECS, AWS Fargate và IAM authentication để xây dựng một dịch vụ xác thực theo hướng hiện đại, hạn chế việc quản lý database instance thủ công và giảm rủi ro khi xử lý thông tin nhạy cảm như mật khẩu hoặc session token.

### [Blog 2 - TỪ MONOLITH ĐẾN MULTI-ACCOUNT: HÀNH TRÌNH CHUYỂN ĐỔI AWS ORGANIZATIONS CỦA PINTEREST](3.2-Blog2/)

Blog này trình bày hành trình Pinterest chuyển đổi từ mô hình tài khoản AWS đơn khối sang chiến lược Multi-Account. Nội dung tập trung vào AWS Organizations, AWS Control Tower, AWS IAM Identity Center, Organizational Units, Service Control Policies và cơ chế quản trị tập trung nhằm giảm Blast Radius, hạn chế Service Quotas và cải thiện khả năng phân bổ chi phí.

### [Blog 3 - BÀI HỌC TỪ VIỆC MỞ RỘNG HỆ THỐNG ĐẾN 1 TRIỆU AWS LAMBDA FUNCTIONS](3.3-Blog3/)

Blog này trình bày những bài học kiến trúc khi mở rộng hệ thống Serverless đến quy mô rất lớn. Nội dung tập trung vào AWS Lambda, Amazon SQS và AWS Step Functions, cùng các vấn đề về concurrency, throttling, cold start và cơ chế chịu lỗi bằng Dead-Letter Queue.