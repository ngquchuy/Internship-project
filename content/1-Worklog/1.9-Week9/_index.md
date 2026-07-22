---
title: "Week 9 Worklog"
date: 2024-01-01
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference only, please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}


### Week 9 Objectives:

* Configure Amazon Cognito User Pool identity management, set up App Clients and JWT authentication mechanisms.
* Design API Gateway REST/HTTP APIs, map Resource Routes, configure CORS and JWT Authorizers.
* Build Serverless Backend applications with AWS Lambda for core movie and user management business tasks.
* Design data models on Amazon DynamoDB optimized for VOD Access Patterns.
* Implement Presigned Upload URL generation enabling Clients to upload video directly and securely into S3 Raw Upload Buckets.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | -------------- |
| 3 | - Configure Amazon Cognito User Pool for managing application users <br> - Set up App Clients, configure Registration, Login, Logout, and Email Verification flows <br> - Learn structures and validation mechanisms for ID Tokens, Access Tokens, and Refresh Tokens <br> | 16/06/2026 | 16/06/2026 | |
| 4 | - Design Amazon API Gateway architecture for system business APIs <br> - Define Routes, Methods (GET, POST, PUT, DELETE), Request/Response parameters, and JSON schemas <br> - Configure Cognito JWT Authorizer to protect APIs and enable CORS sharing <br> | 17/06/2026 | 17/06/2026 | |
| 5 | - Develop core business AWS Lambda functions using Node.js/Python <br> - Write code for movie listing, movie details, post creation, and video processing status updates <br> - Standardize Exception Handling workflows and Response formatting <br> | 18/06/2026 | 18/06/2026 | |
| 6 | - Design Amazon DynamoDB data models based on Access Patterns <br> - Create `Movies` table storing: movieId, title, status, rawS3Key, hlsPath, createdAt, updatedAt <br> - Configure Partition Key, Sort Key, and implement CRUD operations from Lambda via AWS SDK <br> | 19/06/2026 | 19/06/2026 | |
| 2 | - Build Lambda API generating Presigned Upload URLs for Amazon S3 <br> - Validate file types (Video/MP4), file size limits, and generate S3 Raw Object Key paths <br> - Test flow integration: Login -> Get JWT -> Call Presigned URL API -> Direct Video Upload to S3 <br> | 22/06/2026 | 22/06/2026 | |


### Week 9 Achievements:

* Successfully initialized and configured Amazon Cognito User Pool allowing secure user authentication with JWT Tokens.
* Built API Gateway infrastructure protected by Cognito JWT Authorizer with complete CORS configuration.
* Completed AWS Lambda functions for movie catalog management and video processing status updates.
* Designed DynamoDB tables storing movie metadata optimized for system read/write operations.
* Successfully implemented S3 Presigned URL generation allowing Clients to upload video files directly to S3 Raw Buckets.
