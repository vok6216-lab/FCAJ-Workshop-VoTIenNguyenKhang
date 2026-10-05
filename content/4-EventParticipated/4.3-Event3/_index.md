---
title: "Event 3"
date: 2026-10-02
weight: 3
chapter: false
pre: " 4.3. "
---

# Navigating the Future of Cloud & AI in Vietnam

## 1. Event Name

**Navigating the Future of Cloud & AI in Vietnam**

The event featured a keynote session by Dr. Werner Vogels, Chief Technology Officer (CTO) and Vice President of Amazon. The session focused on the future of cloud computing, artificial intelligence, operational excellence, and the evolution of software engineering in the AI era.

Drawing on more than two decades of experience leading global infrastructure at Amazon and Amazon Web Services (AWS), Dr. Vogels shared insights into building reliable distributed systems, designing technology for large-scale operations, and developing the skills needed to succeed in the rapidly evolving technology industry.

The keynote also explored how AI is transforming software development and why engineers must continue to develop systems thinking, ownership, intellectual curiosity, and effective communication skills.

## 2. Date and Time

- **Date:** October 2, 2026
- **Time:** 08:30 AM – 12:00 PM
- **Time Zone:** GMT+7

The event was scheduled to take place on Friday, October 2, 2026.

## 3. Location

- **Venue:** Bitexco Financial Tower
- **Address:** 2 Hai Trieu Street, Ho Chi Minh City, Vietnam

The event brought together members of the technology community to explore emerging developments in cloud computing and AI while learning from an experienced technology leader.

## 4. Participation Role

I participated in the *Navigating the Future of Cloud & AI in Vietnam* event as an attendee and learner in the First Cloud AI Journey (FCAJ) program.

Through Dr. Werner Vogels' keynote session, I gained a deeper understanding of the engineering principles behind large-scale cloud infrastructure, the importance of operational excellence, and the changing responsibilities of software developers in the AI era.

As a Software Engineering student, I was particularly interested in how engineers can design reliable systems, make effective architectural decisions, and use AI tools without compromising software quality or security.

The keynote also encouraged me to reflect on my learning journey and identify the technical and professional skills I need to develop to prepare for future opportunities in software engineering and cloud computing.

## 5. Key Knowledge and Skills Acquired

### 5.1. Learning About System Design Through Real-World Failures

One of the most interesting lessons from Dr. Werner Vogels was how real-world operational failures can influence important system architecture decisions.

More than two decades ago, Amazon experienced a serious database incident during the peak holiday shopping season. A relational database cluster became overloaded, significantly disrupting customer data storage and resulting in substantial financial losses.

This incident demonstrated that commercial software is not always suitable for every workload, especially when systems operate at an extremely large scale.

Engineers analyzed actual database access patterns and discovered that many operations did not require the full capabilities of a traditional relational database:

- Approximately 70% of database workloads involved simple Key-Value lookups.
- Approximately 20% involved single tables without relationships.
- Only around 10% required the capabilities of a relational database.

These findings helped motivate the development of distributed Key-Value storage technologies, laying the groundwork for Amazon Dynamo and DynamoDB.

The main lessons I learned include:

- **Understand actual workloads:** System architecture should reflect real application requirements rather than assumptions.
- **Choose appropriate technologies:** Different workloads require different approaches to data storage and processing.
- **Learn from failures:** Real-world operational incidents can reveal architectural weaknesses and opportunities for improvement.
- **Design for scalability:** Systems should be designed according to expected workloads, growth potential, and reliability requirements.

This example helped me understand that effective software engineering involves more than writing code. It also requires careful problem analysis and selecting solutions that meet the actual needs of a system.

### 5.2. The Four Pillars of Operational Excellence

Operational excellence plays an essential role in maintaining reliable services and delivering consistent user experiences.

Dr. Vogels emphasized several engineering practices that Amazon uses to improve the reliability and resilience of large-scale infrastructure.

**1. Measure Performance at the 99.9th Percentile**

Average response time cannot fully represent application performance. This metric may hide slow requests that significantly affect the experience of certain users.

Engineers should monitor latency percentiles, including P99 and P99.9, to better understand the experience of users whose requests take the longest to complete.

This approach helps identify performance bottlenecks and improve overall service quality.

**2. Embrace the Principle That Everything Can Fail at Any Time**

Distributed systems should be designed with the assumption that individual components can fail.

Important practices include:

- Avoiding unnecessary single points of failure.
- Designing appropriate redundancy and failover mechanisms.
- Ensuring that a failure in one component does not automatically bring down the entire application.
- Testing recovery procedures under conditions that closely resemble real-world scenarios.

This principle highlights the importance of resilience when designing cloud-based applications.

**3. Make GameDays a Regular Practice**

GameDays are controlled exercises designed to test how systems respond to failures.

Engineering teams proactively simulate infrastructure problems to evaluate whether automatic recovery and failover mechanisms operate as expected.

These exercises help teams:

- Identify weaknesses in system architecture.
- Validate automated recovery procedures.
- Reduce dependence on manual intervention.
- Improve incident response and operational readiness.
- Build confidence in system resilience.

**4. Understand the Pay-as-You-Go Cloud Pricing Model**

Cloud computing changes how organizations invest in and manage computing resources.

Instead of making large upfront investments in infrastructure, customers can use cloud services according to their actual needs and consumption.

This model provides flexibility but also requires organizations to monitor resource usage and optimize costs.

The key lesson is that operational excellence is not only about technical reliability. It also includes efficient resource management and the ability to deliver consistent value to customers.

### 5.3. Developing the Mindset of a Renaissance Developer

One of the most valuable concepts introduced by Dr. Vogels was the Renaissance Developer, which can be understood as a versatile software developer with broad knowledge and a holistic perspective.

As AI tools become increasingly capable of generating source code, software engineers need to develop broader skills and take greater responsibility for the systems they build.

The Renaissance Developer mindset includes five essential characteristics.

**1. Curiosity and Continuous Learning**

Technology constantly evolves with the introduction of new programming languages, frameworks, cloud services, and AI tools.

Developers should maintain a habit of learning, experimenting, and improving their technical knowledge.

**2. Systems Thinking**

Engineers need to understand how individual components interact within a complete system.

Rather than focusing only on a single module, developers should consider dependencies, data flows, performance, security, and the impact of architectural decisions on the entire application.

**3. Ownership and Accountability**

AI can generate source code, but engineers remain responsible for the software they deliver.

This includes verifying correctness, identifying security vulnerabilities, handling exceptional cases, and maintaining architectural integrity.

**4. Deep Expertise Combined with Broad Knowledge (T-Shaped Expertise)**

A T-shaped developer combines deep expertise in a primary technical discipline with broad knowledge of related fields.

For example, a backend developer can benefit from understanding databases, user interfaces, infrastructure, security, and business requirements.

This holistic perspective helps engineers optimize the entire process rather than improving individual components in isolation.

**5. Communication Skills**

Technical expertise alone is not always sufficient to solve every engineering problem.

Developers need to communicate effectively with teammates and stakeholders, understand business requirements, and explain the trade-offs between different technical solutions.

These characteristics provide a useful direction for becoming a more capable and responsible software engineer.

### 5.4. Artificial Intelligence as a Tool for Software Development

The keynote explored how AI is transforming software development and changing the responsibilities of engineers.

AI tools can significantly accelerate prototyping, help developers generate source code, explore solutions, and automate repetitive tasks.

However, AI-generated code is not automatically correct, secure, efficient, or suitable for production deployment.

Important considerations include:

- **Code quality:** Review generated code for correctness, readability, and maintainability.
- **Security:** Identify vulnerabilities and ensure that sensitive information is handled appropriately.
- **Edge cases:** Test unusual inputs, failure scenarios, and less common application states.
- **Performance:** Evaluate resource consumption and identify inefficient implementations.
- **Human judgment:** Make architectural decisions by considering the entire system and its intended purpose.

The keynote compared AI to an imperfect compiler that translates natural-language instructions into source code. This comparison emphasizes that developers must carefully evaluate the output rather than blindly trusting generated code.

I realized that AI should be treated as a software development assistant rather than a replacement for engineering judgment and professional responsibility.

### 5.5. Systems Thinking and End-to-End Problem Solving

Systems thinking is the ability to understand the relationships between different components and evaluate how individual decisions affect the entire system.

For example, improving the performance of one service may not make an application faster if the database, network, or another dependent service remains a bottleneck.

To apply systems thinking, engineers should:

- Understand the complete application architecture.
- Identify dependencies between services and databases.
- Track data flows across different components.
- Evaluate how changes affect performance, reliability, and security.
- Consider trade-offs between cost, availability, and complexity.
- Investigate root causes instead of addressing only visible symptoms.

This approach is particularly relevant to cloud engineering, where applications often depend on multiple services and infrastructure components.

