---
title: "Worklog Tuần 6"
date: 2026-05-30
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


### Mục tiêu tuần 6:

- Tìm hiểu các khái niệm cơ bản về database trên AWS.
- Nắm được vai trò của Amazon RDS, Amazon Aurora, Redshift và ElastiCache.
- Thực hành triển khai RDS database instance, kết nối ứng dụng và kiểm tra backup/restore.
- Tìm hiểu và thực hành database migration từ SQL Server/Oracle sang Aurora MySQL.
- Tìm hiểu DynamoDB và các mô hình thiết kế ứng dụng serverless với DynamoDB.
- Tìm hiểu các dịch vụ phân tích dữ liệu trên AWS như Glue, Athena, Kinesis Data Analytics và QuickSight.
- Thực hành tạo pipeline dữ liệu từ ingest, store, catalog, transform, analyze đến visualize.
- Làm quen với CloudShell, SDK, Cloud9 và DataBrew trong quá trình xử lý dữ liệu.
- Hoàn thành các lab chính của Module 06 và Module 07.
- Biết cách kiểm tra kết quả và dọn dẹp tài nguyên sau khi hoàn thành lab.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 6 | Tìm hiểu Database Concepts, RDS, Aurora, Redshift, ElastiCache và thực hành Lab05 về RDS, application deployment, backup/restore | 22/05/2026 | 22/05/2026 | <https://000005.awsstudygroup.com/> |
| 2 | Thực hành Lab43 về database migration, schema conversion, migration task, endpoint, serverless migration và troubleshooting | 25/05/2026 | 25/05/2026 | <https://000043.awsstudygroup.com/> |
| 3 | Tìm hiểu DynamoDB và thực hành Lab39, Lab40 về DynamoDB, backup, design patterns, database table, cost, tagging và query | 26/05/2026 | 26/05/2026 | <https://000039.awsstudygroup.com/><br><https://000040.awsstudygroup.com/> |
| 4 | Thực hành Lab35, Lab60 và Lab70 về S3, delivery stream, Glue Crawler, Athena, QuickSight, CloudShell, SDK, Cloud9 và DataBrew | 27/05/2026 | 27/05/2026 | <https://000035.awsstudygroup.com/><br><https://000070.awsstudygroup.com/> |
| 5 | Thực hành Lab72, Lab73 về data pipeline, Glue, EMR, Athena, Kinesis Data Analytics, Lambda, Redshift, QuickSight dashboard và tổng hợp tuần 6 | 28/05/2026 | 28/05/2026 | <https://000072.awsstudygroup.com/><br><https://000073.awsstudygroup.com/> |

### Kết quả đạt được tuần 6:

