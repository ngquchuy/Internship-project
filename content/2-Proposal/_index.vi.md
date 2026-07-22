---
title: "Bản đề xuất"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

# Bản đề xuất

Nhu cầu lưu trữ, xử lý và phát trực tuyến video dạng Video-on-Demand (VoD) đang tăng trưởng nhanh chóng trong nhiều ứng dụng hiện đại. Tuy nhiên, việc xây dựng và duy trì hạ tầng xử lý truyền thông truyền thống dựa trên máy chủ cố định thường đối mặt với thách thức lớn về chi phí đầu tư ban đầu, khả năng mở rộng không linh hoạt và tài nguyên máy chủ thường xuyên rơi vào trạng thái nhàn rỗi ngoài giờ cao điểm. Trong khi đó, tác vụ chuyển mã video (transcoding) lại có đặc thù tiêu tốn tài nguyên tính toán rất lớn trong một khoảng thời gian ngắn ngay khi tệp tin mới được tải lên.

Để giải quyết sự không cân bằng giữa tần suất sử dụng và nhu cầu tài nguyên tức thời, đề xuất này chọn hướng tiếp cận dựa trên mô hình serverless và kiến trúc dựa trên sự kiện (event-driven architecture) trên nền tảng điện toán đám mây Amazon Web Services (AWS). Đề án nhằm mục tiêu thiết kế và triển khai một hệ thống Serverless Video-on-Demand Platform on AWS hoàn chỉnh, phân tách rõ ràng giữa các tác vụ tương tác trực tiếp với người dùng và các quy trình xử lý phương tiện ngầm bối cảnh. Hệ thống hướng đến việc cung cấp luồng tải lên an toàn, tự động hóa toàn bộ quá trình chuyển mã sang định dạng HTTP Live Streaming (HLS), tối ưu hóa trải nghiệm phát lại video và thiết lập cơ chế giám sát tập trung.


## Bài toán đặt ra

Trong khuôn khổ hệ thống Video-on-Demand, việc tiếp nhận, xử lý và phân phối tệp tin truyền thông đòi hỏi phải giải quyết đồng bộ các vấn đề kỹ thuật sau:

- **Tải lên và lưu trữ tệp video dung lượng lớn:** Tệp video gốc thường có dung lượng lớn và chiếm nhiều băng thông. Việc truyền dữ liệu thông qua các máy chủ backend thông thường dễ gây nghẽn mạng, tiêu tốn bộ nhớ tạm và tăng nguy cơ thất bại khi kết nối gián đoạn.
- **Tác vụ chuyển mã tiêu tốn tài nguyên tính toán:** Tệp tin video đầu vào cần được chuyển đổi sang định dạng HLS kèm theo nhiều mức độ phân giải và tốc độ bit khác nhau nhằm tương thích với đa dạng thiết bị người dùng. Quá trình này đòi hỏi năng lực xử lý cao nhưng chỉ diễn ra theo từng đợt bất định.
- **Phân phối nội dung đến số lượng lớn người dùng:** Việc phát trực tiếp các phân đoạn video từ lưu trữ gốc có thể sinh ra độ trễ cao và chi phí băng thông lớn nếu không có giải pháp mạng phân phối nội dung ở lớp biên.
- **Quản lý trạng thái xử lý bất đồng bộ:** Tác vụ chuyển mã kéo dài cần có cơ chế theo dõi trạng thái chính xác (như `UPLOADED`, `PROCESSING`, `READY`, `FAILED`) để phản hồi cho giao diện người dùng mà không bắt ứng dụng khách phải chờ đợi theo cơ chế đồng bộ.
- **Bảo đảm tính sẵn sàng, khả năng quan sát và kiểm soát chi phí:** Hệ thống cần có cơ chế chịu lỗi, xử lý thông điệp sự cố và theo dõi nhật ký vận hành tập trung mà không làm gia tăng chi phí vận hành máy chủ cố định.


## Giải pháp đề xuất

Đề xuất xây dựng giải pháp tổng thể Serverless Video-on-Demand Platform on AWS bằng cách kết hợp các dịch vụ được quản lý chuyên biệt của AWS theo một luồng xử lý khép kín:

