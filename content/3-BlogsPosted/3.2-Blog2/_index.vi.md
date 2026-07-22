---
title: "Blog 2"
date: 2026-06-01
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây là phần tổng hợp nội dung blog em đã đọc và đăng trong quá trình thực tập, không phải tài liệu chính thức thay thế cho bài viết gốc của AWS.
{{% /notice %}}

# TỪ MONOLITH ĐẾN MULTI-ACCOUNT: HÀNH TRÌNH CHUYỂN ĐỔI AWS ORGANIZATIONS CỦA PINTEREST

Khi quy mô hệ thống phình to theo tốc độ phát triển của doanh nghiệp, việc duy trì một kiến trúc tài khoản đơn khối (Monolith Account Architecture) sẽ nhanh chóng biến thành một “cơn ác mộng” kinh hoàng về quản trị, vận hành và bảo mật. Thời gian qua, core-team của tụi mình đã dành nhiều tuần để “mổ xẻ” và phân tích sâu (deep-dive) hành trình lột xác hạ tầng cực kỳ kinh điển của Pinterest trên AWS Blog. Bài viết này là những đúc kết chuyên sâu nhất về cách họ phá vỡ chiếc áo Monolith chật chội để chuyển dịch sang chiến lược Multi-Account quy mô lớn.

━━━━━━━━━━━━━━━

## “Nỗi đau” của kiến trúc cũ và lý do phải chuyển dịch

Trước khi thực hiện cuộc cách mạng này, Pinterest vận hành với một số lượng rất ít tài khoản AWS nhưng chứa hàng vạn tài nguyên khổng lồ. Điều này dẫn đến 3 bài toán nan giải:

- **Rủi ro bảo mật và Blast Radius quá lớn:** Chỉ cần một sai sót cấu hình nhỏ từ môi trường Development cũng có nguy cơ làm ảnh hưởng gián tiếp đến toàn bộ hệ thống Production do dùng chung một mạng VPC hoặc chung tài khoản.
- **Cạn kiệt API Limits và AWS Service Quotas:** Ở quy mô hàng triệu request, các script tự động hóa hoặc công cụ giám sát liên tục call API lên AWS Core Services (như EC2, S3), dẫn đến tình trạng tài khoản bị Throttling diện rộng, khiến các tác vụ quan trọng bị đình trệ.
- **Khó kiểm soát và phân bổ chi phí:** Đội ngũ tài chính hoàn toàn “bó tay” trong việc bóc tách chính xác từng đô-la trên hóa đơn tổng thuộc về microservice nào hay team kỹ sư nào đang chịu trách nhiệm.

━━━━━━━━━━━━━━━

## Giải pháp kiến trúc mới: Bộ ba dịch vụ quản trị từ AWS

Để giải quyết triệt để, Pinterest đã phối hợp triển khai bộ ba giải pháp cốt lõi của AWS bao gồm: AWS Organizations + AWS Control Tower + AWS IAM Identity Center.

Thay vì gom tất cả các workload vào một nơi, họ đã phân rã hệ thống thành một cấu trúc phân cấp chặt chẽ thông qua các Đơn vị tổ chức (OU - Organizational Units).

━━━━━━━━━━━━━━━

## Cấu trúc Organizational Units

| Đơn vị tổ chức (OU) | Vai trò trong hệ thống | Cơ chế quản trị |
| --- | --- | --- |
| OU Core Infrastructure | Cô lập các dịch vụ dùng chung nền tảng | Quản lý Shared VPCs, Networking Core và Centralized Registry |
| OU Business Units (Sản phẩm) | Chia nhỏ theo từng team tính năng như Home Feed, Search và Ads | Mỗi team sở hữu ba tài khoản biệt lập gồm Dev, Staging và Prod |
| OU Security & Governance | Đóng vai trò kiểm toán và quản trị bảo mật | Chứa tài khoản Log Archive và Audit |

