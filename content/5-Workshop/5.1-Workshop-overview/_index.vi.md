---
title: "Tổng quan Workshop"
date: 2026-07-20
weight: 1
chapter: false
pre: "<b>5.1. </b>"
---

# 5.1. Tổng quan Workshop

## Giới thiệu

Nội dung phần Workshop 5.1 cung cấp cái nhìn tổng quan về quy trình xây dựng và triển khai thực tế hệ thống **Serverless Video-on-Demand Platform on AWS**. Trái ngược với các chương trước vốn tập trung vào phân tích lý thuyết và thiết kế kiến trúc tổng thể, chương Workshop tập trung vào các bước cấu hình thực hành trực tiếp trên hạ tầng đám mây AWS.

Hệ thống được thiết kế hoàn toàn trên mô hình serverless architecture và event-driven architecture nhằm phân tách triệt để giữa các tác vụ tương tác giao diện người dùng đồng bộ và các quy trình xử lý phương tiện bất đồng bộ ngầm. Mô hình này giúp giảm nhu cầu duy trì máy chủ cố định, có khả năng mở rộng theo workload và tự động hóa quy trình xử lý video sau khi các dịch vụ được cấu hình hoàn chỉnh.


## Mục tiêu của Workshop

Sau khi hoàn thành Workshop, người đọc được kỳ vọng có thể triển khai và kiểm thử các chức năng chính của một nền tảng Video-on-Demand trong phạm vi đồ án. Các mục tiêu cụ thể bao gồm:

- Khởi tạo và cấu hình Amazon Cognito User Pool để quản lý định danh, xác thực người dùng và cấp mã JWT.
- Thiết lập Amazon API Gateway kết hợp với JWT Authorizer để bảo mật và định tuyến các yêu cầu API thông qua Amazon API Gateway.
- Phát triển các hàm AWS Lambda thực thi logic nghiệp vụ, bao gồm khởi tạo presigned URL cho phép ứng dụng khách tải tệp video trực tiếp lên Amazon S3 Raw Upload Bucket.
- Thiết kế bảng Amazon DynamoDB để lưu trữ metadata của phim và theo dõi trạng thái xử lý bất đồng bộ.
- Xây dựng pipeline xử lý video hướng sự kiện kết hợp Amazon S3, Amazon EventBridge, hàng đợi Amazon SQS (kèm Dead-Letter Queue), Amazon EventBridge Pipes và luồng điều phối AWS Step Functions.
- Tích hợp dịch vụ AWS Elemental MediaConvert để chuyển mã video tự động sang chuẩn phát trực tuyến HLS đa phân giải kèm hình ảnh thumbnail.
- Cấu hình lưu trữ kết quả tại Amazon S3 Processed Media Bucket và phân phối luồng phát lại HLS với độ trễ thấp thông qua mạng Amazon CloudFront CDN kết hợp tường lửa AWS WAF và Origin Access Control (OAC).
- Cấu hình lớp bảo lưu giao diện ứng dụng Web tĩnh tại Amazon S3 Frontend Bucket riêng tư.
- Thiết lập hệ thống giám sát tập trung với Amazon CloudWatch để thu thập log, metric và cảnh báo sự cố.


## Kiến trúc triển khai

Kiến trúc triển khai của hệ thống Serverless Video-on-Demand Platform on AWS được tổ chức thành ba phân vùng chức năng chính:

- **Frontend:** Giao diện ứng dụng Web được lưu trữ trong S3 Frontend Bucket riêng tư và phân phối qua Amazon CloudFront CDN kết hợp tường lửa AWS WAF. Người dùng đăng nhập qua Amazon Cognito để nhận JWT trước khi thực hiện các yêu cầu hệ thống.
- **Backend:** Gồm Amazon API Gateway tiếp nhận request API, kiểm tra JWT Authorizer và định tuyến đến AWS Lambda. Backend không nhận trực tiếp tệp video mà chỉ khởi tạo presigned URL để trình duyệt upload tệp thẳng vào Amazon S3 Raw Upload Bucket, đồng thời ghi nhận metadata ban đầu vào Amazon DynamoDB.
- **Video Processing Pipeline:** Luồng xử lý phương tiện bất đồng bộ hoạt động hoàn toàn độc lập với request upload của người dùng. Tệp video mới tải lên S3 Raw Bucket phát sinh sự kiện Object Created, được lọc bởi Amazon EventBridge, đưa vào hàng đợi Amazon SQS, sau đó Amazon EventBridge Pipes kích hoạt luồng điều phối AWS Step Functions để gọi AWS Elemental MediaConvert chuyển mã video sang định dạng HLS và xuất kết quả ra Amazon S3 Processed Media Bucket.


