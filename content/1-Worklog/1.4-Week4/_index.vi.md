---
title: "Worklog Tuần 4"
date: 2026-05-16
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


### Mục tiêu tuần 4:

- Tìm hiểu nhóm dịch vụ lưu trữ trên AWS và vai trò của từng loại storage.
- Nắm được các thành phần quan trọng của Amazon S3 như bucket, object, access control, storage class, access point và object key.
- Hiểu cách triển khai static website trên S3 và kết hợp với CloudFront để phân phối nội dung.
- Tìm hiểu các dịch vụ lưu trữ và di chuyển dữ liệu như S3 Glacier, Snow Family, Storage Gateway và VM Import/Export.
- Thực hành tạo S3 bucket, triển khai hạ tầng, tạo backup plan, cấu hình notification và kiểm tra restore theo Lab13.
- Thực hành VM Import/Export theo Lab14.
- Thực hành triển khai File Storage Gateway và mount file share từ máy on-premises theo Lab24.
- Thực hành triển khai FSx trên Windows và kiểm tra các tính năng quản lý file system theo Lab25.
- Thực hành triển khai static website trên S3, cấu hình CloudFront, versioning và sao chép object sang region khác theo Lab57.
- Biết cách kiểm tra kết quả và dọn dẹp tài nguyên sau khi hoàn thành lab.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành |
| --- | --- | --- | --- |
| 6 | Tìm hiểu dịch vụ lưu trữ trên AWS, Amazon S3, storage class, access control và thực hành Lab13 về S3 bucket, backup plan, notification, restore | 08/05/2026 | 08/05/2026 |
| 2 | Tìm hiểu VM Import/Export, S3 bucket ACL và thực hành Lab14 về import/export máy ảo giữa môi trường on-premises và AWS | 11/05/2026 | 11/05/2026 |
| 3 | Tìm hiểu Storage Gateway, Snow Family, Glacier và thực hành Lab24 về File Storage Gateway, file shares, mount từ máy on-premises | 12/05/2026 | 12/05/2026 |
| 4 | Tìm hiểu file storage trên AWS và thực hành Lab25 về FSx for Windows, Multi-AZ file system, hiệu năng, shadow copy, quota và mở rộng lưu trữ | 13/05/2026 | 13/05/2026 |
| 5 | Tìm hiểu S3 Static Website, CORS, Object Key, Performance, CloudFront và thực hành Lab57 về static website, versioning, object copy, cleanup | 14/05/2026 | 14/05/2026 |

### Kết quả đạt được tuần 4:

- Nắm được vai trò của nhóm dịch vụ lưu trữ trên AWS trong việc lưu trữ object, block, file và dữ liệu backup.
- Phân biệt được các hướng lưu trữ chính trên AWS như object storage, file storage, block storage và archive storage.
- Nắm được vai trò của Amazon S3 trong lưu trữ object trên AWS.
- Tạo được S3 bucket phục vụ cho các bài lab liên quan đến backup, static website và lưu trữ dữ liệu.
- Hiểu được vai trò của S3 object, object key và bucket trong quá trình tổ chức dữ liệu trên S3.
- Nắm được vai trò của S3 Storage Class trong việc lựa chọn lớp lưu trữ phù hợp với nhu cầu truy cập và chi phí.
- Nắm được vai trò của S3 Access Point trong việc quản lý truy cập dữ liệu ở quy mô lớn.
- Hiểu được các cơ chế kiểm soát truy cập trong S3 như Block Public Access, public object và bucket ACL.
- Nắm được vai trò của CORS khi static website hoặc ứng dụng web cần truy cập tài nguyên từ S3.
- Nắm được các yếu tố cơ bản ảnh hưởng đến hiệu năng khi tổ chức object trên S3.
- Nhận biết được vai trò của Amazon S3 Glacier trong lưu trữ dữ liệu dài hạn.
- Nhận biết được vai trò của AWS Snow Family trong các tình huống di chuyển dữ liệu dung lượng lớn.
- Nắm được vai trò của AWS Storage Gateway trong việc kết nối lưu trữ giữa môi trường on-premises và AWS.
- Nắm được vai trò của AWS Backup trong việc tạo kế hoạch sao lưu và khôi phục tài nguyên.
- Triển khai được hạ tầng theo yêu cầu của Lab13.
- Tạo được backup plan theo nội dung Lab13.
- Cấu hình được notification cho backup plan theo yêu cầu lab.
- Kiểm tra được quá trình restore sau khi tạo backup.
- Thực hiện cleanup tài nguyên sau Lab13 để hạn chế phát sinh chi phí.
- Nắm được quy trình VM Import/Export trong việc di chuyển máy ảo giữa môi trường on-premises và AWS.
- Chuẩn bị được máy ảo phục vụ cho quá trình export/import theo Lab14.
- Export được virtual machine từ môi trường on-premises theo nội dung lab.
- Upload được virtual machine lên AWS thông qua S3 theo yêu cầu lab.
- Import được virtual machine vào AWS theo nội dung Lab14.
- Triển khai được EC2 instance từ AMI sau quá trình import.
- Cấu hình được S3 bucket ACL theo yêu cầu của quá trình VM Import/Export.
- Export được virtual machine từ instance theo nội dung Lab14.
- Thực hiện cleanup tài nguyên trên AWS Cloud sau Lab14.
- Tạo được Storage Gateway theo nội dung Lab24.
- Tạo được File Shares phục vụ kết nối lưu trữ giữa on-premises và AWS.
- Mount được File Shares trên máy on-premises theo nội dung thực hành.
- Thực hiện cleanup tài nguyên sau Lab24.
- Tạo được SSD Multi-AZ file system trong FSx for Windows theo nội dung Lab25.
- Tạo được HDD Multi-AZ file system trong FSx for Windows theo nội dung Lab25.
- Ánh xạ được file share mặc định trong môi trường Windows.
- Tạo được file mới trên file share để kiểm tra hoạt động lưu trữ.
- Kiểm tra được hiệu năng của file system trong bài lab FSx.
- Kích hoạt được tính năng chống dữ liệu trùng lặp.
- Kích hoạt được shadow copy cho file system.
- Quản lý được sessions người dùng và các tệp đang mở.
- Kích hoạt được hạn ngạch bộ nhớ của người dùng.
- Kích hoạt được chia sẻ truy cập liên tục.
- Mở rộng được khả năng thông lượng của file system.
- Mở rộng được dung lượng lưu trữ của file system.
- Thực hiện cleanup tài nguyên sau Lab25.
- Bật được tính năng Static Website Hosting trên S3 theo nội dung Lab57.
- Cấu hình được Block Public Access và Public Object phù hợp với yêu cầu triển khai static website.
- Kiểm tra được website tĩnh được host trên Amazon S3.
- Chặn lại toàn bộ truy cập công cộng vào S3 sau khi hoàn thành phần kiểm tra theo yêu cầu lab.
- Cấu hình được Amazon CloudFront để phân phối nội dung static website.
- Kiểm tra được hoạt động của static website thông qua CloudFront.
- Bật và sử dụng được tính năng Bucket Versioning.
- Thực hiện được thao tác di chuyển object trong S3.
- Thực hiện được thao tác sao chép S3 object sang Region khác.
- Thực hiện cleanup tài nguyên sau Lab57.
- Hoàn thành các lab chính trong tuần 4 gồm Lab13, Lab14, Lab24, Lab25 và Lab57.
- Hình thành thói quen kiểm tra trạng thái tài nguyên, kết quả lab và dọn dẹp tài nguyên sau khi thực hành.
