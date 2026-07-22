---
title: "Nhật ký công việc"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

Nhật ký công việc (Worklog) này ghi lại toàn bộ quá trình học tập, thực hành và triển khai dự án của tôi trong suốt thời gian thực tập tại đơn vị. Quá trình thực tập được phân chia rõ ràng thành hai giai đoạn chính:

1. **Giai đoạn học tập nền tảng (Tuần 1 - Tuần 6):** Tiếp thu kiến thức cốt lõi về điện toán đám mây và các dịch vụ hạ tầng cơ bản của Amazon Web Services (AWS) thông qua chuỗi bài giảng và thực hành từ playlist "First Cloud Journey Bootcamp". Giai đoạn này được thực hiện trong 6 tuần, bắt đầu từ ngày **17/04/2026** đến ngày **01/06/2026**.
2. **Giai đoạn triển khai dự án (Tuần 7 - Tuần 12):** Nghiên cứu sâu, thiết kế kiến trúc và xây dựng một dự án ứng dụng thực tế trên nền tảng AWS nhằm hoàn thiện báo cáo thực tập tốt nghiệp.

Dưới đây là tóm tắt và liên kết chi tiết nội dung công việc thực hiện theo từng tuần:

**Tuần 1:** [AWS Căn Bản, AWS Console và AWS CLI](1.1-Week1/) (17/04/2026 - 23/04/2026) - Làm quen với lộ trình học tập, tìm hiểu về Cloud computing, AWS Global Infrastructure (Region, AZ, Edge Location), các nhóm dịch vụ cơ bản và thiết lập môi trường AWS CLI.

**Tuần 2:** [IAM, Bảo Mật Tài Khoản và Quản Lý Chi Phí](1.2-Week2/) (24/04/2026 - 01/05/2026) - Tìm hiểu sâu về AWS IAM (User, Group, Role, Policy), kích hoạt MFA để bảo mật tài khoản và thiết lập công cụ quản lý chi phí AWS Budgets.

**Tuần 3:** [Networking với Amazon VPC](1.3-Week3/) (05/05/2026 - 11/05/2026) - Thiết lập hệ thống mạng ảo độc lập Amazon VPC, tìm hiểu và phân chia Public/Private subnet, cấu hình Route Table, Internet Gateway, Security Group và Network ACL.

**Tuần 4:** [Networking Nâng Cao và CloudFormation](1.4-Week4/) (12/05/2026 - 18/05/2026) - Triển khai NAT Gateway phục vụ kết nối một chiều cho Private Subnet, tìm hiểu các phương thức VPC connection, và học cách quản lý hạ tầng bằng mã nguồn (IaC) với AWS CloudFormation.

**Tuần 5:** [Compute, Storage và Backup](1.5-Week5/) (19/05/2026 - 25/05/2026) - Thực hành quản trị máy chủ ảo Amazon EC2 (AMI, Instance Type, Key Pair, Elastic IP), sử dụng dịch vụ lưu trữ EBS & Amazon S3, và thiết lập cơ chế sao lưu tự động với AWS Backup.

**Tuần 6:** [AWS Workshop, Vẽ Kiến Trúc và Tổng Kết](1.6-Week6/) (26/05/2026 - 01/06/2026) - Thực hành các bài lab còn lại trên AWS Workshop, thiết kế sơ đồ kiến trúc chuẩn hóa bằng Draw.io sử dụng bộ AWS Icons, tổng hợp toàn bộ kiến thức 6 tuần và định hướng đề tài dự án.

**Tuần 7:** [Chuẩn bị đề tài và thiết kế hệ thống Project](1.7-Week7/) (02/06/2026 - 08/06/2026) - Giai đoạn nghiên cứu tài liệu, xác định các yêu cầu nghiệp vụ và phác thảo sơ đồ kiến trúc tổng quan của ứng dụng. Phân tích yêu cầu nghiệp vụ và lựa chọn mô hình Serverless Architecture cho hệ thống Video-on-Demand.

**Tuần 8:** [Thiết kế kiến trúc hệ thống cho Project](1.8-Week8/) (09/06/2026 - 15/06/2026) - Tập trung nghiên cứu, thiết kế chi tiết kiến trúc hệ thống, xác định luồng dữ liệu và lựa chọn các dịch vụ AWS tối ưu cho dự án. Nghiên cứu Video pipleline: AWS Elemental MediaConvert.

**Tuần 9:** [Hoàn thiện bản vẽ kiến trúc Project](1.9-Week9/) (16/06/2026 - 22/06/2026) - Tiếp tục rà soát, hoàn thiện thiết kế kiến trúc hệ thống, làm rõ các thành phần bảo mật, mạng và tối ưu chi phí trước khi triển khai. Xây dựng logic xử lý backend, các hàm lambda, hoàn thiện các API nghiệp vụ cốt lỗi.

**Tuần 10:** [Bắt đầu triển khai và xây dựng Project](1.10-Week10/) (23/06/2026 - 29/06/2026) - Xây dựng luồng xử lý video tự động bằng S3, Lambda, MediaConvert. Cấu hình lưu trữ và phân phối nội dung thông qua Amazon CloudFront và S3.

**Tuần 11:** [Phát triển và tích hợp các dịch vụ Project](1.11-Week11/) (30/06/2026 - 06/07/2026) - Lập trình các chức năng cốt lõi của ứng dụng, kết nối các service với dịch vụ AWS Cloud. Tối ưu hóa lớp bảo mật hệ thống với AWS WAF và quản lý truy cập chặt chẽ. Kiểm thử khả năng vận hành của API Gateway và CloudFront.

**Tuần 12:** [Hoàn thiện Project và tổng kết báo cáo](1.12-Week12/) (07/07/2026 - 13/07/2026) - Kiểm thử toàn diện hệ thống, tối ưu hiệu năng, hoàn thiện báo cáo thực tập tốt nghiệp. Hoàn thành phiếu tiến độ và đánh giá.