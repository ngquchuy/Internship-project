---
title: "Blogs Posted"
date: 2026-06-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}}

This section lists and introduces the blogs I posted during my internship, mainly related to AWS, Cloud Computing, Backend, Database, and Generative AI.

### [Blog 1 - USER AUTHENTICATION AND SESSION MANAGEMENT WITH AMAZON AURORA DSQL](3.1-Blog1/)

This blog introduces how to build a user authentication and session management system with Amazon Aurora DSQL. The content focuses on backend authentication in an environment that requires scalability, strong consistency, and better security. The solution uses Aurora DSQL together with Amazon ECS, AWS Fargate, and IAM authentication to build a modern authentication service, reduce manual database instance management, and lower the risks when handling sensitive information such as passwords and session tokens.

### [Blog 2 - FROM MONOLITH TO MULTI-ACCOUNT: PINTEREST'S AWS ORGANIZATIONS TRANSFORMATION JOURNEY](3.2-Blog2/)

This blog presents Pinterest's journey transitioning from a monolithic AWS account model to a Multi-Account strategy. The content focuses on AWS Organizations, AWS Control Tower, AWS IAM Identity Center, Organizational Units, Service Control Policies, and centralized governance to reduce Blast Radius, limit Service Quotas, and improve cost allocation.

### [Blog 3 - LESSONS FROM SCALING TO 1 MILLION AWS LAMBDA FUNCTIONS](3.3-Blog3/)

This blog presents architectural lessons when scaling a Serverless system to a very large scale. The content focuses on combining AWS Lambda, Amazon SQS, and AWS Step Functions for asynchronous processing, concurrency control, throttling prevention, cold start reduction, and building fault-tolerant mechanisms using Dead-Letter Queues.