Systems thinking also helps developers make more informed decisions when designing, debugging, and maintaining complex software systems.

### 5.6. Professional Responsibility and the Future of Software Engineering

Dr. Vogels emphasized that the growing capabilities of AI do not eliminate the need for skilled software engineers.

Although AI can automate many repetitive development tasks, engineers remain responsible for understanding problems, making decisions, and ensuring that systems function correctly.

Important professional principles include:

- Taking responsibility for source code and the systems being developed.
- Maintaining high standards for software quality and security.
- Continuously learning new technologies and modern engineering practices.
- Developing creativity, critical thinking, and problem-solving skills.
- Communicating technical decisions clearly.
- Proactively questioning outdated assumptions and remaining open to better approaches.

The keynote concluded with a well-known quote attributed to Rear Admiral Grace Hopper:

**"The most dangerous phrase in the language is, 'We've always done it this way.'"**

This message highlights the importance of questioning existing practices, embracing positive change, and continuously searching for better solutions.

## 6. Check-in Photo as Evidence of Participation

The image below is intended to be used as my check-in photo at the *Navigating the Future of Cloud & AI in Vietnam* event to demonstrate my participation.

**Navigating the Future of Cloud & AI in Vietnam – Check-in Photo**

**Participation Evidence:** Replace the placeholder image link with an actual check-in photo taken at the event. The image should accurately reflect my participation and should only be used as evidence after verification.

## 7. Lessons Learned and Personal Contributions

### Lessons Learned

After studying the keynote content, I identified several important lessons for my development as a Software Engineering student participating in the FCAJ program.

- **Architecture should reflect actual workloads:** Engineers should analyze real usage patterns before choosing databases, infrastructure, and system components.
- **Reliability requires preparation:** Systems should be designed to withstand failures, and recovery mechanisms should be tested regularly.
- **Performance metrics matter:** Monitoring high-percentile latency can reveal problems that average response times fail to show.
- **AI does not eliminate engineering responsibility:** Developers must verify AI-generated code for correctness, security, performance, and maintainability.
- **Systems thinking improves decision-making:** Understanding how components interact helps engineers solve problems at the system level.
- **Continuous learning is essential:** Developers must continually improve their skills as cloud computing and AI evolve.
- **Communication is an engineering advantage:** Understanding business requirements and explaining technical alternatives can lead to better solutions.
- **Accountability makes a difference:** Developers must take responsibility for the behavior and quality of the systems they deliver.
- **Innovation requires questioning assumptions:** Existing practices should be evaluated regularly to determine whether better solutions are available.

### Personal Contributions

Based on the knowledge gained from the keynote, I identified several ways to apply these lessons to my studies and future projects:

- Review software architecture before selecting technologies for a project.
- Explore AWS services and practice deploying applications on cloud infrastructure.
- Learn how to monitor application performance using latency metrics and system logs.
- Practice designing applications with appropriate error-handling and recovery mechanisms.
- Use AI tools to accelerate programming while actively reviewing and testing generated results.
- Strengthen my knowledge of databases, backend development, computer networking, and cloud infrastructure.
- Document technical decisions and explain the reasoning behind architectural choices.
- Continue researching emerging technologies and experimenting with practical solutions.
- Apply systems thinking when debugging and evaluating changes to applications.

Through these learning activities, I can connect the knowledge shared during the keynote with my training in the FCAJ program while improving my preparation for future opportunities in software engineering and cloud computing.

## Conclusion

The *Navigating the Future of Cloud & AI in Vietnam* event provided valuable insights into the engineering principles behind reliable cloud infrastructure and the evolving role of software developers in the AI era.

Dr. Werner Vogels' keynote demonstrated the importance of learning from real-world operational failures, analyzing workloads, measuring performance, preparing for infrastructure failures, and building systems that operate reliably at scale.

More importantly, the concept of the Renaissance Developer helped me understand that a successful software engineer needs more than programming skills. Engineers must develop systems thinking, accountability, curiosity, broad technical knowledge, and effective communication.

AI can accelerate software development, but professional judgment, security awareness, and engineering responsibility remain essential for producing production-ready systems.

As a Software Engineering student participating in the First Cloud AI Journey program, I can apply these lessons by strengthening my AWS knowledge, practicing system design, exploring AI-powered software development tools, and continuously improving my technical skills.

Ultimately, continuous learning, operational excellence, and the responsible use of AI are essential to becoming a capable software engineer who can build reliable, scalable solutions to real-world problems.