## Các dịch vụ AWS sử dụng

Dưới đây là bảng tổng hợp danh sách các dịch vụ AWS được tích hợp trong hệ thống và vai trò cụ thể của từng dịch vụ:

| Dịch vụ | Vai trò |
| --- | --- |
| Amazon S3 | Lưu trữ tệp tĩnh giao diện, video nguồn và nội dung video HLS đã xử lý |
| Amazon CloudFront | Phân phối giao diện ứng dụng Web và luồng phát video HLS |
| AWS WAF | Lọc và kiểm soát các truy cập ứng dụng bảo vệ CloudFront |
| Amazon Cognito | Quản lý định danh, xác thực người dùng và cấp phát JWT |
| Amazon API Gateway | Tiếp nhận, bảo mật và cung cấp API nghiệp vụ cho ứng dụng Web |
| AWS Lambda | Thực thi logic nghiệp vụ backend ngắn hạn và tích hợp dịch vụ |
| Amazon DynamoDB | Lưu trữ dữ liệu metadata phim và theo dõi trạng thái xử lý video |
| Amazon EventBridge | Lọc và định tuyến sự kiện Object Created từ Amazon S3 |
| Amazon SQS | Làm hàng đợi đệm thông điệp và hỗ trợ xử lý sự kiện bất đồng bộ |
| EventBridge Pipes | Kết nối thông điệp từ Amazon SQS với AWS Step Functions |
| AWS Step Functions | Điều phối workflow các bước xử lý và cập nhật trạng thái video |
| AWS Elemental MediaConvert | Thực hiện nén và chuyển mã tệp video nguồn sang định dạng HLS |
| Amazon CloudWatch | Thu thập nhật ký vận hành, chỉ số hiệu năng và thiết lập cảnh báo |


## Quy trình hoạt động của hệ thống

Sau khi các tài nguyên và quyền truy cập được cấu hình, quy trình xử lý được kích hoạt tự động khi video hợp lệ được tải lên S3 Raw Upload Bucket theo thứ tự các bước sau:

1. Người dùng đăng ký, đăng nhập và xác thực thông tin thông qua Amazon Cognito để nhận mã JWT.
2. Ứng dụng Web gửi yêu cầu API kèm mã JWT đến Amazon API Gateway; yêu cầu được kiểm tra tính hợp lệ bởi Cognito JWT Authorizer.
3. Amazon API Gateway chuyển yêu cầu đến AWS Lambda để thực thi logic khởi tạo presigned URL của Amazon S3.
4. AWS Lambda ghi nhận thông tin metadata ban đầu của video với trạng thái `UPLOADED` vào bảng Amazon DynamoDB.
5. Trình duyệt ứng dụng Web sử dụng presigned URL để tải tệp video nguồn trực tiếp vào Amazon S3 Raw Upload Bucket.
6. Tệp tin mới được tải lên kích hoạt sự kiện `Object Created` từ S3 gửi tới Amazon EventBridge.
7. Amazon EventBridge Rule lọc sự kiện theo cấu hình và định tuyến thông điệp vào hàng đợi Amazon SQS.
8. Amazon EventBridge Pipes đọc thông điệp từ SQS, biến đổi cấu trúc dữ liệu và khởi chạy luồng điều phối trên AWS Step Functions.
9. AWS Step Functions điều phối quy trình làm việc, cập nhật trạng thái `PROCESSING` và gọi dịch vụ AWS Elemental MediaConvert.
10. AWS Elemental MediaConvert thực hiện nén và chuyển mã video gốc thành các tệp HLS (master playlist, variant playlists, segment) và ảnh thumbnail.
11. Kết quả chuyển mã HLS được ghi trực tiếp vào Amazon S3 Processed Media Bucket.
12. Sau khi tác vụ chuyển mã hoàn thành, trạng thái video được cập nhật thành `READY` và lưu đường dẫn HLS vào Amazon DynamoDB.
13. Người dùng truy cập và xem luồng phát trực tuyến HLS mượt mà thông qua Amazon CloudFront CDN.
14. Amazon CloudWatch liên tục thu thập log, metric và phát tín hiệu cảnh báo nếu xuất hiện lỗi phát sinh.


