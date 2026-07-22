---
title: "Worklog Tuần 9"
date: 2024-01-01
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


### Mục tiêu tuần 9:

* Cấu hình dịch vụ quản lý định danh Amazon Cognito User Pool, thiết lập App Client và cơ chế xác thực JWT.
* Thiết kế API Gateway REST/HTTP API, quy hoạch các Resource Route, cấu hình CORS và JWT Authorizer.
* Xây dựng ứng dụng Backend Serverless với AWS Lambda cho các tác vụ nghiệp vụ quản lý phim và người dùng.
* Thiết kế mô hình dữ liệu trên Amazon DynamoDB tối ưu theo truy vấn Access Pattern cho dự án VOD.
* Triển khai cơ chế sinh Presigned Upload URL giúp Client tải trực tiếp video vào S3 Raw Upload Bucket an toàn.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | -------------- |
| 3 | - Cấu hình Amazon Cognito User Pool quản lý người dùng ứng dụng <br> - Thiết lập App Client, cấu hình luồng Đăng ký, Đăng nhập, Đăng xuất và Xác nhận Email <br> - Tìm hiểu cấu trúc và cơ chế xác thực của ID Token, Access Token và Refresh Token <br> | 16/06/2026 | 16/06/2026 | |
| 4 | - Thiết kế kiến trúc Amazon API Gateway cho các API nghiệp vụ của hệ thống <br> - Định nghĩa các Route, Method (GET, POST, PUT, DELETE), tham số Request/Response và định dạng JSON <br> - Cấu hình Cognito JWT Authorizer bảo vệ API và bật chia sẻ tài nguyên CORS <br> | 17/06/2026 | 17/06/2026 | |
| 5 | - Phát triển các hàm AWS Lambda xử lý nghiệp vụ chính bằng Node.js/Python <br> - Viết code xử lý lấy danh sách phim, chi tiết phim, tạo bài đăng phim và cập nhật trạng thái xử lý video <br> - Chuẩn hóa quy trình xử lý ngoại lệ (Exception Handling) và định dạng Response trả về <br> | 18/06/2026 | 18/06/2026 | |
| 6 | - Thiết kế mô hình dữ liệu Amazon DynamoDB dựa trên các luồng truy vấn (Access Pattern) <br> - Tạo bảng `Movies` lưu thông tin: movieId, title, status, rawS3Key, hlsPath, createdAt, updatedAt <br> - Cấu hình Partition Key, Sort Key và triển khai các thao tác CRUD từ Lambda qua AWS SDK <br> | 19/06/2026 | 19/06/2026 | |
| 2 | - Xây dựng API Lambda tạo Presigned Upload URL cho dịch vụ Amazon S3 <br> - Kiểm tra tính hợp lệ của loại tệp (Video/MP4), dung lượng và khởi tạo đường dẫn S3 Raw Object Key <br> - Kiểm thử tích hợp luồng: Đăng nhập -> Nhận JWT -> Gọi API sinh Presigned URL -> Upload video trực tiếp lên S3 <br> | 22/06/2026 | 22/06/2026 | |


### Kết quả đạt được tuần 9:

* Khởi tạo và cấu hình thành công Amazon Cognito User Pool cho phép xác thực người dùng an toàn bằng JWT Token.
* Xây dựng hệ thống API Gateway được bảo vệ bởi Cognito JWT Authorizer và cấu hình CORS đầy đủ.
* Hoàn thiện các hàm AWS Lambda xử lý nghiệp vụ quản lý danh mục phim và trạng thái video.
* Thiết kế bảng DynamoDB lưu trữ metadata phim tối ưu cho các thao tác đọc/ghi của hệ thống.
* Triển khai thành công luồng sinh S3 Presigned URL hỗ trợ Client tải file video trực tiếp lên S3 Raw Bucket.
