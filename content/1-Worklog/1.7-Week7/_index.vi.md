---
title: "Worklog Tuần 7"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


### Mục tiêu tuần 7:

* Nghiên cứu bài toán hệ thống Video-on-Demand (VOD) và xác định đầy đủ các yêu cầu nghiệp vụ, actor và use case cốt lõi.
* Phân tích các yêu cầu phi chức năng bao gồm khả năng mở rộng, tính sẵn sàng, hiệu năng, bảo mật và tối ưu chi phí vận hành.
* Phân tích và phân chia trách nhiệm của từng lớp dịch vụ trong mô hình Serverless Architecture.
* Thiết kế sequence flow chi tiết cho các luồng nghiệp vụ: Đăng nhập, Upload video, Transcoding HLS và Phát lại (Playback).
* Rà soát kiến trúc tổng quan, lập tài liệu Architecture Decision Record (ADR) và xây dựng backlog triển khai cho tuần 8–12.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                                                                                                                                           | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | -------------- |
| 3   | - Phân tích bài toán website xem phim Video-on-Demand <br> - Xác định các actor (User, Admin) và sơ đồ use case chính <br> - Xác định phạm vi các chức năng MVP: Đăng nhập, danh mục phim, upload video, xử lý video tự động và phát lại HLS <br>                                                                                   | 02/06/2026   | 02/06/2026      |                |
| 4   | - Phân tích yêu cầu phi chức năng cho hệ thống xem phim <br> - Xác định chỉ số khả năng mở rộng (Scalability), độ tin cậy (Availability), hiệu năng phát video (Latency/Throughput), bảo mật dữ liệu và observability <br> - Tính toán sơ bộ ngân sách vận hành tối ưu với AWS Serverless <br>                                      | 03/06/2026   | 03/06/2026      |                |
| 5   | - Phân tích trách nhiệm từng lớp dịch vụ (Service Responsibility) trong kiến trúc <br> - Phân định rõ vai trò của Cognito (Identity), CloudFront (Edge), API Gateway & Lambda (Application), DynamoDB & S3 (Data), EventBridge/SQS/Step Functions (Event & Pipeline), MediaConvert (Transcoding) và CloudWatch (Observability) <br> | 04/06/2026   | 04/06/2026      |                |
| 6   | - Thiết kế Sequence Flow chi tiết cho 4 luồng chính: Đăng nhập/gọi API, Upload video trực tiếp, Transcoding đa phân giải và Playback HLS <br> - Phân tích ranh giới tin cậy (Trust Boundary) và luồng dữ liệu đi qua từng dịch vụ <br>                                                                                              | 05/06/2026   | 05/06/2026      |                |
| 2   | - Rà soát kiến trúc tổng quan hệ thống Video-on-Demand <br> - Đánh giá ưu nhược điểm của mô hình Serverless và xác định các điểm lỗi tiềm ẩn (Single Points of Failure) <br> - Lập báo cáo Architecture Decision Record (ADR) và phân bổ backlog triển khai chi tiết cho tuần 8-12 <br>                                             | 08/06/2026   | 08/06/2026      |                |


### Kết quả đạt được tuần 7:

* Đã xác định rõ ràng các actor, use case và phạm vi tính năng MVP cho website Video-on-Demand.
* Xây dựng bộ tiêu chí phi chức năng hoàn chỉnh về hiệu năng, độ tin cậy và tối ưu chi phí cho mô hình Serverless.
* Hoàn thành phân định trách nhiệm dịch vụ (Service Responsibility Table) giữa Cognito, API Gateway, Lambda, S3, MediaConvert và CloudFront.
* Thiết kế chi tiết sơ đồ luồng dữ liệu (Data Flow) và sơ đồ trình tự (Sequence Diagram) cho các luồng nghiệp vụ cốt lõi.
* Lập xong báo cáo Architecture Decision Record (ADR) chốt kiến trúc Serverless VOD và phân chia backlog thực hiện cho 5 tuần tiếp theo.
