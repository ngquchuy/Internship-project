---
title: "Blog 3"
date: 2026-06-01
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây là phần tổng hợp nội dung blog em đã đọc và đăng trong quá trình thực tập, không phải tài liệu chính thức thay thế cho bài viết gốc của AWS.
{{% /notice %}}

# BÀI HỌC TỪ VIỆC MỞ RỘNG HỆ THỐNG ĐẾN 1 TRIỆU AWS LAMBDA FUNCTIONS

Trong kỷ nguyên điện toán đám mây hiện đại, kiến trúc Serverless (không máy chủ) đã trở thành lựa chọn hàng đầu cho các doanh nghiệp nhờ khả năng tự động mở rộng và mô hình chi phí linh hoạt. Tuy nhiên, việc vận hành một hệ thống đạt đến quy mô 1 triệu AWS Lambda executions mỗi ngày đặt ra những thách thức kỹ thuật lớn về quản lý concurrency, xử lý độ trễ cold start và đảm bảo tính sẵn sàng cao.

━━━━━━━━━━━━━━━

## Kiến trúc hệ thống: Bài toán hiệu năng và sự kết hợp dịch vụ

Khi mở rộng hệ thống Serverless lên quy mô lớn, việc gọi trực tiếp các dịch vụ theo cơ chế đồng bộ (synchronous) dễ dẫn đến tình trạng quá tải và nghẽn hệ thống. Để giải quyết bài toán này, giải pháp tối ưu là chuyển sang kiến trúc hướng sự kiện (event-driven architecture) kết hợp các dịch vụ được quản lý chuyên biệt của AWS.

━━━━━━━━━━━━━━━

## Chi tiết cơ chế vận hành phối hợp

- **Amazon SQS làm bộ đệm hấp thụ tải:** Amazon SQS đóng vai trò làm hàng đợi đệm để tiếp nhận toàn bộ các sự kiện đầu vào, giúp phân tách luồng xử lý và đảm bảo hệ thống không bị quá tải khi có lượng truy cập đột biến.
- **AWS Step Functions điều phối trạng thái:** AWS Step Functions chịu trách nhiệm điều phối toàn bộ workflow xử lý bất đồng bộ, quản lý trạng thái của từng bước thực thi và đảm bảo tính nhất quán của dữ liệu.

━━━━━━━━━━━━━━━

## So sánh hai mô hình kiến trúc

| Tiêu chí so sánh | Kiến trúc đồng bộ truyền thống (Synchronous) | Kiến trúc hướng sự kiện (Event-Driven) |
| --- | --- | --- |
| Khả năng chịu tải đỉnh | Dễ bị sập nguồn (Throttling / 503 Service Unavailable) | SQS hấp thụ và điều tiết dòng chảy mượt mà |
| Tối ưu hóa chi phí | Cao (Do lãng phí thời gian idle chờ kết quả dịch vụ con) | Tối ưu tuyệt đối (Chỉ trả tiền khi Lambda thực sự xử lý) |
| Độ phức tạp mã nguồn | Thấp ban đầu, nhưng khó handle lỗi logic phức tạp | Cần thiết lập State Machine nhưng tách biệt rõ ràng trách nhiệm |
| Cơ chế Retry/Khôi phục | Phức tạp, dễ gây lặp dữ liệu hoặc mất mát dữ liệu | Tự động thông qua Step Functions và Dead Letter Queue (DLQ) |

━━━━━━━━━━━━━━━

## Ba bài học kỹ thuật cốt lõi dành cho kỹ sư Cloud

### 1. Làm chủ Concurrency và tránh hiện tượng Throttling

Việc thiết lập mức Reserved Concurrency cho các hàm Lambda quan trọng giúp đảm bảo tài nguyên tính toán luôn sẵn sàng, đồng thời cấu hình Provisioned Concurrency đối với các hàm có yêu cầu khắt khe về thời gian phản hồi.

### 2. Tinh giản package và kiểm soát Cold Start

Giảm thiểu dung lượng deployment package bằng cách tối ưu hóa các thư viện phụ thuộc (dependencies), sử dụng AWS Lambda Layers và chọn runtime có thời gian khởi tạo nhanh như Node.js hoặc Go.

### 3. Thiết kế cơ chế chịu lỗi chủ động

Kết hợp hàng đợi Dead-Letter Queue (DLQ) trên Amazon SQS cùng chính sách retry tự động của AWS Step Functions nhằm bắt kịp thời các sự cố phát sinh mà không làm gián đoạn luồng xử lý chính.

━━━━━━━━━━━━━━━

## Ứng dụng thực tế: Cấu hình Infrastructure as Code

```yaml
AWSTemplateFormatVersion: '2010-09-09'
Transform: AWS::Serverless-2016-10-31
Description: Event-driven architecture scaling to 1 million AWS Lambda executions.

Resources:
  ProcessingQueue:
    Type: AWS::SQS::Queue
    Properties:
      QueueName: HighScaleProcessingQueue
      VisibilityTimeout: 300
      MessageRetentionPeriod: 86400
      RedrivePolicy:
        deadLetterTargetArn: !GetAtt ProcessingDLQ.arn
        maxReceiveCount: 3

  ProcessingDLQ:
    Type: AWS::SQS::Queue
    Properties:
      QueueName: HighScaleProcessingDLQ

  HighScaleLambdaFunction:
    Type: AWS::Serverless::Function
    Properties:
      FunctionName: HighScaleWorker
      CodeUri: src/
      Handler: app.handler
      Runtime: nodejs18.x
      MemorySize: 512
      Timeout: 30
      ReservedConcurrentExecutions: 500
      Events:
        SQSEvent:
          Type: SQS
          Properties:
            Queue: !GetAtt ProcessingQueue.arn
            BatchSize: 10
```

━━━━━━━━━━━━━━━

## Ứng dụng thực tế và thảo luận cộng đồng

Việc triển khai kiến trúc Serverless quy mô 1 triệu AWS Lambda executions đòi hỏi sự kết hợp chặt chẽ giữa các nguyên tắc thiết kế event-driven, công cụ giám sát tập trung và mô hình quản lý hạ tầng bằng mã nguồn (IaC). Đây là nền tảng quan trọng giúp các hệ thống hiện đại vận hành ổn định, linh hoạt và tối ưu hóa chi phí trên nền tảng đám mây AWS.

━━━━━━━━━━━━━━━

## Link bài gốc

AWS Architecture Blog:  
https://aws.amazon.com/vi/blogs/architecture/lessons-learned-from-scaling-to-1-million-lambda-functions/

AWS Study Group:  
https://www.facebook.com/groups/awsstudygroupfcj/permalink/2199927530772207/

## Hình ảnh