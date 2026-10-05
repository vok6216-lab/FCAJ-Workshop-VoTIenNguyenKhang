
---
title: "Event 3"
date: 2026-10-02
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

# Navigating the Future of Cloud & AI in Vietnam

## 1. Event Name

**Navigating the Future of Cloud & AI in Vietnam**

The event featured a keynote session by **Dr. Werner Vogels, Chief Technology Officer and Vice President at Amazon**, focusing on the future of cloud computing, artificial intelligence, operational excellence, and the evolution of software engineering in the age of AI.

Drawing on his experience leading global infrastructure at Amazon and Amazon Web Services (AWS), Dr. Vogels shared insights into building reliable distributed systems, designing technology for large-scale operations, and developing the skills required to succeed in a rapidly changing technology industry.

The keynote also explored how AI is changing software development and why engineers must continue to develop systems thinking, technical ownership, curiosity, and effective communication skills.

## 2. Time

- **Date:** October 2, 2026
- **Time:** 08:30 AM – 12:00 PM
- **Timezone:** GMT+7

The event was scheduled for Friday, October 2, 2026.

## 3. Location

- **Venue:** Bitexco Financial Tower
- **Address:** 2 Hai Trieu Street, Ho Chi Minh City, Vietnam

The event brought together members of the technology community to explore developments in cloud computing and AI and learn from the experiences of an experienced technology leader.

## 4. Participation Role

I participated in **Navigating the Future of Cloud & AI in Vietnam** as a **participant and learner in the First Cloud AI Journey (FCAJ) program**.

Through the keynote session by Dr. Werner Vogels, I gained insights into the engineering principles behind large-scale cloud infrastructure, the importance of operational excellence, and the changing responsibilities of software developers in the age of AI.

As a Software Engineering student, I was particularly interested in how engineers can design reliable systems, make effective architectural decisions, and use AI tools without compromising software quality and security.

The session also encouraged me to reflect on my own learning journey and identify the technical and professional skills I need to develop to prepare for future opportunities in software engineering and cloud computing.

## 5. Main Knowledge and Skills Gained

### 5.1. Understanding System Design Through Real-World Failures

One of the most interesting lessons from Dr. Werner Vogels was how real-world operational failures can influence major architectural decisions.

More than two decades ago, Amazon experienced a critical database failure during the peak holiday shopping season. A relational database cluster became overloaded, causing a major disruption to customer data storage and resulting in significant financial losses.

This incident demonstrated that commercial software is not always suitable for every workload, especially when a system operates at an extremely large scale.

Engineers analyzed actual database usage patterns and discovered that many operations did not require the full capabilities of a traditional relational database:

- Approximately 70% of database workloads involved simple Key-Value queries.
- Approximately 20% involved single, unlinked tables.
- Only approximately 10% genuinely required relational database capabilities.

These findings helped motivate the development of distributed Key-Value storage technology that contributed to the foundations of Amazon Dynamo and DynamoDB.

The main lessons I gained include:

- **Understand actual workloads:** System architecture should reflect real application requirements rather than assumptions.
- **Choose appropriate technologies:** Different workloads require different data storage and processing approaches.
- **Learn from failures:** Production incidents can reveal architectural weaknesses and opportunities for improvement.
- **Design for scale:** Systems must be designed with their expected workload, growth, and reliability requirements in mind.

This example helped me understand that effective software engineering involves analyzing problems carefully and selecting solutions that fit the actual needs of a system.

### 5.2. Four Pillars of Operational Excellence

Operational excellence is essential for maintaining reliable services and delivering consistent user experiences.

Dr. Vogels highlighted several engineering practices that Amazon uses to improve the reliability and resilience of large-scale infrastructure.

**1. Measuring Performance at the 99.9th Percentile**

Average response time alone does not provide a complete picture of application performance. It can hide slow requests that significantly affect some users.

Engineers should monitor latency percentiles, including P99 and P99.9, to understand the experience of users at the slower end of the performance distribution.

This approach helps identify performance bottlenecks and improve the overall quality of a service.

**2. Embracing "Everything Fails All the Time"**

Distributed systems must be designed with the expectation that individual components can fail.

Important practices include:

- Avoiding unnecessary single points of failure.
- Designing appropriate redundancy and failover mechanisms.
- Ensuring that failures in individual components do not automatically cause the entire application to become unavailable.
- Testing recovery procedures under realistic conditions.

