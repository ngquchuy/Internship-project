---
title: "Worklog Tuần 11"
date: 2024-01-01
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


### Mục tiêu tuần 11:

* Chuẩn hóa cấu trúc thư mục lưu trữ HLS output và cấu hình Metadata/Content-Type trên S3 Processed Media Bucket.
* Cấu hình mạng phân phối nội dung Amazon CloudFront kết hợp Origin Access Control (OAC) bảo vệ dữ liệu S3.
* Nghiên cứu cơ chế bảo vệ bản quyền nội dung video HLS với CloudFront Signed URLs / Signed Cookies.
* Triển khai tường lửa ứng dụng web AWS WAF thiết lập các quy tắc Rate-based và Managed Rules bảo vệ CloudFront.
* Tích hợp giao diện Frontend với Cognito, API Gateway, Lambda, DynamoDB và trình phát HLS Player kiểm thử End-to-End.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | -------------- |
| 3 | - Chuẩn hóa quy hoạch cấu trúc dữ liệu xuất ra trên Amazon S3 Processed Media Bucket <br> - Phân loại lưu trữ: Master Playlist (.m3u8), Variant Playlists, đoạn video Segment (.ts) và hình ảnh Thumbnail (.jpg) <br> - Xây dựng cơ chế tự động thiết lập Content-Type và Cache-Control header cho từng định dạng tệp <br> | 30/06/2026 | 30/06/2026 | |
| 4 | - Cấu hình dịch vụ phân phối nội dung Amazon CloudFront CDN cho Frontend và tệp phương tiện HLS <br> - Thiết lập Origin Access Control (OAC) vô hiệu hóa quyền truy cập trực tiếp từ Internet vào S3 Bucket <br> - Cấu hình các chính sách Cache Behavior tối ưu cho định dạng tệp tĩnh, tệp playlist và tệp video segment <br> | 01/07/2026 | 01/07/2026 | |
| 5 | - Nghiên cứu và so sánh các giải pháp bảo mật luồng video HLS chống truy cập trái phép <br> - So sánh ưu nhược điểm giữa CloudFront Signed URLs và CloudFront Signed Cookies cho phát trực tuyến HLS <br> - Thử nghiệm tạo URL chứa chữ ký bảo mật có thời gian hết hạn cho luồng phát video <br> | 02/07/2026 | 02/07/2026 | |
| 6 | - Triển khai dịch vụ tường lửa ứng dụng AWS WAF (Web ACL) bảo vệ lớp Edge <br> - Cấu hình bộ quy tắc AWS Managed Rules (Common Rule Set) và quy tắc giới hạn tần suất truy cập Rate-based Rules <br> - Gắn Web ACL vào CloudFront Distribution và kiểm tra các yêu cầu Sampled Requests / Metric giám sát <br> | 03/07/2026 | 03/07/2026 | |
| 2 | - Tích hợp hoàn chỉnh giao diện ứng dụng web Frontend với toàn bộ hệ thống AWS Backend <br> - Kết nối luồng Đăng nhập Cognito -> Lấy danh sách phim API Gateway -> Upload video -> Theo dõi trạng thái -> Trình phát HLS Player <br> - Kiểm thử khả năng chịu tải và tính đồng bộ giữa CloudFront, API Gateway và Lambda <br> | 06/07/2026 | 06/07/2026 | |


### Kết quả đạt được tuần 11:

* Chuẩn hóa cấu trúc lưu trữ và tự động gắn header Content-Type/Cache-Control cho tệp HLS trên S3.
* Cấu hình phân phối nội dung tốc độ cao qua Amazon CloudFront kết hợp OAC bảo vệ tuyệt đối S3 Bucket.
* Thử nghiệm thành công giải pháp giới hạn quyền truy cập video HLS bằng chữ ký an toàn Signed URLs.
* Triển khai AWS WAF thiết lập bộ quy tắc Managed Rules và Rate-limiting ngăn chặn các cuộc tấn công DDoS/Web.
* Tích hợp thành công toàn bộ hệ thống giữa Frontend web, Cognito, API Gateway, Lambda và HLS Player.