## Nội dung của Workshop

Nội dung triển khai thực hành của Workshop được tổ chức thành 6 phần kế tiếp:

1. **5.2. Điều kiện tiên quyết (Prerequisites):** Chuẩn bị tài khoản AWS, IAM Role, CLI và các tài nguyên môi trường ban đầu.
2. **5.3. Xây dựng Backend (Build Backend):** Cấu hình Cognito, API Gateway, Lambda và DynamoDB; kiểm thử API tạo presigned URL và thao tác upload trực tiếp lên S3.
3. **5.4. Xây dựng Video Processing Pipeline (Build Video Processing Pipeline):** Cấu hình EventBridge, SQS, EventBridge Pipes, Step Functions và MediaConvert.
4. **5.5. Kiểm thử hệ thống (System Testing):** Thực hiện kiểm thử end-to-end từ tải lên, chuyển mã đến cập nhật trạng thái.
5. **5.6. Xây dựng ứng dụng Web (Build Web Application):** Tích hợp giao diện Frontend với Backend API và HLS Video Player.
6. **5.7. Kết luận (Conclusion):** Đánh giá tổng kết kết quả triển khai và các bài học kinh nghiệm.


## Kết quả mong đợi

Khi các bước cấu hình hoàn tất trong phạm vi workshop, người đọc được kỳ vọng có thể kiểm thử và xác minh các kết quả sau:

- API Gateway và Lambda trả về response presigned URL dự kiến cho yêu cầu hợp lệ.
- Metadata ban đầu của tệp tin được ghi nhận chính xác vào bảng DynamoDB.
- Video được tải lên trực tiếp từ trình duyệt vào S3 Raw Upload Bucket bằng presigned URL.
- Sự kiện tải lên được đưa thành công vào hàng đợi SQS và EventBridge Pipes khởi chạy Step Functions execution.
- MediaConvert job được khởi tạo và tạo đúng bộ đầu ra HLS kèm thumbnail tại S3 Processed Media Bucket.
- Trạng thái xử lý video trong DynamoDB được cập nhật chính xác sang `READY`.
- Nội dung video HLS có thể phát mượt mà thông qua phân phối Amazon CloudFront CDN.
- Nhật ký vận hành của toàn bộ các dịch vụ được ghi nhận đầy đủ trong Amazon CloudWatch.


## Quy ước trong Workshop

Các bước chính được thực hiện trên AWS Management Console; mã nguồn và lệnh hỗ trợ được sử dụng tại những phần cần thiết. Giao diện AWS Management Console và một số tùy chọn có thể thay đổi; người đọc cần đối chiếu với tài liệu AWS hiện hành khi thực hiện.


## Hình ảnh minh họa

Các bước cấu hình quan trọng được minh họa bằng ảnh chụp trong quá trình triển khai khi có sẵn nhằm giúp người đọc dễ dàng đối chiếu và thực hiện.


## Cấu trúc các phần tiếp theo

Các phần từ 5.2 đến 5.7 được thiết kế theo trình tự nâng cấp từng bước: bắt đầu từ việc chuẩn bị môi trường tài nguyên ở phần 5.2, xây dựng luồng API backend và database ở phần 5.3, thiết lập pipeline xử lý sự kiện bất đồng bộ ở phần 5.4, kiểm thử tích hợp các chức năng ở phần 5.5, kết nối giao diện ứng dụng Web ở phần 5.6 và tổng kết dự án ở phần 5.7.


## Tổng kết

Phần 5.1 đã trình bày tổng quan về phạm vi, mục tiêu, kiến trúc, danh sách dịch vụ và quy trình hoạt động của hệ thống Serverless Video-on-Demand Platform on AWS. Các nội dung này thiết lập nền tảng định hướng trước khi bước vào các thao tác cấu hình chi tiết. Phần 5.2 tiếp theo sẽ hướng dẫn chuẩn bị các điều kiện tiên quyết và tài nguyên ban đầu để bắt đầu triển khai hệ thống.
