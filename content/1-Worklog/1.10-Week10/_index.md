---
title: "Week 10 Worklog"
date: 2024-01-01
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference only, please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}


### Week 10 Objectives:

* Configure Amazon S3 Event Notifications to emit Object Created events to Amazon EventBridge.
* Deploy Amazon SQS Queue and Dead-Letter Queue (DLQ) as a buffer for secure video processing message ingestion.
* Configure Amazon EventBridge Pipes to read messages from SQS and trigger execution pipelines.
* Build automated state orchestration workflows using AWS Step Functions State Machine.
* Integrate the end-to-end automated pipeline from S3 Upload to MediaConvert transcoding and HLS output storage.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | -------------- |
| 3 | - Configure EventBridge Notification feature on S3 Raw Upload Bucket <br> - Analyze event payload structure configuration when new video files are uploaded <br> - Build Event Patterns on EventBridge Bus filtering events precisely by Bucket name and video extension <br> | 23/06/2026 | 23/06/2026 | |
| 4 | - Initialize Amazon SQS queue as a Buffer Queue for the video processing pipeline <br> - Configure Visibility Timeout, Message Retention Period, Long Polling, and Retry Policy parameters <br> - Set up Dead-Letter Queue (DLQ) with Redrive Policy to capture failed messages <br> | 24/06/2026 | 24/06/2026 | |
| 5 | - Configure Amazon EventBridge Pipes as a no-code service integration bridge <br> - Set SQS Queue as Source and AWS Step Functions State Machine as Target <br> - Configure Filtering rules and Input Transformation structures for messages <br> | 25/06/2026 | 25/06/2026 | |
| 6 | - Design and build automated workflows using AWS Step Functions (State Machine) <br> - Define ASL steps: Validate input -> Update DynamoDB (PROCESSING) -> Trigger MediaConvert Job -> Poll status completion -> Update (READY/FAILED) <br> - Implement Retry mechanisms, Catch exception handlers, and idempotent fault handling <br> | 26/06/2026 | 26/06/2026 | |
| 2 | - Connect and integrate full automated End-to-End video processing pipeline <br> - Perform MP4 Upload -> S3 triggers EventBridge -> SQS receives message -> EventBridge Pipe calls Step Functions -> MediaConvert generates HLS -> Write output to S3 Processed -> Update DynamoDB <br> - Test corrupted file upload to verify message routing to SQS DLQ <br> | 29/06/2026 | 29/06/2026 | |


### Week 10 Achievements:

* Successfully established automated event routing from Amazon S3 to Amazon EventBridge.
* Built Amazon SQS queue system combined with Dead-Letter Queue (DLQ) ensuring zero message loss.
* Configured Amazon EventBridge Pipes connecting SQS queues and Step Functions state machines reliably.
* Constructed automated workflow diagrams on AWS Step Functions controlling the entire video transcoding lifecycle.
* Completed automated video pipeline integration from S3 Raw upload to HLS transcoding and database updates.
