---
title: "Week 8 Worklog"
date: 2024-01-01
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference only, please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}


### Week 8 Objectives:

* In-depth research on digital video processing concepts: Distinguish Containers and Codecs, compression standards MP4, H.264, H.265, and AAC.
* Analyze HLS (HTTP Live Streaming) adaptive bitrate streaming mechanisms, Master Playlist structure, Media Playlists, Segments, and Rendition Ladders.
* Research technical architecture of AWS Elemental MediaConvert: Inputs, Output Groups, Job Templates, Queues, and Service Roles.
* Design MediaConvert Job Templates supporting resolutions 1080p, 720p, 480p, video/audio encoding settings, and thumbnail generation.
* Practice manual MediaConvert job execution and testing, evaluate encoded HLS file quality, and record processing metrics.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | -------------- |
| 3 | - Research foundational digital media concepts <br> - Distinguish Containers (MP4, MOV) and Codecs (H.264/AVC, H.265/HEVC, AAC) <br> - Learn parameters affecting video quality: Resolution, Frame rate (FPS), Bitrate (VBR/CBR) <br> | 09/06/2026 | 09/06/2026 | |
| 4 | - Learn HLS (HTTP Live Streaming) streaming standards and Adaptive Bitrate Streaming techniques <br> - Analyze Master Playlist (.m3u8) index file structures, multi-resolution Variant Playlists, and video Segments (.ts/fMP4) <br> - Determine optimal Rendition Ladder for mobile and desktop devices <br> | 10/06/2026 | 10/06/2026 | |
| 5 | - Analyze architecture and components of AWS Elemental MediaConvert <br> - Learn configuration of Inputs, Output Groups, Job Queues, Job Templates, and IAM Execution Roles <br> - Evaluate quota management mechanisms and transcoding cost per video minute <br> | 11/06/2026 | 11/06/2026 | |
| 6 | - Design detailed MediaConvert Job Templates for the Video-on-Demand system <br> - Define output resolution levels: 1080p (Full HD), 720p (HD), and 480p (SD) based on input video <br> - Configure AAC audio encoding, Segment duration (6s), and automated thumbnail extraction <br> | 12/06/2026 | 12/06/2026 | |
| 2 | - Execute trial manual MediaConvert Jobs using sample MP4 video files <br> - Extract and inspect generated HLS output sets: Master Playlist, Variant Playlists, Segment files, and Thumbnails <br> - Record transcoding execution time, output file sizes, and measure actual processing cost <br> | 15/06/2026 | 15/06/2026 | |


### Week 8 Achievements:

* Mastered video compression concepts, H.264/AAC codec standards, and HLS adaptive bitrate streaming mechanisms.
* Understood HLS streaming file structures including Master Playlists, Variant Playlists, and Segment files.
* Mastered AWS Elemental MediaConvert transcoding architecture, including Inputs, Output Groups, and Job Templates.
* Successfully built a standardized Job Template transcoding video into 3 resolution levels (1080p, 720p, 480p) with thumbnail generation.
* Successfully transcoded sample MP4 video files into HLS format and verified video playback quality.
