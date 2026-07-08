---
title: "Week 2 Worklog"
date: 2026-05-02
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference only, please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}


### Week 2 Objectives:

- Learn Amazon VPC and foundational networking components on AWS.
- Understand how to design subnets, route tables, Internet Gateways, and NAT Gateways.
- Grasp the roles of Security Groups and Network ACLs in network security.
- Practice creating VPCs, subnets, route tables, Internet Gateways, NAT Gateways, and deploying EC2 instances in subnets.
- Learn about Hybrid DNS with Route 53 Resolver.
- Practice VPC Peering and Transit Gateway to connect multiple VPCs.
- Know how to verify connectivity, configure routes, and clean up resources after labs.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date |
| --- | --- | --- | --- |
| Friday | Learn about Amazon VPC, subnets, route tables, Internet Gateways, and practice the first part of Lab03 | 24/04/2026 | 24/04/2026 |
| Monday | Learn about VPC Security, NAT Gateways, Security Groups, Network ACLs, and complete Lab03 | 27/04/2026 | 27/04/2026 |
| Tuesday | Learn about Hybrid DNS, VPN/Direct Connect concepts, and practice Lab10 with Route 53 Resolver | 28/04/2026 | 28/04/2026 |
| Wednesday | Learn about Multi-VPC features and practice Lab19 with VPC Peering, route tables, NACLs, and Cross-Peer DNS | 29/04/2026 | 29/04/2026 |
| Thursday | Learn about Transit Gateways, Load Balancers, and related extra resources, and practice Lab20 | 30/04/2026 | 30/04/2026 |

### Week 2 Achievements:

- Understood the role of Amazon VPC in creating virtual private networks on AWS.
- Differentiated public and private subnets in the VPC model.
- Understood the role of route tables in directing traffic between subnets and to the Internet.
- Configured an Internet Gateway to allow resources in a public subnet to access the Internet.
- Configured a NAT Gateway to allow outbound Internet access for resources in a private subnet.
- Differentiated between Security Groups and Network ACLs in terms of scope, operations, and purpose.
- Created a VPC, subnets, route tables, Internet Gateways, security groups, and EC2 instances per Lab03 requirements.
- Verified connectivity between EC2 instances within subnets and outbound Internet connectivity based on route configurations.
- Utilized the VPC Resource Map to visualize the created network components in the VPC.
- Got familiar with EC2 Instance Connect Endpoints when connecting to EC2 instances.
- Understood the concept of Site-to-Site VPN and its role in connecting on-premises environments to AWS.
- Understood the concept of AWS Direct Connect and its role in establishing dedicated network connections to AWS.
- Understood the basic role of Load Balancers in distributing traffic across multiple backend resources.
- Understood the Hybrid DNS model with Route 53 Resolver.
- Created key pairs and used CloudFormation templates to prepare the lab environment.
- Configured Security Groups to allow connections to lab resources.
- Connected to the RDGW instance according to Lab10 instructions.
- Created Route 53 Outbound Endpoints, Resolver Rules, and Inbound Endpoints as required.
- Tested and verified DNS resolution results within the Hybrid DNS model.
- Understood how VPC Peering connects two VPCs together.
- Created VPC Peering connections according to Lab19 instructions.
- Configured route tables to allow communication between VPCs over VPC Peering.
- Updated Network ACLs to allow appropriate traffic in the peering architecture.
- Enabled Cross-Peer DNS support to resolve DNS queries across peered VPCs.
- Understood the role of AWS Transit Gateway in multi-VPC connectivity.
- Created a Transit Gateway, Transit Gateway Attachments, and Transit Gateway Route Tables according to Lab20 instructions.
- Added routes to VPC route tables to route traffic via Transit Gateway.
- Verified network connectivity after configuring VPC Peering and Transit Gateway.
- Cleaned up resources after each lab to prevent unnecessary costs.
- Successfully completed the main labs for Week 2, including Lab03, Lab10, Lab19, and Lab20.