This principle reinforces the importance of resilience when designing cloud-based applications.

**3. Institutionalizing GameDays**

GameDays are controlled exercises used to test how systems respond to failures.

Engineering teams deliberately simulate infrastructure problems to evaluate whether automated recovery and failover mechanisms work as expected.

These exercises can help teams:

- Identify weaknesses in system architecture.
- Verify automated recovery procedures.
- Reduce dependence on manual intervention.
- Improve incident response and operational readiness.
- Build confidence in system resilience.

**4. Understanding the Cloud Pay-as-You-Go Model**

Cloud computing changes how organizations acquire and manage computing resources.

Instead of committing to large infrastructure investments upfront, customers can use cloud services according to their requirements and usage.

This model provides flexibility, but it also requires organizations to monitor resource consumption and optimize costs.

The key lesson is that operational excellence involves not only technical reliability but also efficient resource management and the ability to deliver consistent value to customers.

### 5.3. Developing the Renaissance Developer Mindset

One of the most valuable concepts introduced by Dr. Vogels was the idea of the **Renaissance Developer**.

As AI tools become more capable of generating code, software engineers need to develop broader skills and take greater responsibility for the systems they build.

The Renaissance Developer mindset includes five essential characteristics.

**1. Curiosity and Continuous Learning**

Technology changes constantly, with new programming languages, frameworks, cloud services, and AI tools emerging over time.

Developers should maintain a habit of learning, experimenting, and improving their technical knowledge.

**2. Systems Thinking**

Engineers should understand how individual components interact within a complete system.

Instead of focusing only on a single module, developers need to consider dependencies, data flows, performance, security, and the effects of architectural decisions across the application.

**3. Ownership**

AI can generate code, but engineers remain responsible for the software they deliver.

This includes verifying correctness, identifying security vulnerabilities, handling edge cases, and maintaining architectural integrity.

**4. T-Shaped Expertise**

A T-shaped developer combines deep expertise in a primary technical area with broad knowledge of related disciplines.

For example, a backend developer can benefit from understanding databases, user interfaces, infrastructure, security, and business requirements.

This broader perspective helps engineers optimize complete workflows rather than individual components in isolation.

**5. Communication Skills**

Technical skills alone are not sufficient to solve every engineering problem.

Developers must communicate effectively with teammates and stakeholders, understand actual business requirements, and explain the trade-offs between alternative technical solutions.

These characteristics provide a useful framework for developing into a more capable and responsible software engineer.

### 5.4. Artificial Intelligence as a Tool for Software Development

The keynote explored how AI is changing software development and influencing the responsibilities of engineers.

AI tools can significantly accelerate prototyping and help developers generate code, explore solutions, and automate repetitive tasks.

However, AI-generated code is not automatically correct, secure, efficient, or suitable for production.

Important considerations include:

- **Code Quality:** Reviewing generated code for correctness, readability, and maintainability.
- **Security:** Identifying vulnerabilities and ensuring that sensitive information is handled appropriately.
- **Edge Cases:** Testing unexpected inputs, failure conditions, and unusual application states.
- **Performance:** Evaluating resource usage and identifying inefficient implementations.
- **Human Judgment:** Making architectural decisions that consider the complete system and its intended purpose.

The keynote compared AI to an imprecise compiler that translates natural-language instructions into code. This comparison emphasizes that developers must carefully evaluate the results rather than blindly trusting generated output.

I learned that AI should be treated as a development assistant, not as a replacement for engineering judgment and professional responsibility.

### 5.5. Systems Thinking and End-to-End Problem-Solving

Systems thinking involves understanding the relationships between different components and evaluating how decisions affect the entire system.

For example, improving the performance of one service may not improve the overall application if the database, network, or another dependent service remains a bottleneck.

To apply systems thinking, engineers should:

- Understand the complete application architecture.
- Identify dependencies between services and databases.
- Trace data flows across different components.
- Evaluate the effects of changes on performance, reliability, and security.
- Consider trade-offs between cost, availability, and complexity.
- Investigate root causes instead of addressing only visible symptoms.

This approach is particularly relevant to cloud engineering, where applications often depend on multiple services and infrastructure components.

It also helps developers make more informed decisions when designing, debugging, and maintaining complex software systems.

### 5.6. Professional Responsibility and the Future of Software Engineering

