---
title: "Blog 2"
date: 2026-06-01
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

{{% notice warning %}}
⚠️ **Note:** The information below is a summary of the blog post I read and published during my internship, and is not an official document replacing the original AWS article.
{{% /notice %}}

# FROM MONOLITH TO MULTI-ACCOUNT: PINTEREST'S AWS ORGANIZATIONS TRANSFORMATION JOURNEY

As system scale expands with business growth, maintaining a Monolith Account Architecture quickly turns into a operational and security challenge. This article deep-dives into Pinterest's infrastructure transformation on the AWS Blog, exploring how they transitioned from a monolithic account setup to a large-scale Multi-Account strategy.

━━━━━━━━━━━━━━━

## Pain Points of the Old Architecture and Reasons for Migration

Before this transformation, Pinterest operated with a minimal number of AWS accounts containing vast amounts of resources. This led to three major challenges:

- **Security Risks and Excessive Blast Radius:** A minor configuration error in Development risked impacting Production systems due to shared VPC networks or accounts.
- **API Rate Limits and AWS Service Quotas Exhaustion:** At scale, automated scripts and monitoring tools calling AWS Core Services APIs caused widespread throttling.
- **Lack of Cost Visibility and Allocation:** Finance teams struggled to accurately attribute overall AWS billings to specific microservices or engineering teams.

━━━━━━━━━━━━━━━

## New Architectural Solution: AWS Governance Trio

Pinterest deployed a core AWS solution trio: AWS Organizations + AWS Control Tower + AWS IAM Identity Center.

Instead of pooling workloads together, they decomposed the system into a structured hierarchy via Organizational Units (OUs):

━━━━━━━━━━━━━━━

## Organizational Units Structure

| Organizational Unit (OU) | Role in System | Governance Mechanism |
| --- | --- | --- |
| OU Core Infrastructure | Isolates shared platform services | Manages Shared VPCs, Networking Core, and Centralized Registry |
| OU Business Units (Products) | Divided by feature teams (Home Feed, Search, Ads) | Each team owns 3 isolated accounts: Dev, Staging, and Prod |
| OU Security & Governance | Auditing and security management | Contains Log Archive and Audit accounts |

━━━━━━━━━━━━━━━

## Cost Optimization & Operational Performance Strategy

Pinterest implemented Service Control Policies (SCPs):

- **Resource Control in Dev and Staging:** Prevents creation of expensive EC2 instances (P-series or X-series) without prior approval.
- **Centralized Log Aggregation:** Log data from CloudTrail, CloudWatch, and GuardDuty is compressed and shipped asynchronously to a secure central Data Lake.

━━━━━━━━━━━━━━━

## Four Core Technical Takeaways for Cloud Engineers

### 1. Establish a Standard Landing Zone Early

Use AWS Control Tower to automate Account Factory processes. When a new team requires resources, the system automatically provisions a clean AWS Account with built-in guardrails.

### 2. Apply Service Control Policies Proactively

Use SCPs to enforce top-level infrastructure guardrails and restrict allowed AWS Regions to minimize Blast Radius.

### 3. Centralized Identity Governance with IAM Identity Center

Replace long-lived access keys and manual IAM users with enterprise Single Sign-On (SSO) and temporary credentials.

### 4. Cost Attribution via Strict Tagging Strategies

Pair Multi-Account architecture with mandatory Tagging policies (CostCenter, Environment, Owner) enforced via AWS Config and Lambda automation.

━━━━━━━━━━━━━━━

## References and Community Discussion

Multi-Account architecture via AWS Organizations is an essential prerequisite for hyper-scale systems.

━━━━━━━━━━━━━━━

## Original Article Link

AWS Cloud Operations Blog:  
https://aws.amazon.com/vi/blogs/mt/from-monolith-to-multi-account-pinterests-aws-organization-transformation-journey/

AWS Study Group:  
https://www.facebook.com/groups/awsstudygroupfcj/permalink/2200922960672664/

## Images