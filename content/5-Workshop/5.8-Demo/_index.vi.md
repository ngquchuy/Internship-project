---
title: "Demo"
date: 2026-07-20
weight: 8
chapter: false
pre: "<b>5.8. </b>"
---

# Demo hệ thống

## Tổng quan

Sau khi hoàn thành các bước triển khai và kiểm thử, video demo được sử dụng để minh họa quy trình hoạt động của **Serverless Video-on-Demand Platform on AWS** trong phạm vi phiên bản MVP. Nội dung trình bày luồng xử lý từ khi người dùng tải video lên hệ thống cho đến khi video được chuyển mã và sẵn sàng để phát trên ứng dụng Web.

## Nội dung Demo

Video minh họa các bước chính của hệ thống theo kiến trúc đã triển khai, bao gồm:

- Đăng nhập vào hệ thống.
- Tải video lên thông qua ứng dụng Web.
- Kiểm tra video nguồn trong Amazon S3 Raw Upload Bucket.
- Theo dõi AWS Elemental MediaConvert thực hiện chuyển mã video.
- Kiểm tra nội dung đầu ra trong Amazon S3 Processed Media Bucket.
- Xác nhận metadata và trạng thái xử lý trong Amazon DynamoDB.
- Phát video trên ứng dụng Web sau khi quá trình xử lý hoàn tất.

## Video Demo

👉 Tài liệu đính kèm gồm Video Demo và Source Code:

https://drive.google.com/drive/folders/1rPrD49VZEmlGYVUGhIUE2riv0jqQ93_J?usp=sharing

Thư mục Google Drive bao gồm:

- 📄 Source code của ứng dụng Web trong Workshop.
- 🎥 Video minh họa quy trình vận hành của hệ thống.

## Kết quả

Video demo cho thấy các chức năng chính của hệ thống có thể hoạt động liên tục theo luồng đã thiết kế. Sau khi video được tải lên, pipeline xử lý được kích hoạt, AWS Elemental MediaConvert tạo nội dung đầu ra, metadata được cập nhật và video có thể được phát thông qua ứng dụng Web.

Kết quả demo được sử dụng làm minh chứng cho việc tích hợp các thành phần chính của kiến trúc trong phạm vi MVP. Các đánh giá chi tiết hơn về hiệu năng, khả năng chịu tải và chi phí cần được thực hiện bằng các kịch bản kiểm thử riêng.
