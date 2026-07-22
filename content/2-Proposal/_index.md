---
title: "Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

# Proposal

The demand for storing, processing, and streaming Video-on-Demand (VoD) media is growing rapidly across modern applications. However, building and maintaining traditional media processing infrastructure based on fixed servers often faces major challenges regarding high initial capital expenditure, rigid scaling limits, and idle server resources during off-peak hours. Meanwhile, video transcoding tasks exhibit intensive compute resource spikes over short durations immediately after new media files are uploaded.

To address the imbalance between utilization frequency and instantaneous resource demands, this proposal adopts an approach based on serverless computing and event-driven architecture on the Amazon Web Services (AWS) cloud platform. The project aims to design and implement a complete Serverless Video-on-Demand Platform on AWS, establishing a clear separation between direct user interaction tasks and background media processing pipelines. The system aims to provide secure upload flows, automated transcoding into HTTP Live Streaming (HLS) formats, optimized video playback user experiences, and centralized observability.


## Problem Statement

Within a Video-on-Demand platform, ingesting, processing, and delivering media files requires solving the following synchronized technical challenges:

- **Large Video File Upload and Storage:** Raw video files are large and consume substantial bandwidth. Transmitting media through traditional application backends easily causes network congestion, temporary memory exhaustion, and increased connection drop rates.
- **Compute-Intensive Transcoding Tasks:** Input media files need to be converted into HLS streaming formats with multiple resolutions and bitrates to ensure compatibility across diverse viewer devices. This process requires heavy compute capacity occurring in unpredictable bursts.
- **High-Volume Content Delivery:** Streaming HLS video segments directly from origin storage can introduce high latency and prohibitive egress bandwidth costs without edge content delivery networking.
- **Asynchronous Processing State Management:** Prolonged transcoding tasks require accurate status tracking (such as `UPLOADED`, `PROCESSING`, `READY`, `FAILED`) to provide UI feedback without blocking clients synchronously.
- **Ensuring Availability, Observability, and Cost Controls:** The system must incorporate fault tolerance, incident message handling, and centralized operational logging without incurring fixed server management costs.


## Proposed Solution

The proposal builds a comprehensive Serverless Video-on-Demand Platform on AWS solution by orchestrating specialized managed AWS services in a closed-loop processing workflow:

1. **User Authentication:** Users log in via Amazon Cognito User Pool to receive valid JWT tokens.
2. **Business API Call:** Users issue requests to Amazon API Gateway; requests are authenticated automatically by Cognito JWT Authorizer before being routed to AWS Lambda.
3. **Presigned URL Generation:** AWS Lambda generates an Amazon S3 presigned URL and returns it to the client application.
4. **Direct Media Upload:** The user browser uses the presigned URL to upload raw video files directly into Amazon S3 Raw Upload Bucket, bypassing backend servers.
5. **Event Emission and Routing:** New file uploads to S3 trigger `Object Created` events. These events are captured and filtered by Amazon EventBridge according to predefined event patterns.
6. **Message Queuing:** EventBridge routes events to Amazon SQS queues to buffer messages and isolate asynchronous workloads.
7. **Workflow Orchestration Initiation:** Amazon EventBridge Pipes reads messages from SQS, transforms input payloads, and triggers state machine execution on AWS Step Functions.
8. **Transcoding Execution:** AWS Step Functions orchestrates the workflow and invokes AWS Elemental MediaConvert to transcode raw video into HLS packages (master playlist, variant playlists, media segments) and thumbnail images.
9. **Transcoded Output Storage:** Completed HLS assets are written directly to Amazon S3 Processed Media Bucket.
10. **Data and Status Update:** AWS Step Functions updates file metadata and HLS playback paths in Amazon DynamoDB tables.
11. **High-Speed Content Delivery:** Users access and stream HLS videos via Amazon CloudFront CDN, protected by AWS WAF and Origin Access Control (OAC).
12. **Centralized Observability:** Logs, performance metrics, and incident alarms from API Gateway, Lambda, SQS, Step Functions, and MediaConvert are collected centrally in Amazon CloudWatch.


## Proposed Architecture

The system architecture is designed with clear layer decoupling to minimize inter-component dependencies, enabling individual services to scale independently based on actual demand. The strict separation between synchronous workflows (authentication, API calls, presigned URL generation) and asynchronous processing (event ingestion, message queuing, workflow orchestration, transcoding) improves overall system availability, facilitating testing, fault isolation, and operational monitoring.

![Proposed Architecture of Serverless Video-on-Demand Platform on AWS](/images/2-Proposal/VOD.drawio.png)  
*Figure 2.1. Proposed Architecture of Serverless Video-on-Demand Platform on AWS.*


## Architectural Description

The Serverless Video-on-Demand Platform on AWS architecture is organized into 7 functional layers:

- **Identity & Access Layer:** Employs Amazon Cognito for user management, providing registration, login, and JWT token issuance to secure system resource access.
- **Edge & Content Delivery Layer:** Consists of Amazon CloudFront integrated with AWS WAF and Amazon S3 Frontend Bucket. The web interface is hosted in a private S3 bucket. CloudFront delivers static web assets and HLS video streams to users with low latency, using Origin Access Control (OAC) to restrict direct Internet access to the S3 origin. AWS WAF attached to CloudFront filters malicious traffic and guards against application-layer attacks.
- **Application Layer:** Comprises Amazon API Gateway and AWS Lambda functions. API Gateway handles HTTP/REST requests, verifies tokens via JWT Authorizer, and routes requests to Lambda. AWS Lambda executes short-lived business logic, such as S3 presigned URL generation and catalog retrieval.
- **Data Layer:** Includes Amazon DynamoDB, Amazon S3 Raw Upload Bucket, and Amazon S3 Processed Media Bucket. DynamoDB stores movie metadata, user records, and video processing states. S3 Raw Upload Bucket stores uploaded source videos. S3 Processed Media Bucket stores output HLS assets and thumbnails.
- **Event Processing Layer:** Encompasses Amazon EventBridge, Amazon SQS (with SQS Dead-Letter Queue), Amazon EventBridge Pipes, and AWS Step Functions. Upon file upload to S3 Raw Bucket, EventBridge routes event notifications to SQS queues for buffering. SQS handles load spikes and forwards failed messages to Dead-Letter Queue (DLQ). EventBridge Pipes polls SQS messages to trigger AWS Step Functions State Machine, which orchestrates execution steps and status updates.
- **Media Processing Layer:** Utilizes AWS Elemental MediaConvert as the dedicated transcoding service. MediaConvert receives raw video files from S3 Raw Bucket upon Step Functions invocation, compresses and packages them into HLS playlists (.m3u8), video segments (.ts), and thumbnails (.jpg), outputting results to S3 Processed Media Bucket.
- **Monitoring Layer:** Uses Amazon CloudWatch to centrally gather logs, metrics, and set up alarms across API Gateway, Lambda, SQS, Step Functions, and MediaConvert.


## Implementation Plan

The Serverless Video-on-Demand Platform on AWS implementation roadmap is structured into sequential phases:

The initial phase focuses on refining system requirements, finalizing layered architecture, and selecting appropriate AWS managed services. Next, the team builds static web frontend interfaces, integrates Amazon Cognito user authentication, and sets up business APIs on Amazon API Gateway paired with AWS Lambda.

The subsequent phase designs metadata structures on Amazon DynamoDB and implements S3 presigned URL generation enabling client applications to upload video files directly to Amazon S3 Raw Upload Bucket. Following upload workflow completion, efforts focus on asynchronous event-driven pipelines, including Amazon EventBridge event rules, Amazon SQS queues, Dead-Letter Queues, and Amazon EventBridge Pipes setup.

In the media processing phase, the team designs AWS Step Functions orchestration workflows and configures AWS Elemental MediaConvert Job Templates generating multi-resolution HLS outputs and thumbnails. Transcoded outputs are stored in Amazon S3 Processed Media Bucket and configured for delivery through Amazon CloudFront CDN protected by Origin Access Control (OAC) and AWS WAF.

The final phase establishes Amazon CloudWatch observability, conducts comprehensive end-to-end integration testing, evaluates real-world performance metrics and operational costs, finalizes report documentation, and prepares project demonstration scripts.


## Estimated Costs

Infrastructure Costs

AWS Elemental MediaConvert: 22.50 USD/month (10 videos, 60 minutes each, HLS 1080p, 720p, and 480p outputs).

Amazon S3 Standard: 1.60 USD/month (63 GB raw video storage, HLS content, thumbnails, and frontend).

Amazon CloudFront and AWS WAF: 0.00 USD/month (under 100 GB data transfer out and under 1 million requests).

Amazon Cognito: 0.00 USD/month (100 active users).

Amazon API Gateway: 0.05 USD/month (50,000 requests).

AWS Lambda: 0.00 USD/month (100,000 requests, 512 MB memory).

Amazon DynamoDB: 0.05 USD/month (50,000 read and 10,000 write metadata requests).

Amazon EventBridge: 0.00 USD/month (1,000 events).

Amazon SQS and Dead-Letter Queue: 0.00 USD/month (under 1 million requests).

Amazon EventBridge Pipes: 0.00 USD/month (1,000 messages).

AWS Step Functions: 0.00 USD/month (10 workflows and under 4,000 state transitions).

Amazon CloudWatch: 0.50 USD/month (1 GB logs, basic dashboard, and alarms).

Total: 24.70 USD/month, 296.40 USD/12 months.


## Expected Outcomes

Based on the proposed architectural design, the Serverless Video-on-Demand Platform on AWS is expected to achieve the following technical outcomes:

- Provide secure user authentication and authorization mechanisms via Cognito and JWT Authorizers.
- Support direct client upload of large video files into S3 Raw Bucket using presigned URLs, reducing backend application load.
- Fully automate raw video transcoding into multi-resolution HLS streaming assets and thumbnail generation.
- Enable users to track asynchronous video processing states in real time based on DynamoDB updates.
- Deliver HLS video streams with low latency and smooth playback across user browsers via CloudFront CDN.
- Maintain comprehensive operational logging and early anomaly detection capabilities via CloudWatch.
- Automatically scale system capacity in response to user traffic without manual administrative intervention.


## Conclusion

This proposal presented an architectural blueprint for a Serverless Video-on-Demand Platform on AWS to address infrastructure cost, scalability, and media processing performance challenges inherent in traditional server-based models. By combining AWS managed serverless services, the proposed architecture effectively decouples synchronous user interactions from asynchronous transcoding workflows, establishing a solid foundation for system development. This proposal serves as a key technical guide, directing detailed implementation, testing, and evaluation steps in subsequent project phases.