━━━━━━━━━━━━━━━

## Chiến lược tối ưu chi phí và vận hành

Nhờ việc phân rã này, Pinterest đã áp dụng thành công các chính sách quản trị tối cao Service Control Policies (SCPs):

- **Kiểm soát tài nguyên tại Dev và Staging:** Chặn đứng hoàn toàn việc khởi tạo các loại EC2 Instance đắt đỏ (như dòng P-series hay X-series) khi không có sự phê duyệt trước, giúp tiết kiệm hàng trăm ngàn USD chi phí lãng phí.
- **Thu gom log tập trung:** Toàn bộ dữ liệu logs từ Amazon CloudTrail, Amazon CloudWatch và Amazon GuardDuty được nén và đẩy bất đồng bộ về một Data Lake bảo mật duy nhất, giúp loại bỏ chi phí lưu trữ trùng lặp ở các tài khoản con.

━━━━━━━━━━━━━━━

## Bốn bài học kỹ thuật cốt lõi dành cho kỹ sư Cloud

### 1. Thiết lập Landing Zone chuẩn ngay từ đầu

Sử dụng AWS Control Tower để tự động hóa quy trình Account Factory. Mỗi khi một team mới cần tài nguyên, hệ thống tự động sinh ra một AWS Account sạch, được tích hợp sẵn Guardrails bảo mật mà không cần can thiệp thủ công bằng tay.

### 2. Áp dụng Service Control Policies như một chốt chặn chủ động

Đừng đợi đến khi nhận hóa đơn “vọt xà” mới đi tìm giải pháp tối ưu. Hãy dùng SCPs để kiểm soát hạ tầng ở mức cao nhất, giới hạn các AWS Regions được phép hoạt động để thu hẹp Blast Radius.

### 3. Quản trị định danh tập trung với IAM Identity Center

Loại bỏ hoàn toàn việc tạo IAM User thủ công hoặc sử dụng chung Long-lived Access Keys trên các môi trường. Thay thế hoàn toàn bằng cơ chế SSO (Single Sign-On) liên kết với tài khoản doanh nghiệp, tự động thu hồi quyền sau một khoảng thời gian nhất định để triệt tiêu nguy cơ rò rỉ thông tin.

### 4. Bóc tách chi phí bằng chiến lược tagging nghiêm ngặt

Kết hợp kiến trúc Multi-Account với chính sách ép buộc Tagging (như CostCenter, Environment, Owner). Bất kỳ tài nguyên nào thiếu Tag sẽ bị AWS Config phát hiện và tự động terminate thông qua Lambda Automation.

━━━━━━━━━━━━━━━

## Liên kết tham khảo và thảo luận cộng đồng

Kiến trúc Multi-Account thông qua AWS Organizations không chỉ là một xu hướng công nghệ, mà là điều kiện tiên quyết mang tính “sống còn” cho bất kỳ hệ thống nào muốn hướng tới mục tiêu siêu mở rộng (Hyper-scale). Để giúp anh em có cái nhìn trực quan hơn, core-team tụi mình đã vẽ và biên soạn lại toàn bộ sơ đồ phân cấp OU của Pinterest, kèm theo các mã cấu hình chính sách mẫu (SCPs template) rất chi tiết trên blog của nhóm.

Mời anh em cùng click vào các đường link bên dưới để đọc bài viết đầy đủ, và hãy thoải mái để lại bình luận xem hệ thống của anh em đã chuyển sang Multi-Account chưa, hay vẫn đang “gồng gánh” với Monolith Account nhé!

━━━━━━━━━━━━━━━

## Link bài gốc

AWS Cloud Operations Blog:  
https://aws.amazon.com/vi/blogs/mt/from-monolith-to-multi-account-pinterests-aws-organization-transformation-journey/

AWS Study Group:  
https://www.facebook.com/groups/awsstudygroupfcj/permalink/2200922960672664/

## Hình ảnh