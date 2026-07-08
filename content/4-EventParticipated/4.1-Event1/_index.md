---
title: "Event 1"
date: 2026-05-23
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy it verbatim** into your report, including this warning.
{{% /notice %}}

# Reflection on “FCAJ Community Day”

### Event Information

- **Event name:** FCAJ Community Day
- **Time:** 09:00 AM - 12:00 PM, May 23, 2026
- **Location:** Floor 26, Bitexco Financial Tower
- **Role in the event:** Participant

### Purpose of the Event

- To create an opportunity for members of the First Cloud AI Journey community to connect and exchange knowledge.
- To share practical knowledge about AWS, Generative AI, Amazon CloudFront, multi-agent systems, and AI applications in enterprise environments.
- To help participants understand how AWS technologies are applied to real-world problems.
- To inspire students and beginners to build personal projects, join hackathons, and improve their cloud/AI skills.
- To provide practical perspectives from speakers working in cloud, DevOps, AI, platform engineering, and business systems.

### Speakers

- **Tinh Truong** - Platform Engineer, GoTymeX
- **Pham Ng Hai Anh** - G-AsiaPacific Vietnam, AWS Community Builder
- **Nguyen Tuan Thinh** - DevOps Engineer, First Cloud AI Journey
- **Duc Dao** - Solution Architect, Cloud Kinetics
- **Vy Lam** - Senior Business Systems Analyst, VPBank
- **Team UTMorpho** - Sharing the journey of building a product at LotusHacks 2026

### Highlighted Content

#### Context Is Everything - GenAIOps Essential

This session focused on the importance of context when working with AI. The speaker emphasized that modern AI models are already powerful, but poor results often come from insufficient, unclear, or irrelevant context.

The session helped me understand that an effective prompt should include a clear goal, situation, constraints, relevant information, and success criteria. Without these elements, AI can easily produce generic answers, go in the wrong direction, or miss important requirements.

The talk also introduced the evolution from Prompt to Context to Memory, showing that AI usage is moving from isolated question-answer interactions toward systems that can store, retrieve, and use relevant context over time.

#### Automate Any Business Process Using Amazon Quick Suite

The session about Amazon Quick Suite focused on automating business processes in enterprise environments. The speaker presented a common problem: business users often need to gather and analyze information from many sources while repeating time-consuming manual tasks.

Amazon Quick Suite was introduced as a platform for agentic AI, capable of connecting enterprise data, user-uploaded files, databases, data warehouses, web search, and third-party applications. It can support tasks such as chat, research, BI dashboards, automation flows, and insight generation.

One notable use case was a PM assistant that can automatically create meeting minutes, send emails to stakeholders, and schedule the next meeting. From this session, I learned that AI in business is not limited to chatbots; it can become an assistant that supports operations and automates real workflows.

#### CloudFront as Your Foundation

The Amazon CloudFront session gave me a broader view of AWS CDN services. Before this event, I mainly understood CloudFront as a caching and content delivery service. However, this session presented CloudFront as a foundation for cost optimization, security, resiliency, and performance.

The speaker analyzed the challenges of the pay-as-you-go model, especially when traffic spikes unexpectedly, content goes viral, or an application faces DDoS attacks. The session also introduced flat-rate pricing as a way to make CDN costs more predictable.

In addition to cost optimization, the session covered AWS Global Edge Network, AWS WAF, AWS Shield, DDoS mitigation, HTTPS/TLS, Mutual TLS, Origin Access Control, Signed URL, geographic restriction, origin failover, HTTP/3, compression, and edge logic with CloudFront Functions or Lambda@Edge.

#### UTMorpho - Building from Idea to Reality

The UTMorpho session shared the journey of building a product during LotusHacks 2026. The team started without a clear idea, brainstormed multiple directions, and eventually found a problem from their own daily working experience.

UTMorpho came from a limitation of AI UI generators: they can generate an interface from a prompt, but editing details such as color, spacing, text, or layout often requires re-prompting, which can unintentionally change the original design. To solve this, the team built an agent that can generate UI and allow direct editing on the canvas in a WYSIWYG style.

From this story, I learned that a strong product idea can come from a real pain point. The session also showed that when building a product in a short period, a team needs to split tasks effectively, focus on the demo path, cut unnecessary features, and treat token usage as a design constraint.

#### Non-Determinism of “Deterministic” LLM Settings

This session helped me understand more deeply how LLMs generate outputs. The speaker explained that LLMs generate text token by token. At each step, the model produces logits, converts them into probabilities with softmax, and chooses the next token.

A key point was that many people assume temperature = 0 always produces identical outputs. However, the presentation showed that in reality, LLM outputs can still vary even when the prompt, seed, and settings are the same.

The causes include floating-point arithmetic on GPUs, parallel computation order, and inference batching on managed endpoints. This is especially important for production systems and sensitive domains such as healthcare, legal research, and financial analysis, where stability and testability are critical.

#### Enterprise-Grade Multi-Agent System

The final session discussed Enterprise-Grade Multi-Agent Systems through a startup credit scoring case study. The speaker explained that traditional credit scoring systems are usually designed for established businesses, but they struggle with startups because startup data is short-term, unstructured, and often lacks credit history or traditional collateral.

