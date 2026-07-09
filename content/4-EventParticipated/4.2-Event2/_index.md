---
title: "Event 2"
date: 2026-06-27
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

# Reflection on “FCAJ Community Day - Data Driven, AI Risen”

### Event Information

- **Event name:** FCAJ Community Day
- **Theme:** Data Driven, AI Risen
- **Time:** 09:00 AM - 12:00 PM, June 27, 2026
- **Location:** Floor 26, Bitexco Financial Tower, 2 Hai Trieu Street, Saigon Ward, Ho Chi Minh City
- **Role in the event:** Participant

### Purpose of the Event

- To create an opportunity for members of the First Cloud AI Journey community and people interested in AWS, Cloud, and AI to connect.
- To share practical perspectives on how AI is developing in enterprise environments, especially in areas such as data, voice AI, DevOps AI Agents, Amazon Q, and system security.
- To help participants better understand how companies are using AI to automate processes, optimize operations, and support decision-making.
- To give students a practical view of the job market, career paths in Cloud/AI, and the skills required in the current technology landscape.
- To inspire participants to learn proactively, build personal projects, and gain real-world experience early.

### Speakers

- **Truong Tran** - AI Solution Sales, Noventiq
- **Steve Tran** - CTO/Founder, CloudThinker
- **Trung Vu** - CEO, Revve AI
- **Anh Dang** - Solution Sales, Noventiq
- **Nghi Danh** - AI Engineer, Renova Cloud
- **Kiet Tran** - AI Engineer, AWS Student Builder Group
- **Bao Phan** - Cloud Engineer, Cloud Kinetics
- **Nguyen Nguyen** - Cloud Engineer, Cloud Kinetics
- **Toan Nguyen** - AWS Security Builder

### Highlighted Content

#### Career Path and Cloud Agentic Platform

One of the notable sessions focused on career paths in Cloud Engineering and how AI is affecting the technology job market. The speaker shared that as companies increasingly apply AI in their operations, students and junior developers need to improve their practical skills and learn how to use AI as a tool to support their work instead of relying only on theoretical knowledge.

This session helped me gain a clearer view of how to build a career path in Cloud/AI. To become more competitive, learners should gain experience early through internships, personal projects, community activities, or startup environments. In addition to technical skills, problem-solving ability, system thinking, and the ability to use AI to improve productivity are becoming increasingly important.

The session also introduced the idea of a **Cloud Agentic Platform**, an approach that uses AI Agents to support humans in tasks such as incident handling, code review, cloud cost optimization, security support, and DevOps simplification. A key point is that AI does not fully replace engineers; instead, it acts as an assistant that helps reduce response time and improve system visibility.

#### Voice AI / Voice Agent in Enterprise Environments

Another important topic was **Voice AI** and **Voice Agents**. The speaker introduced a common voice AI architecture consisting of three main components: Speech-to-Text, LLM, and Text-to-Speech. With this architecture, a user’s voice is converted into text, then processed by an LLM, and finally converted back into spoken responses.

Through this session, I understood that building a real-world Voice Bot is much more complex than creating a simple demo. For Vietnamese, the challenge is even greater because speech data is still limited and there are many regional accents, tones, and forms of address. Therefore, the system needs to handle issues such as latency, conversation context, interruption handling, gender-based addressing, and smooth handover to human agents when AI cannot solve the problem.

The event also included a Voice Agent demo using AWS Bedrock and Knowledge Base to answer questions with context. This demo helped me better imagine how voice interfaces can be combined with Generative AI to create an assistant that interacts naturally with users.

#### DevOps AI Agent for Monitoring and Incident Response

The session about **DevOps AI Agent** focused on monitoring, investigation, and incident response in cloud systems. The speakers analyzed a familiar DevOps problem: when a system fails, logs, metrics, and traces are often scattered across many tools, making root cause investigation time-consuming and increasing MTTR.

The DevOps AI Agent was presented as an assistant that can support engineers during incident response. The agent can receive alerts, analyze logs and metrics, understand system topology, generate hypotheses about possible causes, identify root causes, and suggest remediation steps. However, the system still follows the **Human-in-the-loop** principle, meaning AI supports analysis and recommendations while the final decision remains with humans.

In the demo, the speakers simulated an incident related to unusual traffic on an e-commerce application. The agent helped detect bottlenecks, analyze possible issues around the load balancer or backend services, and suggest remediation directions for engineers to review. This showed me the potential of AI to reduce investigation time and help DevOps engineers work more efficiently.

#### Amazon Q in HR Workflow

Another session focused on applying **Amazon Q** to human resources workflows, especially recruitment. The speakers mentioned several common HR challenges, such as time-consuming manual CV screening, inconsistent candidate evaluation, difficulty in standardizing criteria, and data security risks when using public AI tools without proper control.

Amazon Q was introduced as an AI assistant that can help transform user questions or requests into practical tasks. In the recruitment context, it can support job description creation, candidate CV analysis, scoring based on criteria, candidate classification, and evaluation report generation.

Through the demo, I realized that AI can optimize repetitive internal workflows, especially tasks that require reading, summarizing, and comparing many documents. However, with sensitive data such as CVs or candidate information, companies need to pay attention to access control, data protection, and how AI uses the provided information.

