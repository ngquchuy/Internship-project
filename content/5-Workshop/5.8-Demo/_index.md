---
title: "Demo"
date: 2026-07-20
weight: 8
chapter: false
pre: "<b>5.8. </b>"
---

# System Demo

## Overview

After completing the implementation and testing steps, the demo video illustrates the operational workflow of the **Serverless Video-on-Demand Platform on AWS** within the MVP scope. The content demonstrates the workflow from when a user uploads a video until it is transcoded and ready for playback on the web application.

## Demo Content

The video demonstrates the key steps of the system according to the deployed architecture, including:

- Logging into the system.
- Uploading a video via the web application.
- Checking raw source videos in Amazon S3 Raw Upload Bucket.
- Monitoring AWS Elemental MediaConvert executing video transcoding.
- Checking output assets in Amazon S3 Processed Media Bucket.
- Verifying metadata and processing status in Amazon DynamoDB.
- Playing back video on the web application after processing completes.

## Video Demo

👉 Attached documents including Video Demo and Source Code:

https://drive.google.com/drive/folders/1rPrD49VZEmlGYVUGhIUE2riv0jqQ93_J?usp=sharing

The Google Drive folder includes:

- 📄 Source code of the web application in the Workshop.
- 🎥 Demonstration video illustrating the system operational workflow.

## Results

The demo video shows that core system features operate continuously along the designed workflow. Once a video is uploaded, the processing pipeline triggers, AWS Elemental MediaConvert generates output assets, metadata updates, and the video can be played back via the web application.

The demo results serve as evidence of integrating key architectural components within the MVP scope. Detailed evaluations regarding performance, load handling, and costs require separate testing scenarios.