1. **Xác thực người dùng:** Người dùng thực hiện đăng nhập thông qua Amazon Cognito User Pool để nhận mã xác thực JWT Token hợp lệ.
2. **Gọi API nghiệp vụ:** Người dùng gửi yêu cầu đến Amazon API Gateway; yêu cầu được xác thực tự động bởi Cognito JWT Authorizer trước khi chuyển cho AWS Lambda xử lý.
3. **Tạo presigned URL:** Hàm AWS Lambda khởi tạo một presigned URL của Amazon S3 và trả về cho ứng dụng khách.
4. **Tải lên trực tiếp:** Trình duyệt người dùng sử dụng presigned URL để tải trực tiếp tệp video gốc vào Amazon S3 Raw Upload Bucket mà không đi qua máy chủ ứng dụng.
5. **Phát sinh và định tuyến sự kiện:** Tệp video mới tải lên S3 kích hoạt sự kiện `Object Created`. Sự kiện này được Amazon EventBridge tiếp nhận và lọc theo đúng pattern quy định.
6. **Đưa thông điệp vào hàng đợi:** EventBridge chuyển sự kiện đến hàng đợi Amazon SQS nhằm làm đệm lưu trữ thông điệp và cách ly tải bất đồng bộ.
7. **Khởi chạy luồng điều phối:** Amazon EventBridge Pipes đọc thông điệp từ SQS, thực hiện biến đổi dữ liệu đầu vào và kích hoạt quy trình làm việc trên AWS Step Functions.
8. **Thực hiện chuyển mã:** AWS Step Functions điều phối quy trình và gọi dịch vụ AWS Elemental MediaConvert để thực hiện chuyển mã video gốc thành bộ tệp HLS (bao gồm master playlist, variant playlists và các phân đoạn segment) cùng hình ảnh thumbnail.
9. **Lưu trữ kết quả chuyển mã:** Bộ tệp HLS hoàn thành được ghi trực tiếp vào Amazon S3 Processed Media Bucket.
10. **Cập nhật dữ liệu và trạng thái:** AWS Step Functions cập nhật trạng thái tệp tin và thông tin đường dẫn phát lại HLS vào bảng Amazon DynamoDB.
11. **Phân phối nội dung tốc độ cao:** Người dùng truy cập và phát video HLS thông qua mạng phân phối nội dung Amazon CloudFront được bảo vệ bởi AWS WAF và cơ chế Origin Access Control (OAC).
12. **Giám sát tập trung:** Toàn bộ nhật ký, chỉ số vận hành và cảnh báo sự cố từ API Gateway, Lambda, SQS, Step Functions, MediaConvert được thu thập tập trung về Amazon CloudWatch.


## Kiến trúc đề xuất

Kiến trúc hệ thống được thiết kế theo mô hình phân lớp rõ ràng nhằm giảm thiểu sự phụ thuộc lẫn nhau giữa các thành phần (decoupling), cho phép từng dịch vụ tự động mở rộng quy mô độc lập theo nhu cầu thực tế. Việc phân tách triệt để giữa luồng xử lý đồng bộ (xác thực, gọi API, sinh presigned URL) và luồng xử lý bất đồng bộ (tiếp nhận sự kiện, hàng đợi thông điệp, điều phối trạng thái và chuyển mã) góp phần nâng cao tính sẵn sàng của toàn hệ thống, tạo điều kiện thuận lợi cho công tác kiểm thử, cô lập sự cố và giám sát vận hành.

![Kiến trúc đề xuất hệ thống Serverless Video-on-Demand Platform on AWS](/images/2-Proposal/VOD.drawio.png)  
*Hình 2.1. Kiến trúc đề xuất của hệ thống Serverless Video-on-Demand Platform on AWS.*


## Mô tả kiến trúc đề xuất

Hệ thống Serverless Video-on-Demand Platform on AWS được tổ chức thành 7 lớp chức năng chính:

