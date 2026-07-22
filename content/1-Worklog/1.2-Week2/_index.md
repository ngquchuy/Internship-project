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

- Learn about Amazon VPC and foundational networking components on AWS.
- Understand how to design subnets, route tables, Internet Gateways, and NAT Gateways.
- Grasp the role of Security Groups and Network ACLs in network security.
- Practice creating VPCs, subnets, route tables, Internet Gateways, NAT Gateways, and EC2 instances in subnets.
- Learn about Hybrid DNS with Route 53 Resolver.
- Practice VPC Peering and Transit Gateway to connect multiple VPCs.
- Know how to verify connectivity, configure routes, and clean up resources after labs.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 6 | Learn about Amazon VPC, subnets, route tables, Internet Gateways, and practice the first part of Lab03 | 24/04/2026 | 24/04/2026 | <https://000003.awsstudygroup.com/> |
| 2 | Learn about VPC Security, NAT Gateways, Security Groups, Network ACLs, and complete Lab03 | 27/04/2026 | 27/04/2026 | <https://000003.awsstudygroup.com/> |
| 3 | Learn about Hybrid DNS, VPN/Direct Connect at a conceptual level, and practice Lab10 with Route 53 Resolver | 28/04/2026 | 28/04/2026 | <https://000003.awsstudygroup.com/> |
| 4 | Learn about Multi-VPC features and practice Lab19 with VPC Peering, route tables, NACLs, and Cross-Peer DNS | 29/04/2026 | 29/04/2026 | <https://000003.awsstudygroup.com/> |
| 5 | Learn about Transit Gateway, Load Balancers/extra resources at an overview level, and practice Lab20 | 30/04/2026 | 30/04/2026 | <https://000003.awsstudygroup.com/> |

### Week 2 Achievements:

- Grasped the role of Amazon VPC in creating virtual private networks on AWS.
- Differentiated public subnets and private subnets in the VPC model.
- Understood the role of route tables in directing traffic between subnets and to the Internet.
- Configured Internet Gateways to allow resources in public subnets to access the Internet.
- Configured NAT Gateways to support resources in private subnets to access the Internet outbound.
- Differentiated Security Groups and Network ACLs regarding scope, operation, and usage purpose.
- Created VPCs, subnets, route tables, Internet Gateways, security groups, and EC2 instances as required in Lab03.
- Tested connectivity between EC2 instances in subnets and Internet access according to route configuration.
- Used VPC Resource Map to observe network components created in the VPC.
- Became familiar with EC2 Instance Connect Endpoints when connecting to EC2 instances.
- Grasped Site-to-Site VPN concepts and the role of VPN in connecting on-premises environments with AWS.
- Grasped Direct Connect concepts and the role of Direct Connect in dedicated network connections to AWS.
- Understood the basic role of Load Balancers in distributing traffic to backend resources.
- Understood the Hybrid DNS model with Route 53 Resolver.
- Created key pairs and used CloudFormation templates during lab environment preparation.
- Configured Security Groups for connecting to lab resources.
- Connected to RDGW according to Lab10 content.
- Created Route 53 Outbound Endpoints, Resolver Rules, and Inbound Endpoints as required by the lab.
- Verified DNS resolution results in the Hybrid DNS model.
- Grasped how to use VPC Peering to connect two VPCs.
- Created peering connections between VPCs according to Lab19 content.
- Configured route tables for VPCs to communicate via VPC Peering.
- Updated Network ACLs to allow appropriate traffic in the connection model.
- Enabled Cross-Peer DNS to support DNS resolution between peered VPCs.
- Grasped the role of AWS Transit Gateway in multi-VPC connection models.
- Created Transit Gateways, Transit Gateway Attachments, and Transit Gateway Route Tables according to Lab20.
- Added routes to VPC route tables to direct traffic through Transit Gateway.
- Knew how to test connectivity after configuring VPC Peering and Transit Gateway.
- Cleaned up resources after labs to limit unnecessary cost generation.
- Completed major labs in Week 2 including Lab03, Lab10, Lab19, and Lab20.
