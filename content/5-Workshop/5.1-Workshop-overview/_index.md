---
title: "Workshop Overview"
date: 2026-07-20
weight: 1
chapter: false
pre: "<b>5.1. </b>"
---

# 5.1. Workshop Overview

## Introduction

Section 5.1 provides a comprehensive overview of the implementation process for the **Serverless Video-on-Demand Platform on AWS**. Unlike previous chapters focusing on theoretical analysis and architectural design, this workshop section emphasizes practical hands-on implementation steps across AWS cloud services.

The system is designed around a serverless architecture and event-driven architecture to strictly decouple synchronous user interface interactions from asynchronous background media processing pipelines. This approach reduces the need to maintain fixed application servers, supports workload-based scaling, and automates video processing workflows once system components are configured.


## Workshop Objectives

Upon completing the workshop, readers are expected to be able to deploy and test the main components of the proposed Video-on-Demand platform within the scope of the project. Specific objectives include:

- Initialize and configure Amazon Cognito User Pool for identity management, user authentication, and JWT issuance.
- Set up Amazon API Gateway paired with JWT Authorizer to secure and route API requests.
- Develop AWS Lambda functions executing business logic, including generating S3 presigned URLs for direct client uploads into Amazon S3 Raw Upload Bucket.
- Design Amazon DynamoDB tables for movie metadata storage and asynchronous processing status tracking.
- Build an event-driven video processing pipeline combining Amazon S3, Amazon EventBridge, Amazon SQS (with Dead-Letter Queue), Amazon EventBridge Pipes, and AWS Step Functions orchestration.
- Integrate AWS Elemental MediaConvert for automated video transcoding into multi-resolution HLS streaming outputs and thumbnails.
- Configure output storage in Amazon S3 Processed Media Bucket and deliver low-latency HLS streams via Amazon CloudFront CDN protected by AWS WAF and Origin Access Control (OAC).
- Host static web application assets in a private Amazon S3 Frontend Bucket.
- Establish centralized monitoring with Amazon CloudWatch to collect operational logs, metrics, and incident alarms.


## System Architecture

The deployment architecture of the Serverless Video-on-Demand Platform on AWS is structured into three primary functional domains:

- **Frontend:** The web application UI is hosted in a private S3 Frontend Bucket and distributed via Amazon CloudFront CDN protected by AWS WAF. Users authenticate via Amazon Cognito to obtain JWTs before invoking system APIs.
- **Backend:** Consists of Amazon API Gateway handling API requests, validating tokens via JWT Authorizers, and routing to AWS Lambda. The backend does not proxy video files directly; instead, it generates presigned URLs enabling browser uploads directly to Amazon S3 Raw Upload Bucket while recording initial metadata in Amazon DynamoDB.
- **Video Processing Pipeline:** An asynchronous media processing workflow operating independently from user upload requests. New file uploads to S3 Raw Bucket trigger Object Created events, filtered by Amazon EventBridge, queued in Amazon SQS, and routed via Amazon EventBridge Pipes to trigger AWS Step Functions executing AWS Elemental MediaConvert transcoding into HLS assets stored in Amazon S3 Processed Media Bucket.


## AWS Services Used

The table below summarizes the AWS services integrated within the system and their specific operational roles:

| Service | Operational Role |
| --- | --- |
| Amazon S3 | Stores static frontend assets, raw source videos, and processed HLS video content |
| Amazon CloudFront | Distributes web application UI and HLS video streaming content |
| AWS WAF | Filters and controls application traffic protecting CloudFront |
| Amazon Cognito | Manages user identities, authentication, and JWT issuance |
| Amazon API Gateway | Ingests, secures, and exposes business APIs for the web application |
| AWS Lambda | Executes short-lived backend business logic and service integrations |
| Amazon DynamoDB | Stores movie metadata and tracks video processing states |
| Amazon EventBridge | Filters and routes Object Created events from Amazon S3 |
| Amazon SQS | Buffers event messages and supports asynchronous processing |
| EventBridge Pipes | Connects Amazon SQS queues to AWS Step Functions state machines |
| AWS Step Functions | Orchestrates video processing workflows and status updates |
| AWS Elemental MediaConvert | Transcodes raw source video files into HLS streaming packages |
| Amazon CloudWatch | Gathers operational logs, performance metrics, and configures alarms |


