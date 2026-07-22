---
title: "Worklog Tuần 8"
date: 2024-01-01
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


### Mục tiêu tuần 8:

* Tìm hiểu chuyên sâu kiến thức xử lý video số: Phân biệt Container và Codec, các chuẩn nén MP4, H.264, H.265 và AAC.
* Phân tích cơ chế phát video thích ứng HLS (HTTP Live Streaming), cấu trúc Master Playlist, Media Playlist, Segment và Rendition Ladder.
* Nghiên cứu cấu trúc kỹ thuật của AWS Elemental MediaConvert: Input, Output Group, Job Template, Queue và Service Role.
* Thiết kế Job Template cho MediaConvert với các độ phân giải 1080p, 720p, 480p, cấu hình mã hóa video/audio và sinh ảnh thumbnail.
* Thực hành khởi tạo và kiểm thử MediaConvert job thủ công, đánh giá chất lượng file HLS mã hóa và ghi nhận thông số xử lý.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | -------------- |
| 3 | - Nghiên cứu các khái niệm nền tảng về truyền thông đa phương tiện <br> - Phân biệt giữa Container (MP4, MOV) và Codec (H.264/AVC, H.265/HEVC, AAC) <br> - Tìm hiểu các thông số ảnh hưởng chất lượng video: Resolution, Frame rate (FPS), Bitrate (VBR/CBR) <br> | 09/06/2026 | 09/06/2026 | |
| 4 | - Tìm hiểu chuẩn phát trực tuyến HLS (HTTP Live Streaming) và kỹ thuật Adaptive Bitrate Streaming <br> - Phân tích cấu trúc tệp chỉ mục Master Playlist (.m3u8), Media Playlist đa độ phân giải và các đoạn video Segment (.ts/fMP4) <br> - Xác định Rendition Ladder tối ưu cho thiết bị di động và máy tính <br> | 10/06/2026 | 10/06/2026 | |
| 5 | - Phân tích kiến trúc và cấu trúc thành phần trong dịch vụ AWS Elemental MediaConvert <br> - Tìm hiểu cách cấu hình Input, Output Group, Job Queue, Job Template và phân quyền IAM Execution Role <br> - Đánh giá cơ chế quản lý quota và chi phí chuyển mã theo phút video <br> | 11/06/2026 | 11/06/2026 | |
| 6 | - Thiết kế chi tiết MediaConvert Job Template cho hệ thống Video-on-Demand <br> - Định nghĩa các mức chất lượng đầu ra: 1080p (Full HD), 720p (HD) và 480p (SD) tùy theo video gốc <br> - Cấu hình mã hóa âm thanh AAC, kích thước Segment (6 giây) và cơ chế tự động trích xuất thumbnail <br> | 12/06/2026 | 12/06/2026 | |
| 2 | - Thực hành khởi chạy thử nghiệm MediaConvert Job thủ công từ tệp video mẫu MP4 <br> - Trích xuất và kiểm tra bộ tệp HLS output: Master Playlist, Playlist con, các file Segment và Thumbnail <br> - Ghi nhận thời gian chuyển mã, dung lượng file output và đo lường chi phí xử lý thực tế <br> | 15/06/2026 | 15/06/2026 | |


### Kết quả đạt được tuần 8:

* Nắm vững các khái niệm nén video, chuẩn codec H.264/AAC và cơ chế phát video thích ứng HLS.
* Hiểu rõ cấu trúc tệp tin phát trực tuyến HLS gồm Master Playlist, Variant Playlists và các đoạn Segment.
* Nắm vững kiến trúc chuyển mã của AWS Elemental MediaConvert, bao gồm các thành phần Input, Output Group và Job Template.
* Xây dựng thành công Job Template chuẩn hóa chuyển mã video thành 3 mức độ phân giải (1080p, 720p, 480p) kèm trích xuất thumbnail.
* Thực hiện chuyển mã thử nghiệm thành công tệp MP4 mẫu sang định dạng HLS và kiểm tra chất lượng phát video.
