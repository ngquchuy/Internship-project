---
title: "Week 7 Worklog"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference only, please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}


### Week 7 Objectives:

* Research the Video-on-Demand (VOD) system domain and define complete business requirements, actors, and core use cases.
* Analyze non-functional requirements including scalability, availability, performance, security, and operational cost optimization.
* Analyze and map service responsibilities for each architectural layer in the Serverless Architecture model.
* Design detailed sequence flows for key business workflows: Login, Video Upload, HLS Transcoding, and Playback.
* Review overall system architecture, draft the Architecture Decision Record (ADR), and build the implementation backlog for Weeks 8–12.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | -------------- |
| 3 | - Analyze Video-on-Demand movie streaming platform problem statement <br> - Identify actors (User, Admin) and main use case diagrams <br> - Define MVP scope: Authentication, movie catalog, video upload, automated video processing, and HLS playback <br> | 02/06/2026 | 02/06/2026 | |
| 4 | - Analyze non-functional requirements for the movie streaming system <br> - Define metrics for scalability, availability, video streaming performance (latency/throughput), data security, and observability <br> - Estimate initial operational budget optimized with AWS Serverless <br> | 03/06/2026 | 03/06/2026 | |
| 5 | - Analyze service responsibilities for each layer in the architecture <br> - Define roles of Cognito (Identity), CloudFront (Edge), API Gateway & Lambda (Application), DynamoDB & S3 (Data), EventBridge/SQS/Step Functions (Event & Pipeline), MediaConvert (Transcoding), and CloudWatch (Observability) <br> | 04/06/2026 | 04/06/2026 | |
| 6 | - Design detailed Sequence Flows for 4 main workflows: Authentication/API calls, Direct Video Upload, Multi-resolution Transcoding, and HLS Playback <br> - Analyze trust boundaries and data flow across each service <br> | 05/06/2026 | 05/06/2026 | |
| 2 | - Review overall Video-on-Demand architecture <br> - Evaluate pros & cons of the Serverless model and identify potential Single Points of Failure <br> - Write Architecture Decision Record (ADR) report and allocate detailed implementation backlog for Weeks 8–12 <br> | 08/06/2026 | 08/06/2026 | |


### Week 7 Achievements:

* Clearly defined actors, use cases, and MVP feature scope for the Video-on-Demand platform.
* Built a complete set of non-functional criteria regarding performance, reliability, and cost optimization for the Serverless model.
* Completed Service Responsibility mapping between Cognito, API Gateway, Lambda, S3, MediaConvert, and CloudFront.
* Designed detailed Data Flow and Sequence Diagrams for core business workflows.
* Finalized the Architecture Decision Record (ADR) establishing the Serverless VOD architecture and implementation backlog for the next 5 weeks.