## Overall System Workflow

After the required resources and permissions are configured, valid uploads can initiate the processing workflow automatically when video files are uploaded to S3 Raw Upload Bucket:

1. Users register, log in, and authenticate via Amazon Cognito to receive JWT tokens.
2. The web application issues API requests with JWT tokens to Amazon API Gateway; requests are validated by Cognito JWT Authorizer.
3. Amazon API Gateway routes requests to AWS Lambda to execute S3 presigned URL generation logic.
4. AWS Lambda records initial video metadata with an `UPLOADED` status in Amazon DynamoDB tables.
5. The web application browser uses the presigned URL to upload raw video files directly into Amazon S3 Raw Upload Bucket.
6. The uploaded file triggers an `Object Created` event from S3 sent to Amazon EventBridge.
7. Amazon EventBridge Rule filters the event and routes message payloads into Amazon SQS queues.
8. Amazon EventBridge Pipes reads messages from SQS, transforms input payloads, and triggers AWS Step Functions state machine execution.
9. AWS Step Functions orchestrates the workflow, updates status to `PROCESSING`, and invokes AWS Elemental MediaConvert.
10. AWS Elemental MediaConvert compresses and transcodes raw video into HLS assets (master playlist, variant playlists, segments) and thumbnails.
11. HLS output assets are written directly to Amazon S3 Processed Media Bucket.
12. Upon transcoding completion, the video status is updated to `READY` and HLS playback paths are saved in Amazon DynamoDB.
13. Users stream HLS video content with low latency via Amazon CloudFront CDN.
14. Amazon CloudWatch continuously collects logs and metrics, emitting alarms if operational anomalies occur.


## Workshop Structure

The workshop implementation content is structured into 6 sequential sections:

1. **5.2. Prerequisites:** Setting up AWS accounts, IAM roles, CLI tools, and initial environment resources.
2. **5.3. Build the Backend:** Configuring Cognito, API Gateway, Lambda, and DynamoDB; testing presigned URL generation APIs and direct S3 uploads.
3. **5.4. Build the Video Processing Pipeline:** Configuring EventBridge, SQS, EventBridge Pipes, Step Functions, and MediaConvert.
4. **5.5. System Testing:** Conducting end-to-end testing from upload, transcoding, to status updates.
5. **5.6. Build the Web Application:** Integrating Frontend UI with Backend APIs and HLS Video Player.
6. **5.7. Conclusion:** Evaluating implementation results and summarizing key technical takeaways.


## Workshop Organization

Sections 5.2 through 5.7 provide step-by-step guidance organized logically to guide readers through practical deployment: section 5.2 prepares environmental prerequisites, section 5.3 constructs backend APIs and database tables, section 5.4 establishes asynchronous event processing pipelines, section 5.5 performs functional testing, section 5.6 connects web frontend interfaces, and section 5.7 concludes the project implementation.


## Expected Outcomes

When the configuration steps are completed within the workshop scope, readers are expected to verify the following outcomes:

- API Gateway and Lambda return expected presigned URL responses for valid requests.
- Initial file metadata is correctly recorded in DynamoDB tables.
- Video files are uploaded directly from the browser into S3 Raw Upload Bucket via presigned URLs.
- Upload events are queued in SQS and EventBridge Pipes triggers Step Functions execution.
- MediaConvert jobs execute and generate valid HLS outputs and thumbnails in S3 Processed Media Bucket.
- Video processing states in DynamoDB are updated to `READY`.
- HLS video content plays smoothly via Amazon CloudFront CDN distribution.
- Operational logs across all services are captured in Amazon CloudWatch.


## Workshop Conventions

Primary configuration steps are performed using the AWS Management Console; supporting code snippets and CLI commands are provided where necessary. The AWS Management Console interface and options may evolve; readers should reference current AWS documentation when implementing.


## Documentation Approach

Key configuration steps are illustrated with screenshots captured during implementation when available to assist readers in following along.


## Summary

Section 5.1 presented an overview of the scope, objectives, architecture, service list, and overall workflow of the Serverless Video-on-Demand Platform on AWS. These contents establish a foundational guide before entering detailed configuration steps. Section 5.2 next guides readers through setting up prerequisites and initial environment resources to begin implementation.