- **Lớp định danh và truy cập (Identity & Access Layer):** Sử dụng Amazon Cognito để quản lý thông tin người dùng, cung cấp luồng đăng ký, đăng nhập và phát hành JWT Token nhằm bảo mật các truy cập vào tài nguyên hệ thống.
- **Lớp biên và phân phối nội dung (Edge & Content Delivery Layer):** Gồm Amazon CloudFront kết hợp với AWS WAF và Amazon S3 Frontend Bucket. Giao diện Web được lưu trữ an toàn trong một S3 bucket riêng tư. CloudFront đóng vai trò phân phối các tệp tĩnh của giao diện và luồng video HLS đến người dùng với độ trễ thấp, đồng thời áp dụng Origin Access Control (OAC) để ngăn chặn truy cập trực tiếp từ Internet vào S3 origin. Tường lửa AWS WAF được gắn tại CloudFront để lọc các truy cập bất thường và chống tấn công lớp ứng dụng.
- **Lớp ứng dụng (Application Layer):** Bao gồm Amazon API Gateway và các hàm AWS Lambda. API Gateway tiếp nhận các yêu cầu HTTP/REST từ người dùng, sử dụng JWT Authorizer để kiểm tra quyền hạn và định tuyến đến Lambda. AWS Lambda thực thi các logic nghiệp vụ ngắn hạn như sinh presigned URL tải lên S3 và truy vấn danh mục phim.
- **Lớp dữ liệu (Data Layer):** Gồm Amazon DynamoDB, Amazon S3 Raw Upload Bucket và Amazon S3 Processed Media Bucket. DynamoDB lưu trữ metadata của phim, thông tin người dùng và trạng thái xử lý video. S3 Raw Upload Bucket chứa các video gốc do người dùng tải lên. S3 Processed Media Bucket lưu trữ kết quả đầu ra gồm các tệp HLS và thumbnail.
- **Lớp xử lý sự kiện và điều phối (Event Processing Layer):** Bao gồm Amazon EventBridge, Amazon SQS (kèm SQS Dead-Letter Queue), Amazon EventBridge Pipes và AWS Step Functions. Khi có video mới tại S3 Raw Bucket, EventBridge tiếp nhận sự kiện và gửi đến SQS để xếp hàng chờ. SQS đóng vai trò vùng đệm chịu tải và chuyển các tin nhắn không xử lý được sang Dead-Letter Queue (DLQ). EventBridge Pipes đọc thông điệp từ SQS để khởi chạy AWS Step Functions State Machine - thành phần chịu trách nhiệm điều phối chi tiết các bước xử lý và cập nhật trạng thái video.
- **Lớp xử lý truyền thông (Media Processing Layer):** Sử dụng AWS Elemental MediaConvert làm dịch vụ chuyển mã chuyên dụng. MediaConvert nhận tệp video nguồn từ S3 Raw Bucket theo lệnh từ Step Functions, tiến hành nén và phân tách thành các tệp HLS playlist (.m3u8), video segment (.ts) và ảnh đại diện (.jpg), sau đó xuất dữ liệu sang S3 Processed Bucket.
- **Lớp giám sát (Monitoring Layer):** Sử dụng Amazon CloudWatch làm trung tâm thu thập nhật ký (Logs), chỉ số hiệu năng (Metrics) và thiết lập cảnh báo (Alarms) cho toàn bộ các dịch vụ API Gateway, Lambda, SQS, Step Functions và MediaConvert.


## Kế hoạch triển khai

Quy trình phát triển hệ thống Serverless Video-on-Demand Platform on AWS được chia thành các giai đoạn tuần tự:

Giai đoạn đầu tập trung nghiên cứu chi tiết yêu cầu bài toán, thống nhất kiến trúc phân lớp và lựa chọn bộ dịch vụ AWS phù hợp. Tiếp theo, nhóm tiến hành xây dựng giao diện ứng dụng Web tĩnh, tích hợp xác thực người dùng bằng Amazon Cognito và thiết lập các API nghiệp vụ trên Amazon API Gateway kết hợp với AWS Lambda.

Giai đoạn kế tiếp thực hiện thiết kế cấu trúc dữ liệu metadata trên Amazon DynamoDB và phát triển tính năng sinh presigned URL cho phép ứng dụng khách tải tệp video trực tiếp lên Amazon S3 Raw Upload Bucket. Sau khi luồng tải lên hoàn tất, nhóm tập trung xây dựng luồng xử lý sự kiện bất đồng bộ bao gồm việc cấu hình Amazon EventBridge, hàng đợi Amazon SQS, Dead-Letter Queue và Amazon EventBridge Pipes.

Ở giai đoạn xử lý truyền thông, nhóm thiết kế quy trình điều phối trên AWS Step Functions và cấu hình các Job Template chuyển mã trên AWS Elemental MediaConvert để tạo định dạng HLS đa phân giải kèm thumbnail. Kết quả chuyển mã được lưu trữ tại Amazon S3 Processed Media Bucket và được cấu hình phân phối qua Amazon CloudFront CDN kết hợp cơ chế bảo vệ Origin Access Control (OAC) và tường lửa AWS WAF.

