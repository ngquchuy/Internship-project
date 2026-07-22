---
title: "Worklog Tuần 2"
date: 2026-05-02
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


### Mục tiêu tuần 2:

- Tìm hiểu Amazon VPC và các thành phần networking nền tảng trên AWS.
- Hiểu cách thiết kế subnet, route table, Internet Gateway và NAT Gateway.
- Nắm được vai trò của Security Group và Network ACL trong bảo mật mạng.
- Thực hành tạo VPC, subnet, route table, Internet Gateway, NAT Gateway và EC2 instance trong subnet.
- Tìm hiểu Hybrid DNS với Route 53 Resolver.
- Thực hành VPC Peering và Transit Gateway để kết nối nhiều VPC.
- Biết cách kiểm tra kết nối, cấu hình route và cleanup tài nguyên sau lab.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 6 | Tìm hiểu Amazon VPC, subnet, route table, Internet Gateway và thực hành phần đầu Lab03 | 24/04/2026 | 24/04/2026 | <https://000003.awsstudygroup.com/> |
| 2 | Tìm hiểu VPC Security, NAT Gateway, Security Group, Network ACL và hoàn thành Lab03 | 27/04/2026 | 27/04/2026 | <https://000003.awsstudygroup.com/> |
| 3 | Tìm hiểu Hybrid DNS, VPN/Direct Connect ở mức khái niệm và thực hành Lab10 với Route 53 Resolver | 28/04/2026 | 28/04/2026 | <https://000003.awsstudygroup.com/> |
| 4 | Tìm hiểu Multi-VPC features và thực hành Lab19 với VPC Peering, route table, NACL và Cross-Peer DNS | 29/04/2026 | 29/04/2026 | <https://000003.awsstudygroup.com/> |
| 5 | Tìm hiểu Transit Gateway, Load Balancer/extra resources ở mức tổng quan và thực hành Lab20 | 30/04/2026 | 30/04/2026 | <https://000003.awsstudygroup.com/> |

### Kết quả đạt được tuần 2:

- Nắm được vai trò của Amazon VPC trong việc tạo mạng riêng ảo trên AWS.
- Phân biệt được public subnet và private subnet trong mô hình VPC.
- Hiểu được vai trò của route table trong việc điều hướng traffic giữa các subnet và ra Internet.
- Cấu hình được Internet Gateway để cho phép tài nguyên trong public subnet truy cập Internet.
- Cấu hình được NAT Gateway để hỗ trợ tài nguyên trong private subnet truy cập Internet theo chiều outbound.
- Phân biệt được Security Group và Network ACL về phạm vi áp dụng, cách hoạt động và mục đích sử dụng.
- Tạo được VPC, subnet, route table, Internet Gateway, security group và EC2 instance theo yêu cầu của Lab03.
- Kiểm tra được kết nối giữa các EC2 instance trong subnet và kết nối ra Internet theo cấu hình route.
- Sử dụng được VPC Resource Map để quan sát các thành phần mạng đã tạo trong VPC.
- Làm quen với EC2 Instance Connect Endpoint trong quá trình kết nối đến EC2 instance.
- Nắm được khái niệm VPN Site-to-Site và vai trò của VPN trong kết nối môi trường on-premises với AWS.
- Nắm được khái niệm Direct Connect và vai trò của Direct Connect trong kết nối mạng chuyên dụng đến AWS.
- Hiểu được vai trò cơ bản của Load Balancer trong việc phân phối traffic đến nhiều tài nguyên phía sau.
- Nắm được mô hình Hybrid DNS với Route 53 Resolver.
- Tạo được key pair và sử dụng CloudFormation template trong quá trình chuẩn bị môi trường lab.
- Cấu hình được Security Group phục vụ kết nối đến tài nguyên trong lab.
- Kết nối được đến RDGW theo nội dung Lab10.
- Tạo được Route 53 Outbound Endpoint, Resolver Rules và Inbound Endpoints theo yêu cầu lab.
- Kiểm tra được kết quả phân giải DNS trong mô hình Hybrid DNS.
- Nắm được cách sử dụng VPC Peering để kết nối hai VPC với nhau.
- Tạo được peering connection giữa các VPC theo nội dung Lab19.
- Cấu hình được route table để các VPC giao tiếp thông qua VPC Peering.
- Cập nhật được Network ACL để cho phép traffic phù hợp trong mô hình kết nối.
- Bật được Cross-Peer DNS để hỗ trợ phân giải DNS giữa các VPC được peering.
- Nắm được vai trò của AWS Transit Gateway trong mô hình kết nối nhiều VPC.
- Tạo được Transit Gateway, Transit Gateway Attachments và Transit Gateway Route Tables theo nội dung Lab20.
- Thêm được route vào VPC route table để điều hướng traffic qua Transit Gateway.
- Biết cách kiểm tra kết nối sau khi cấu hình VPC Peering và Transit Gateway.
- Thực hiện cleanup tài nguyên sau các lab để hạn chế phát sinh chi phí không cần thiết.
- Hoàn thành các lab chính trong tuần 2 gồm Lab03, Lab10, Lab19 và Lab20.


