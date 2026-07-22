---
title: "Worklog Tuần 10"
date: 2024-01-01
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


### Mục tiêu tuần 10:

* Cấu hình Amazon S3 Event Notifications đẩy sự kiện Object Created sang Amazon EventBridge.
* Triển khai Amazon SQS Queue và Dead-Letter Queue (DLQ) làm vùng đệm lưu trữ thông điệp xử lý video an toàn.
* Cấu hình Amazon EventBridge Pipes để đọc thông điệp từ SQS và kích hoạt luồng xử lý.
* Xây dựng luồng điều phối trạng thái tự động bằng AWS Step Functions State Machine.
* Tích hợp toàn bộ pipeline tự động hóa từ S3 Upload đến chuyển mã MediaConvert và lưu dữ liệu HLS.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | -------------- |
| 3 | - Cấu hình tính năng EventBridge Notification trên S3 Raw Upload Bucket <br> - Phân tích cấu hình định dạng cấu trúc tệp sự kiện payload khi có file video mới tải lên <br> - Xây dựng Event Pattern trên EventBridge Bus để lọc chính xác sự kiện theo Bucket name và đuôi file video <br> | 23/06/2026 | 23/06/2026 | |
| 4 | - Khởi tạo hàng đợi Amazon SQS làm vùng đệm (Buffer Queue) cho pipeline xử lý video <br> - Cấu hình thông số Visibility Timeout, Message Retention Period, Long Polling và Retry Policy <br> - Thiết lập hàng đợi sự cố Dead-Letter Queue (DLQ) cùng Redrive Policy để hứng các thông điệp lỗi <br> | 24/06/2026 | 24/06/2026 | |
| 5 | - Cấu hình Amazon EventBridge Pipes làm cầu nối tích hợp dịch vụ không dùng code <br> - Cấu hình SQS Queue làm Source và AWS Step Functions State Machine làm Target <br> - Thiết lập các tiêu chí Filter và biến đổi cấu trúc định dạng Input Transformation cho thông điệp <br> | 25/06/2026 | 25/06/2026 | |
| 6 | - Thiết kế và xây dựng quy trình làm việc tự động với AWS Step Functions (State Machine) <br> - Định nghĩa các bước ASL: Kiểm tra dữ liệu đầu vào -> Cập nhật trạng thái DynamoDB (PROCESSING) -> Khởi chạy MediaConvert Job -> Kiểm tra trạng thái hoàn tất -> Cập nhật (READY/FAILED) <br> - Triển khai cơ chế Retry, Catch exception và xử lý sự cố idempotent <br> | 26/06/2026 | 26/06/2026 | |
| 2 | - Kết nối tích hợp toàn bộ luồng Pipeline xử lý video tự động End-to-End <br> - Thực hiện Upload file video MP4 -> S3 kích hoạt EventBridge -> SQS nhận message -> EventBridge Pipe gọi Step Functions -> MediaConvert tạo HLS -> Ghi dữ liệu vào S3 Processed -> Cập nhật DynamoDB <br> - Thử nghiệm tải file hỏng để kiểm tra cơ chế đẩy message lỗi vào SQS DLQ <br> | 29/06/2026 | 29/06/2026 | |


### Kết quả đạt được tuần 10:

* Thiết lập thành công cơ chế đẩy sự kiện tự động từ Amazon S3 sang Amazon EventBridge.
* Xây dựng hệ thống hàng đợi Amazon SQS kết hợp Dead-Letter Queue (DLQ) đảm bảo không mất mát thông điệp.
* Cấu hình Amazon EventBridge Pipes kết nối tin cậy giữa hàng đợi SQS và luồng điều phối Step Functions.
* Xây dựng sơ đồ quy trình tự động trên AWS Step Functions kiểm soát toàn bộ vòng đời chuyển mã video.
* Hoàn thành tích hợp Pipeline xử lý video tự động từ khâu tải lên S3 Raw đến chuyển mã HLS và cập nhật cơ sở dữ liệu.
