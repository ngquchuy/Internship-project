---
title: "Week 11 Worklog"
date: 2024-01-01
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference only, please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}


### Week 11 Objectives:

* Standardize HLS output storage folder structures and configure Metadata/Content-Type on S3 Processed Media Buckets.
* Configure Amazon CloudFront Content Delivery Network combined with Origin Access Control (OAC) securing S3 data.
* Research HLS video content protection mechanisms using CloudFront Signed URLs / Signed Cookies.
* Deploy AWS WAF web application firewall configuring Rate-based and Managed Rules protecting CloudFront.
* Integrate Frontend UI with Cognito, API Gateway, Lambda, DynamoDB, and HLS Player for End-to-End testing.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | -------------- |
| 3 | - Standardize output directory planning on Amazon S3 Processed Media Bucket <br> - Categorize storage: Master Playlist (.m3u8), Variant Playlists, Segment files (.ts), and Thumbnail images (.jpg) <br> - Build automated Content-Type and Cache-Control header attachment mechanism for each file extension <br> | 30/06/2026 | 30/06/2026 | |
| 4 | - Configure Amazon CloudFront CDN service for Frontend and HLS media content delivery <br> - Configure Origin Access Control (OAC) disabling direct Internet access to S3 Buckets <br> - Configure Cache Behavior policies optimized for static assets, playlist files, and video segment files <br> | 01/07/2026 | 01/07/2026 | |
| 5 | - Research and compare HLS video streaming security solutions against unauthorized access <br> - Compare pros & cons of CloudFront Signed URLs vs. CloudFront Signed Cookies for HLS playback <br> - Test time-expiring signed URL generation for video stream playback <br> | 02/07/2026 | 02/07/2026 | |
| 6 | - Deploy AWS WAF (Web ACL) application firewall protecting Edge layer <br> - Configure AWS Managed Rules (Common Rule Set) and Rate-based request limiting rules <br> - Attach Web ACL to CloudFront Distribution and inspect Sampled Requests / Monitoring metrics <br> | 03/07/2026 | 03/07/2026 | |
| 2 | - Complete Frontend web application UI integration with full AWS Backend infrastructure <br> - Connect Cognito Login -> Fetch Movie List via API Gateway -> Upload Video -> Track Status -> HLS Player playback <br> - Test load handling and synchronization between CloudFront, API Gateway, and Lambda <br> | 06/07/2026 | 06/07/2026 | |


### Week 11 Achievements:

* Standardized storage directory structure and automated Content-Type/Cache-Control header tagging for HLS files on S3.
* Configured high-speed content delivery via Amazon CloudFront combined with OAC securing S3 Buckets completely.
* Successfully tested secure HLS video access authorization using Signed URLs.
* Deployed AWS WAF configuring Managed Rules and Rate-limiting protecting against DDoS/Web attacks.
* Successfully integrated complete system between Frontend web, Cognito, API Gateway, Lambda, and HLS Player.
