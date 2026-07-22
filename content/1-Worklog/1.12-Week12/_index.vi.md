---
title: "Worklog Tuần 12"
date: 2024-01-01
weight: 12
chapter: false
pre: " <b> 1.12 </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

### Mục tiêu tuần 12:

* Xây dựng hệ thống giám sát Observability tập trung trên Amazon CloudWatch (Structured Logs, Metrics, Dashboards, Alarms).
* Thực hiện kiểm thử chức năng toàn diện (Functional Testing) cho toàn bộ các luồng nghiệp vụ trên hệ thống.
* Thực hiện kiểm thử khả năng chịu lỗi và phục hồi hệ thống (Failure & Resiliency Testing) với các kịch bản sự cố.
* Đánh giá hiệu năng và chi phí vận hành (Performance & Cost Evaluation), lập phương án tối ưu tài nguyên AWS.
* Hoàn thiện bộ hồ sơ tài liệu báo cáo thực tập tốt nghiệp, phiếu đánh giá tiến độ và dọn dẹp các tài nguyên thử nghiệm.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | -------------- |
| 3   | - Xây dựng hệ thống giám sát và quản lý nhật ký tập trung với Amazon CloudWatch <br> - Cấu hình Structured Logging cho các hàm Lambda, thu thập Log Group và thiết lập thời gian lưu trữ (Retention) <br> - Thiết lập CloudWatch Dashboard và Alarm cảnh báo ngưỡng sự cố cho API Gateway, Lambda, SQS, Step Functions và MediaConvert <br> | 07/07/2026   | 07/07/2026      |                |
| 4   | - Tiến hành kiểm thử chức năng toàn diện (End-to-End Functional Testing) trên môi trường thực tế <br> - Kiểm tra luồng Xác thực tài khoản, Gọi API nghiệp vụ, Tải video trực tiếp, Xử lý chuyển mã và Trình chiếu video <br> - Ghi nhận danh sách các lỗi giao diện, lỗi logic backend và tiến hành sửa lỗi (Bug fixing) <br>               | 08/07/2026   | 08/07/2026      |                |
| 5   | - Thực hiện kiểm thử khả năng phục hồi và xử lý ngoại lệ (Failure & Resiliency Testing) <br> - Mô phỏng kịch bản token hết hạn, tải file định dạng không hỗ trợ, ngắt kết nối mạng và duplicate event <br> - Kiểm tra cơ chế tự động thử lại (Retry) của Step Functions và chuyển thông điệp lỗi sang SQS DLQ <br>                          | 09/07/2026   | 09/07/2026      |                |
| 6   | - Đo lường và đánh giá chỉ số hiệu năng cùng chi phí vận hành (Performance & Cost Evaluation) <br> - Thống kê thời gian tải lên, thời gian chuyển mã MediaConvert, thời gian bắt đầu phát video và tỷ lệ Cache Hit <br> - Phân tích chi phí phát sinh thực tế trên AWS Billing và đề xuất các giải pháp tối ưu hóa <br>                     | 10/07/2026   | 10/07/2026      |                |
| 2   | - Hoàn thiện toàn bộ hồ sơ báo cáo thực tập tốt nghiệp<br> -Vẽ hoàn chỉnh sơ đồ kiến trúc, tài liệu API Contract và kịch bản Demo <br> - Hoàn thành Phiếu theo dõi tiến độ TTTN, phiếu tự đánh giá và dọn dẹp các tài nguyên thử nghiệm thừa <br>                                                                                           | 13/07/2026   | 13/07/2026      |                |


### Kết quả đạt được tuần 12:

* Thiết lập hệ thống giám sát tập trung CloudWatch với Dashboard trực quan và cơ chế cảnh báo sự cố tự động.
* Đã kiểm thử và xác nhận 100% các chức năng hệ thống VOD hoạt động chính xác theo yêu cầu thiết kế.
* Xác minh khả năng chịu lỗi và xử lý sự cố an toàn thông qua cơ chế Retry của Step Functions và SQS DLQ.
* Đánh giá chi tiết chỉ số hiệu năng phát video HLS và tối ưu hóa ngân sách vận hành hệ thống Serverless.
* Đóng gói toàn bộ tài liệu báo cáo thực tập tốt nghiệp, kịch bản demo và hoàn thành phiếu tiến độ thực tập.