The presentation compared single-agent and multi-agent approaches. For problems involving multiple domains, many constraints, audit requirements, and high risk, a multi-agent system is more suitable because each agent can take on a specialized role such as Financial Analyst, Market Analyst, Team Evaluator, Risk Assessor, or Compliance.

The session also emphasized that enterprise AI systems should not only work as demos. They need security, data governance, network isolation, monitoring, incident response, compliance, guardrails, and a clear deployment roadmap.

### What I Learned

#### AI and Effective AI Usage

- I gained a clearer understanding of the role of context when working with AI.
- I learned that AI output quality depends heavily on goals, constraints, relevant data, and expected output format.
- I realized that providing too much unrelated information can reduce output quality because noisy context distracts the model.
- I understood the shift from single prompts to context systems and memory in modern AI applications.
- I learned about student-friendly AI project ideas such as AI Study Assistant, PDF Chat App, AI Code Reviewer, and Personal Second Brain.

#### AWS and Cloud Architecture

- I gained a better understanding of Amazon CloudFront in modern application architecture.
- I realized that CloudFront is not only a CDN, but also supports cost optimization, security, performance, and reliability.
- I learned about security mechanisms such as AWS WAF, AWS Shield, Signed URL, Origin Access Control, Mutual TLS, and geographic restriction.
- I understood how CloudFront reduces origin load through caching, request collapsing, compression, and persistent connections.
- I gained a better perspective on designing more resilient systems using edge networks, failover, and custom error handling.

#### Automation and Enterprise AI Applications

- I understood how agentic AI can support business process automation.
- I learned that Amazon Quick Suite can connect multiple data sources and support enterprise users with research, dashboards, automation flows, and insight generation.
- I realized that AI in business is not limited to answering questions; it can also take actions and support operational workflows.
- I learned a practical example of a PM assistant that can create meeting minutes, send emails, and schedule meetings.

#### LLMs in Production

- I understood how LLMs choose the next token using logits, softmax, and temperature.
- I learned that temperature = 0 does not guarantee fully deterministic output.
- I learned about causes of non-determinism such as floating-point arithmetic, GPU parallelism, and inference batching.
- I understood that production AI systems should be designed to handle output variance and require strong testing practices.
- I learned mitigation approaches such as majority voting, structured output, constrained output, and repeated testing.

#### Multi-Agent Systems

- I learned when to use a single-agent system and when to use a multi-agent system.
- I understood that multi-agent systems are suitable for multi-domain problems that require many evaluation criteria and audit trails.
- I learned how a multi-agent system can simulate a virtual credit committee with specialized agents.
- I realized the importance of guardrails, compliance, security, observability, and operations when deploying AI in enterprise environments.
- I gained a practical view of how AWS building blocks such as Bedrock, ECR, API Gateway, IAM, Secrets Manager, CloudWatch, and X-Ray can support production-ready AI systems.

#### Product Thinking and Teamwork

- I learned that a strong product idea can start from a real pain point in daily work.
- I understood how a hackathon team can build an MVP quickly by focusing on the demo path and cutting unnecessary features.
- I realized that token usage in AI products is not only a cost issue but also affects UX and system design.
- I learned that team chemistry, task splitting, and fast decision-making are very important when building under time pressure.
- I became more motivated to join community events, workshops, and hackathons to learn practical experience from others.

### Application to My Study and Work

- I can apply better context preparation when using AI for learning, writing reports, debugging code, or building projects.
- When working with AI, I should define the goal, constraints, relevant information, and expected output format before asking.
- When designing backend or cloud architecture, I should consider not only whether the system works, but also cost, security, performance, and scalability.
- I can apply CloudFront knowledge when deploying static websites, APIs, or applications that need faster access.
- I can use ideas such as AI assistant or second brain as references for personal projects.
- When building AI applications, I should include testing, logging, guardrails, and handling for non-deterministic outputs.
- I can apply multi-agent thinking to complex problems that require multiple perspectives or specialized roles.
- I gained more direction for choosing a final project related to AI assistant, cloud architecture, serverless applications, or data/automation workflows.

### Experience in the Event

Participating in **FCAJ Community Day** was a very valuable experience for me. The event not only helped me learn more about AWS and AI, but also gave me the opportunity to listen to practical sharing from people working in cloud, DevOps, AI, and enterprise systems.

What impressed me most was that the sessions were not only theoretical. They were connected to real problems: how to use AI more effectively, how to optimize CloudFront, how to build a product during a hackathon, how to understand LLM behavior in production, and how to design enterprise-grade AI systems.

Through the sessions, I realized that to grow in cloud and AI, learners need more than just knowing how to use services. They also need system thinking, the ability to ask the right questions, an understanding of business problems, and awareness of security, cost, operations, and scalability.

The event also motivated me to continue learning AWS, joining community activities, and building more practical personal projects. It was a meaningful activity during my internship because it connected what I learned in the modules with real-world use cases.

#### Some photos from the event

* Add my photos from the event here.

> Overall, FCAJ Community Day helped me broaden my view of AWS, Generative AI, and how cloud technologies are applied in practice. The event provided useful knowledge and gave me more direction for learning, writing blogs, and developing my final project.
