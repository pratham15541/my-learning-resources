# System Design Resources

This folder contains system design, software engineering, and architecture references for building scalable systems.

## How to Use This Folder

- Begin with practical interview-oriented design patterns.
- Add implementation and reliability depth with architecture and SRE materials.
- Pair reading with architecture diagrams and trade-off notes.

## Online Repositories and Series

- Low Level Design (LLD): [awesome-low-level-design](https://github.com/ashishps1/awesome-low-level-design)
- System Design Primer: [system-design-primer](https://github.com/donnemartin/system-design-primer)
- System Design Repository: [system-design](https://github.com/karanpratapsingh/system-design)
- System Design Learning Series: [Karan Pratap Singh Series](https://dev.to/karanpratapsingh/series/19332)
- Roadmap: [System Design](https://roadmap.sh/system-design)

## Local Books

- [books/](books/README.md): Local book collection in recommended order.

## Phased Learning Roadmap

### Phase 1 - LLD (Thinking in Components)

Goal:

- Learn how systems are built internally.

Learn:

- Design patterns (Factory, Observer, Strategy).
- Object modeling.
- API design.
- Basic concurrency.

Resources:

- [Object-Oriented Basics](books/Object-Oriented%20Basics%20-%20Grokking%20the%20Object%20Oriented%20Design%20Interview.pdf)
- [Head First Design Patterns](books/Head%20First%20Design%20Patterns.pdf)
- [Clean Architecture](books/Clean%20Architecture%20A%20Craftsman's%20Guide%20to%20Software%20Structure%20and%20Design.pdf)
- LLD problems (parking lot, elevator, splitwise).

Security focus:

- Input validation.
- Basic authentication concepts.
- Secure coding practices.

### Phase 2 - Core System Design (HLD Fundamentals)

Goal:

- Understand how systems scale.

Learn deeply:

- Load balancers.
- Caching (Redis, CDN).
- Databases (SQL vs NoSQL).
- CAP theorem.
- Replication and sharding.
- Message queues.

Core resources:

- [Understanding Distributed Systems](books/Understanding%20Distributed%20Systems%202nd%20edition.pdf)
- [Designing Data-Intensive Applications](books/Designing%20Data%20Intensive%20Applications.pdf)

Focus questions:

- Why PostgreSQL vs MongoDB?
- Why Cassandra for high writes?
- Why Redis for latency?

Security focus:

- Encryption (TLS, at rest).
- Data leaks via caching.
- Replication risks.
- Trust boundaries.

### Phase 3 - System Design + Tradeoffs (Real Thinking)

Goal:

- Make decisions like a senior engineer.

Practice using:

- GitHub System Design Primer.
- ByteByteGo.

You must answer:

- Why this database?
- Why not alternatives?
- What breaks at scale?
- What if traffic increases by 100x?

Example thinking:

- Read-heavy workload -> cache + replicas.
- Write-heavy workload -> partitioning + eventual consistency.
- Strong consistency -> slower but safer.

Security focus:

- Rate limiting (prevent abuse).
- API gateway protection.
- Authentication vs authorization.
- DDoS basics.

### Phase 4 - System Design Security (Critical)

Goal:

- Design systems that do not get hacked or leak data.

Core resource:

- OWASP Top 10: [owasp.org/www-project-top-ten](https://owasp.org/www-project-top-ten/)

Learn:

- SQL injection.
- Cross-site scripting (XSS).
- Broken authentication.
- Sensitive data exposure.

Practical security resource:

- Web Application Security.

Production-level thinking resource:

- [Google SRE Workbook](books/Google%20SRE%20Workbook.pdf)

Also learn:

- Authentication systems (JWT, OAuth).
- Authorization (RBAC).
- Secrets management.
- Secure architecture design.

### Phase 5 - Advanced System Design (Senior Level)

Goal:

- Handle real-world complexity.

Topics:

- Event-driven architecture.
- Stream processing (Kafka).
- Distributed transactions.
- Idempotency.
- Observability (logs, metrics, tracing).

Think in tradeoffs:

- Consistency vs latency.
- Cost vs performance.
- Security vs usability.

Security focus:

- Zero trust architecture.
- Secure microservices communication.
- Data privacy (GDPR-style thinking).

### Phase 6 - Build Real Systems (Most Important)

Goal:

- Convert theory into decision-making through implementation.

Build projects like:

- URL shortener: database choice, caching, rate limiting.
- Chat system (WhatsApp-style): WebSockets, queues, encryption considerations.
- Payment system: idempotency, strong consistency, fraud detection basics.

While building, always ask:

- What can break?
- What can be attacked?
- What will not scale?

You must:

- Struggle with decisions.
- Compare alternatives.
- Justify tradeoffs.

## Practice Question Bank (LLD + HLD)

Use this section as a build-first curriculum.

For every question below, always define:

- Functional requirements and non-functional requirements.
- API contracts and data models.
- Consistency, latency, availability, and cost tradeoffs.
- Failure modes, abuse vectors, and security controls.
- How the design evolves from 10K users to 1M+ users.

### LLD Questions (10)

1. Design a parking lot system.
   Think about slot allocation strategy, extensibility for vehicle types, concurrency during entry/exit bursts, and payment module integration.
2. Design an elevator control system for a high-rise building.
   Think about scheduling algorithms, starvation prevention, priority handling, and fault handling when an elevator is offline.
3. Design Splitwise-style expense sharing.
   Think about transaction modeling, precision and rounding, settlement simplification, and auditability of balance history.
4. Design a library management system.
   Think about catalog indexing, reservation and waitlist workflows, fine calculation, and concurrent borrow/return races.
5. Design a meeting room booking system.
   Think about conflict detection, recurring bookings, timezone handling, and cancellation policy rules.
6. Design a notification service SDK (email, SMS, push).
   Think about channel abstraction, retry strategies, idempotency keys, and provider failover.
7. Design an in-memory cache with TTL and eviction.
   Think about LRU/LFU tradeoffs, thread safety, memory pressure handling, and stale-read behavior.
8. Design an API rate limiter component.
   Think about token bucket vs sliding window, distributed counters, fairness, and bypass rules for trusted clients.
9. Design a coupon and promotion engine.
   Think about rule evaluation order, combinability constraints, fraud scenarios, and deterministic outcomes.
10. Design a multiplayer game leaderboard module.
    Think about ranking updates, tie-breaking, anti-cheat checks, and eventual vs strong consistency for score display.

### HLD Questions (10)

1. Design a URL shortener for 1M+ daily active users.
   Tradeoffs: key generation, read-heavy caching, analytics pipeline, abuse prevention, and geo latency.
2. Design a WhatsApp-style chat system for 1M+ concurrent users.
   Tradeoffs: WebSockets at scale, message ordering, offline delivery, fan-out model, and end-to-end encryption boundaries.
3. Design a ride-hailing platform.
   Tradeoffs: matching latency, location indexing, surge pricing consistency, and graceful degradation during traffic spikes.
4. Design a video streaming platform.
   Tradeoffs: CDN strategy, transcoding pipeline, storage tiering, recommendation freshness, and content security.
5. Design an e-commerce platform (catalog, cart, checkout).
   Tradeoffs: inventory consistency, flash sale handling, payment reliability, and cart persistence model.
6. Design a payments ledger system.
   Tradeoffs: exactly-once semantics, idempotency, reconciliation, fraud checks, and strong consistency zones.
7. Design a social media feed service.
   Tradeoffs: fan-out on write vs fan-out on read, ranking model, hot-key mitigation, and moderation latency.
8. Design a metrics and observability platform.
   Tradeoffs: high-ingest write path, retention tiers, query latency, cardinality limits, and multi-tenant isolation.
9. Design a distributed file storage service (Drive-like).
   Tradeoffs: chunking strategy, metadata consistency, deduplication, sync conflict resolution, and secure sharing links.
10. Design a ticket booking system for high-demand events.
    Tradeoffs: oversell prevention, queue design, lock strategy, payment timeout handling, bot mitigation, and fairness.

### How to Solve Each Question

- Step 1: Start with assumptions and scope boundaries.
- Step 2: Define APIs and schema before deep architecture.
- Step 3: Draw baseline architecture, then identify bottlenecks.
- Step 4: Add scaling layers (cache, queue, partitioning, replicas).
- Step 5: Add security controls (authn/authz, rate limiting, input validation, encryption).
- Step 6: Explain why chosen components beat alternatives.
- Step 7: Run a 100x traffic thought experiment and redesign weak points.

## Books and What They Cover

### System Design Interview - An Insider's Guide

File: `Alex Yu - System Design Interview An Insider's Guide (2020, Independently published) - libgen.li.pdf`

Covers:

- Structured framework for approaching open-ended system design questions.
- Capacity estimation, API design, and high-level architecture decisions.
- Core components such as load balancers, caches, databases, and queues.
- Common interview case studies including URL shorteners and feeds.
- Trade-off communication patterns for interview clarity.

### Designing Data-Intensive Applications

File: `Designing Data Intensive Applications.pdf`

Covers:

- Data models, storage engines, and distributed system fundamentals.
- Replication, partitioning, consistency, and consensus trade-offs.
- Batch and stream processing architectures.
- Reliability and maintainability principles for large systems.
- Conceptual tools for making durable architecture decisions.

### Google SRE Workbook

File: `Google SRE Workbook.pdf`

Covers:

- Practical SRE implementation patterns and organizational adoption.
- Service level objectives (SLOs), error budgets, and reliability culture.
- Incident response, postmortems, and operational excellence workflows.
- Monitoring, alerting, and toil reduction guidance.
- Real operational case studies and production checklists.

### Head First Design Patterns

File: `Head First Design Patterns.pdf`

Covers:

- Object-oriented design patterns with visual and example-driven teaching.
- Core patterns such as Strategy, Observer, Factory, and Singleton.
- Decoupling and extensibility practices for maintainable codebases.
- Refactoring toward reusable and testable designs.
- Pattern selection guidance through real coding scenarios.

### Seven Databases in Seven Weeks

File: `Seven databases in seven weeks.pdf`

Covers:

- Practical introduction to multiple database paradigms, not just relational systems.
- Hands-on examples across key models like relational, document, key-value, column-family, and graph.
- Query language and data modeling differences between database families.
- Trade-offs in consistency, scalability, and operational complexity when choosing a database.
- Decision-making mindset for selecting the right data store for specific system requirements.

### Clean Code

File: `Clean Code ( PDFDrive.com ).pdf`

Covers:

- Naming, function design, and class structure best practices.
- Readability-first coding style and maintainability habits.
- Refactoring practices that reduce complexity and technical debt.
- Unit testing principles and boundaries for robust code.
- Professional development discipline for long-term code quality.

### Object-Oriented Basics

File: `Object-Oriented Basics - Grokking the Object Oriented Design Interview.pdf`

Covers:

- Core object-oriented concepts (Inheritance, Polymorphism, Encapsulation, Abstraction).
- Visualizing systems using UML diagrams and class diagrams.
- Applying design principles to model real-world systems.
- Preparation strategies for low-level design and object-oriented design interviews.

### Clean Architecture

File: `Clean Architecture A Craftsman's Guide to Software Structure and Design.pdf`

Covers:

- SOLID design principles at the component level.
- Structuring software with clear boundaries and dependency rules.
- Separation of concerns across enterprise business rules, application use cases, and interface adapters.
- Designing architectures that keep options open and defer implementation details.

### Understanding Distributed Systems

File: `Understanding Distributed Systems 2nd edition.pdf`

Covers:

- Core communication patterns (network protocols, APIs, messaging).
- Coordination protocols and consensus patterns in distributed networks.
- Scalability primitives (load balancing, caching, partition strategies).
- Designing resilient systems (retries, rate limiting, circuit breakers).
- Security, monitoring, and operational observability for distributed deployments.