#### Private Security Between Amazon Q and Internal MCP Server

The security session focused on the problem of connecting an AI assistant to internal enterprise data systems. If an AI assistant needs to access an MCP Server or internal services through public endpoints, the system may face risks such as attacks, data leakage, and uncontrolled traffic exposure.

The speaker proposed a more secure approach by placing internal components inside private subnets, using private connectivity within AWS, private load balancers, TLS encryption, and Route 53 Resolver for internal DNS resolution. This approach helps reduce the need for data to travel through the public internet and improves access control between Amazon Q and internal systems.

From this session, I learned that when bringing AI into enterprise environments, security should not be added at the end. It needs to be designed from the beginning. An AI system may be powerful in terms of features, but without network isolation, access control, encryption, and logging, it will be difficult to meet production requirements.

### What I Learned

#### Cloud/AI Career Trends

- I gained a better understanding of how the job market is changing as AI becomes more widely adopted in enterprises.
- I realized that students and junior developers need to gain practical experience early through projects, internships, hackathons, or community activities.
- I learned that the ability to use AI to support work is becoming an important advantage.
- I understood that developing in the Cloud/AI field requires a combination of fundamentals, hands-on skills, and problem-solving thinking.
- I became more motivated to build a personal portfolio instead of only studying theory.

#### Voice AI

- I understood the basic architecture of a Voice AI system, including Speech-to-Text, LLM, and Text-to-Speech.
- I realized that Vietnamese voice AI is challenging because of regional accents, tones, and forms of address.
- I learned about real-world challenges in building Voice Bots, such as latency, interruption handling, response control, and handover to human agents.
- I understood how Knowledge Base and LLMs can help Voice Agents answer questions with context.
- I gained more perspective on applying Voice AI in banking, customer service, and enterprise processes.

#### DevOps AI Agent

- I understood the role of AI Agents in monitoring and incident response.
- I learned that when a system fails, AI can help analyze logs, metrics, traces, and topology to reduce investigation time.
- I understood the concept of Root Cause Analysis and how AI can suggest possible root causes.
- I realized that the Human-in-the-loop principle is very important in operations because AI should support humans instead of making uncontrolled changes in production.
- I gained a clearer view of how AI can help reduce MTTR and support DevOps engineers during incidents.

#### Amazon Q and Enterprise Automation

- I understood how Amazon Q can support internal workflows such as HR, recruitment, and CV evaluation.
- I learned that AI can automate repetitive tasks such as creating job descriptions, reading CVs, comparing candidates, and generating reports.
- I realized that using AI in enterprises must go together with data security and access control.
- I gained more perspective on how companies can use AI assistants to improve operational efficiency.
- I understood that AI is not only for answering questions; it can also help execute specific workflows.

#### AI System Security

- I understood the risks of connecting an AI assistant to internal systems through public endpoints.
- I learned how private subnets, private load balancers, VPC connections, TLS, and Route 53 Resolver can help protect systems.
- I realized that network isolation and access control are important when deploying AI in enterprise environments.
- I understood that security should be designed from the beginning, especially for systems that handle sensitive data.
- I gained a better view of building AI systems in a production-ready way instead of stopping at demos.

### Application to My Study and Work

- When studying or building personal projects, I should focus on real-world problems instead of only simple demos.
- I can use AI to support learning, report writing, document analysis, and automation of repetitive tasks.
- When building my portfolio, I should clearly show problem-solving ability, system design thinking, and practical use cases involving cloud/AI.
- I can use the Voice Agent idea as a reference for projects related to chatbots, voice bots, or customer support assistant.
- I can apply knowledge about DevOps AI Agents to monitoring, logging, alerting, or incident response projects.
- When using AI in applications that handle sensitive data, I need to care about security, authorization, logging, and how data moves between systems.
- I can improve my CV by making it clear, including relevant keywords from job descriptions, and highlighting practical projects.
- I should continue joining community events, workshops, and hackathons to learn from people with real-world experience.

### Experience in the Event

Participating in **FCAJ Community Day - Data Driven, AI Risen** was a very valuable experience for me. Compared with only learning through videos or documents, the event gave me access to more practical perspectives from people working in Cloud, AI, DevOps, and Security.

What impressed me most was that the sessions were connected to specific enterprise problems. Topics such as Voice AI, DevOps AI Agents, Amazon Q for HR workflows, and private security were not only theoretical; they showed how AI is being applied in real operations.

Through the event, I realized that AI is not simply a content generation tool or a chatbot for answering questions. When combined with data, cloud infrastructure, and business processes, AI can become an assistant that supports operations, analysis, automation, and decision-making. However, to deploy it effectively, the system still needs human control, strong security, and a suitable architecture.

The event also helped me see my own development direction more clearly. As an information technology student, I need to keep learning AWS, backend, DevOps, AI, and security, while also building practical projects to prove my abilities. This was a meaningful activity during my internship because it connected what I learned in the program with real-world enterprise problems.

#### Some photos from the event

* Add my photos from the event here.

> Overall, FCAJ Community Day - Data Driven, AI Risen helped me broaden my view of how data, AI, and cloud are changing the way businesses operate. The event provided practical knowledge and gave me clearer direction for learning, building my portfolio, and developing my final project.