Giai đoạn cuối cùng dành cho việc cấu hình hệ thống giám sát Amazon CloudWatch, thực hiện kiểm thử tích hợp toàn diện (end-to-end testing), đánh giá các chỉ số hiệu năng cùng chi phí vận hành thực tế, từ đó hoàn thiện bộ hồ sơ tài liệu báo cáo và chuẩn bị kịch bản nghiệm thu dự án.


## Chi phí dự kiến

Chi phí hạ tầng

AWS Elemental MediaConvert: 22,50 USD/tháng (10 video, mỗi video 60 phút, đầu ra HLS 1080p, 720p và 480p).

Amazon S3 Standard: 1,60 USD/tháng (63 GB lưu trữ video gốc, nội dung HLS, thumbnail và frontend).

Amazon CloudFront và AWS WAF: 0,00 USD/tháng (dưới 100 GB dữ liệu truyền tải và dưới 1 triệu request).

Amazon Cognito: 0,00 USD/tháng (100 người dùng hoạt động).

Amazon API Gateway: 0,05 USD/tháng (50.000 request).

AWS Lambda: 0,00 USD/tháng (100.000 request, bộ nhớ 512 MB).

Amazon DynamoDB: 0,05 USD/tháng (50.000 lượt đọc và 10.000 lượt ghi metadata).

Amazon EventBridge: 0,00 USD/tháng (1.000 sự kiện).

Amazon SQS và Dead-Letter Queue: 0,00 USD/tháng (dưới 1 triệu request).

Amazon EventBridge Pipes: 0,00 USD/tháng (1.000 thông điệp).

AWS Step Functions: 0,00 USD/tháng (10 workflow và dưới 4.000 state transition).

Amazon CloudWatch: 0,50 USD/tháng (1 GB log, dashboard và alarm cơ bản).

Tổng: 24,70 USD/tháng, 296,40 USD/12 tháng.


## Kết quả mong đợi

Dựa trên thiết kế kiến trúc đề xuất, hệ thống Serverless Video-on-Demand Platform on AWS được kỳ vọng đạt được các kết quả kỹ thuật sau:

- Cung cấp cơ chế xác thực và phân quyền người dùng an toàn thông qua Cognito và JWT Authorizer.
- Hỗ trợ tải tệp video dung lượng lớn trực tiếp từ ứng dụng khách lên S3 Raw Bucket bằng presigned URL, giảm tải cho máy chủ ứng dụng.
- Tự động hóa hoàn toàn luồng chuyển mã video nguồn sang chuẩn phát trực tuyến HLS đa phân giải kèm theo ảnh đại diện thumbnail.
- Cho phép người dùng theo dõi trạng thái xử lý video bất đồng bộ theo thời gian thực dựa trên dữ liệu cập nhật tại DynamoDB.
- Phân phối luồng video HLS với độ trễ thấp và trải nghiệm mượt mà tới trình duyệt người dùng nhờ hạ tầng CloudFront CDN.
- Ghi nhận đầy đủ nhật ký vận hành và hỗ trợ phát hiện sớm các bất thường hệ thống thông qua CloudWatch.
- Khả năng tự động mở rộng quy mô linh hoạt theo tải lượng người dùng mà không cần can thiệp quản trị thủ công.


## Kết luận

Bản đề xuất đã trình bày tổng quan giải pháp xây dựng hệ thống Serverless Video-on-Demand Platform on AWS nhằm giải quyết triệt để các thách thức về chi phí hạ tầng, khả năng mở rộng và hiệu năng xử lý truyền thông của mô hình máy chủ truyền thống. Bằng cách kết hợp linh hoạt các dịch vụ serverless được quản lý của AWS, kiến trúc đề xuất giúp phân tách hiệu quả giữa luồng xử lý tương tác đồng bộ và luồng chuyển mã bất đồng bộ, tạo nền tảng vững chắc cho quá trình phát triển hệ thống. Bản đề xuất này đóng vai trò là kim chỉ nam kỹ thuật quan trọng, định hướng cho các bước triển khai chi tiết, kiểm thử và đánh giá hiệu quả của dự án trong các giai đoạn tiếp theo.