- Nắm được các khái niệm cơ bản về database trong hệ thống cloud.
- Phân biệt được nhóm dịch vụ database quan hệ, NoSQL, data warehouse và cache trên AWS.
- Nắm được vai trò của Amazon RDS trong triển khai cơ sở dữ liệu quan hệ được quản lý trên AWS.
- Nắm được vai trò của Amazon Aurora trong nhóm cơ sở dữ liệu quan hệ hiệu năng cao trên AWS.
- Nắm được vai trò của Amazon Redshift trong lưu trữ và phân tích dữ liệu dạng data warehouse.
- Nắm được vai trò của Amazon ElastiCache trong tăng tốc truy cập dữ liệu bằng cache.
- Tạo được VPC phục vụ triển khai môi trường database theo nội dung Lab05.
- Tạo được EC2 Security Group và RDS Security Group.
- Tạo được DB Subnet Group cho RDS.
- Tạo được EC2 instance phục vụ triển khai và kiểm tra ứng dụng.
- Tạo được RDS database instance theo nội dung Lab05.
- Triển khai được ứng dụng kết nối đến database.
- Thực hiện được backup và restore cho RDS database.
- Thực hiện cleanup tài nguyên sau Lab05.
- Kết nối được môi trường Windows thông qua RDP Client và Fleet Manager theo nội dung Lab43.
- Cấu hình được SQL Server source database.
- Kết nối và cấu hình được Oracle source database.
- Thực hiện được thao tác drop constraint phục vụ quá trình migration.
- Cấu hình được target Aurora MySQL cho quá trình migration.
- Tạo được project chuyển đổi từ MSSQL sang Aurora MySQL.
- Thực hiện được schema conversion từ MSSQL sang Aurora MySQL.
- Thực hiện được schema conversion từ Oracle sang MySQL.
- Tạo được migration task và endpoint.
- Kiểm tra được dữ liệu liên quan trong S3.
- Tạo được serverless migration theo nội dung lab.
- Tạo được event phục vụ theo dõi quá trình migration.
- Kiểm tra được logs trong quá trình migration.
- Thực hiện được các bước troubleshooting cho lỗi memory pressure.
- Thực hiện được các bước troubleshooting cho lỗi table error.
- Nắm được vai trò của DynamoDB trong nhóm cơ sở dữ liệu NoSQL trên AWS.
- Làm quen được với DynamoDB Console.
- Thực hiện được backup trong DynamoDB theo nội dung Lab39.
- Nắm được một số design pattern nâng cao cho Amazon DynamoDB.
- Nhận biết được cách xây dựng global serverless application với DynamoDB.
- Nhận biết được cách xây dựng serverless event-driven architecture với DynamoDB.
- Chuẩn bị và xây dựng được database theo nội dung Lab40.
- Thêm và kiểm tra được dữ liệu trong table.
- Kiểm tra được phần cost, tagging và cost allocation cho database.
- Kiểm tra được usage và thực hiện query kết quả theo nội dung lab.
- Tạo được S3 bucket phục vụ luồng dữ liệu trong Lab35.
- Tạo được delivery stream theo nội dung Lab35.
- Tạo được sample data phục vụ kiểm tra luồng dữ liệu.
- Tạo được Glue Crawler để catalog dữ liệu.
- Kiểm tra được dữ liệu sau khi catalog.
- Lưu được output vào S3.
- Thiết lập được session connect setup theo nội dung lab.
- Phân tích được dữ liệu bằng Athena.
- Trực quan hóa được dữ liệu bằng QuickSight.
- Sử dụng được AWS CloudShell trong quá trình thực hành.
- Làm quen được thao tác quản lý tài nguyên thông qua Console và SDK.
- Tạo được Cloud9 instance phục vụ xử lý dữ liệu.
- Tải dataset và upload dataset lên S3.
- Thiết lập được AWS Glue DataBrew.
- Thực hiện được data profiling.
- Thực hiện được clean và transform data bằng DataBrew.
- Thực hiện được các bước ingest and store dữ liệu theo Lab72.
- Catalog được dữ liệu trong pipeline.
- Transform được dữ liệu bằng AWS Glue interactive sessions.
- Transform được dữ liệu bằng AWS Glue GUI.
- Transform được dữ liệu bằng AWS Glue DataBrew.
- Transform được dữ liệu bằng EMR theo nội dung lab.
- Phân tích được dữ liệu bằng Athena.
- Phân tích được dữ liệu bằng Kinesis Data Analytics.
- Trực quan hóa dữ liệu bằng QuickSight.
- Serve được dữ liệu hoặc kết quả xử lý thông qua Lambda.
- Làm quen được mô hình warehouse trên Redshift.
- Xây dựng được dashboard theo Lab73.
- Cải thiện được dashboard sau khi tạo ban đầu.
- Tạo được interactive dashboard theo nội dung Lab73.
- Thực hiện cleanup tài nguyên sau các lab để hạn chế phát sinh chi phí.
- Hoàn thành các lab chính trong tuần 6 gồm Lab05, Lab43, Lab35, Lab39, Lab40, Lab60, Lab70, Lab72 và Lab73.
- Hoàn thành giai đoạn 6 tuần học các bài lý thuyết và lab chính trong playlist.
- Có nền tảng để chuyển sang giai đoạn tiếp theo gồm bài thu hoạch workshop, proposal, blog và project cuối cùng.