Dr. Vogels emphasized that the growing capabilities of AI do not eliminate the need for skilled software engineers.

Although AI can automate many repetitive development tasks, engineers remain responsible for understanding problems, making decisions, and ensuring that systems operate correctly.

Important professional principles include:

- Taking ownership of the code and systems being developed.
- Maintaining high standards for software quality and security.
- Continuously learning new technologies and engineering practices.
- Developing creativity, critical thinking, and problem-solving skills.
- Communicating technical decisions clearly.
- Challenging outdated assumptions and remaining open to better approaches.

The keynote concluded with a reminder attributed to Rear Admiral Grace Hopper:

"The most dangerous phrase in the language is, 'We've always done it this way.'"

This message highlights the importance of questioning existing practices, embracing constructive change, and continuously searching for better solutions.

## 6. Check-in Photo as Proof of Participation

The following photo is intended to be my check-in photo at **Navigating the Future of Cloud & AI in Vietnam**, demonstrating my participation in the event.

![Navigating the Future of Cloud and AI in Vietnam - Check-in](/images/4-EventParticipated/4.3-Event3/navigating-cloud-ai-checkin.jpg)

> **Check-in Evidence:** Replace the sample image path with an actual check-in photo from the event. The image should accurately represent my participation and should only be used as evidence after it has been verified.

## 7. Lessons Learned and Personal Contribution

### Lessons Learned

After studying the keynote content, I identified several important lessons for my development as a Software Engineering student participating in the FCAJ program.

- **Architecture must reflect real workloads:** Engineers should analyze actual usage patterns before choosing databases, infrastructure, and system components.
- **Reliability requires preparation:** Systems should be designed to tolerate failures, and recovery mechanisms should be tested regularly.
- **Performance metrics matter:** Monitoring high-percentile latency can reveal problems that average response times fail to show.
- **AI does not remove engineering responsibility:** Developers must validate AI-generated code for correctness, security, performance, and maintainability.
- **Systems thinking improves decision-making:** Understanding how components interact helps engineers solve problems at the system level.
- **Continuous learning is essential:** Developers need to keep improving their skills as cloud computing and AI technologies evolve.
- **Communication is a technical advantage:** Understanding business requirements and explaining engineering trade-offs can lead to better solutions.
- **Ownership distinguishes responsible engineers:** Developers must take responsibility for the behavior and quality of the systems they deliver.
- **Innovation requires questioning assumptions:** Existing practices should be evaluated regularly to determine whether better solutions are available.

### Personal Contribution

Based on the knowledge gained from the keynote, I identified several ways to apply these lessons to my studies and future projects:

- Review software architecture before selecting technologies for a project.
- Explore AWS services and practice deploying applications on cloud infrastructure.
- Learn how to monitor application performance using latency metrics and logs.
- Practice designing applications with appropriate error handling and recovery mechanisms.
- Use AI development tools to accelerate coding while manually reviewing and testing their output.
- Improve my understanding of databases, backend development, networking, and cloud infrastructure.
- Document technical decisions and explain the reasons behind architectural choices.
- Continue researching new technologies and experimenting with practical solutions.
- Apply systems thinking when debugging problems and evaluating changes to an application.

Through these learning activities, I can connect the concepts discussed in the keynote with my FCAJ training and strengthen my preparation for future software engineering and cloud computing opportunities.

## Conclusion

**Navigating the Future of Cloud & AI in Vietnam** provided valuable insights into the engineering principles behind reliable cloud infrastructure and the evolving role of software developers in the age of AI.

The keynote by Dr. Werner Vogels demonstrated the importance of learning from production failures, analyzing real workloads, measuring performance, preparing for infrastructure failures, and building systems that can operate reliably at scale.

More importantly, the concept of the **Renaissance Developer** reinforced my understanding that successful software engineers need more than programming skills. They must develop systems thinking, ownership, curiosity, broad technical knowledge, and effective communication.

AI can accelerate software development, but professional judgment, security awareness, and responsibility remain essential when delivering production-quality systems.

As a Software Engineering student participating in the First Cloud AI Journey program, I can apply these lessons by strengthening my AWS knowledge, practicing system design, exploring AI development tools, and continuously improving my technical skills.

Ultimately, **continuous learning, operational excellence, and responsible use of AI** are essential for becoming a capable software engineer who can build reliable, scalable, and practical solutions for real-world problems.
