# DevOps Resources

This folder contains DevOps, observability, and production operations material.

## Folder Layout

- [books/](books/README.md): Book summaries and a recommended reading order for DevOps learning.

## Focus Areas

- Build and release automation.
- Operating services in production.
- Observability, incident response, and reliability.
- Linux command-line utilities that support day-to-day operations.

## Notes

Use this folder alongside the system design track when you want more operational depth than architecture alone provides.

## Book Guide

- [DevOps books](books/README.md): Practical reading on delivery pipelines, production stability, observability, and Linux tooling.

## System Design vs DevOps Questions

System design asks:

- What should we build?

DevOps asks:

- How do we run this reliably in production, at scale, without breaking it every week?

The tradeoffs are often the same, viewed from a different operational angle.

## DevOps Decision Framework

Instead of evaluating choices only as architecture (for example, Kafka vs RabbitMQ), apply a DevOps lens:

- How hard is this to operate?
- How do we monitor and debug it?
- What happens when it fails at 3AM?
- What is the on-call burden?

### 1. DevOps Tradeoff Axes

Use these axes for day-to-day engineering decisions:

- Operability: How easy is it to run, patch, and debug?
- Observability: Logs, metrics, traces, and alert quality.
- Failure blast radius: How far does one bad change propagate?
- On-call complexity: How many systems must responders understand?
- Automation level: How much is manual vs repeatable by pipeline?
- MTTR: How quickly can the team recover service?

Golden rule:

- The best system is not the most scalable. It is the one your team can keep alive.

### 2. Monolith vs Microservices (DevOps View)

Monolith advantages:

- Single deployment pipeline.
- Centralized logs.
- Easier debugging path.
- Lower infrastructure cost.

Monolith pain:

- Large deployments are riskier.
- Scaling is coarse-grained.

Microservices advantages:

- Independent deploys.
- Better scaling control per service.

Microservices pain:

- Distributed tracing becomes mandatory.
- Log aggregation is required.
- Cross-service debugging is harder.
- CI/CD pipelines multiply.
- On-call load increases.

Operational reality:

- Microservices are a DevOps problem first, architecture problem second.

### 3. Kafka vs RabbitMQ (DevOps Lens)

Apache Kafka operational profile:

- Requires cluster management.
- Needs partition and replication balancing.
- Requires lag and offset monitoring.
- Needs disk and retention management.

Common failure modes:

- Consumer lag causes backlog growth.
- Broker failures can impact partition availability.

Tradeoff summary:

- High throughput and flexibility, with higher operational cost.

RabbitMQ operational profile:

- Easier to run for many teams.
- Simpler monitoring and tuning path.

Common failure modes:

- Queue buildup under load.
- Message loss risk if durability/ack settings are wrong.

Tradeoff summary:

- Lower complexity and faster team adoption, with lower operational overhead.

### 4. Kubernetes (Practical DevOps View)

Why teams choose Kubernetes:

- Auto-scaling.
- Self-healing primitives.
- Declarative infrastructure and deployment patterns.

DevOps tradeoffs:

- Standardization and automation improve platform consistency.
- Complexity cost is significant.
- Debugging becomes harder through extra abstraction layers.
- Strong observability is required for safe operations.

Operational reality:

- Kubernetes solves problems many teams do not have yet.

### 5. Real Incident Scenario

Example stack:

- Microservices
- Kafka
- Kubernetes

Outage sequence:

1. API latency spikes.
2. Basic metrics are not enough to isolate root cause.
3. Logs are distributed across services.
4. Tracing shows delay concentrated in one dependency chain.
5. Kafka consumer lag rises due to downstream slowness.
6. Root cause is a slow downstream service.

What the tradeoffs expose:

- Microservices increase debugging complexity.
- Kafka can hide backpressure until lag is severe.
- Kubernetes adds an abstraction layer during triage.

### 6. What Senior DevOps Engineers Optimize For

Not primarily:

- "Best architecture"

Primary optimization goals:

- Can we debug failures fast?
- Can we deploy safely?
- Can we recover quickly?
- Can new engineers understand and operate this?

Mindset progression:

- Beginner: Which tech stack is best?
- Intermediate: Which architecture scales?
- Senior DevOps: What will break, and how painful is recovery?

### 7. Security Tradeoffs (DevOps Lens)

Security is part of operability, not a separate afterthought. The same design choices that affect scale also affect incident impact.

Core security axes:

- Attack surface: More services and endpoints mean more exposure.
- Secrets management: Secret sprawl increases leak risk and rotation burden.
- Identity and access: Fine-grained access improves safety but increases policy complexity.
- Isolation and blast radius: Strong boundaries reduce compromise impact but add platform complexity.
- Detection and response: Better telemetry improves threat response but increases data volume and tuning work.

Typical tradeoffs:

- Monolith: Smaller attack surface and simpler auth paths, but a compromise can have wider impact.
- Microservices: Better service isolation potential, but mTLS, service identity, and policy drift become operational risks.
- Kafka/RabbitMQ: Durable messaging improves recovery, but unsecured brokers, weak ACLs, or plaintext traffic create high-impact risk.
- Kubernetes: Strong policy controls are possible, but misconfigured RBAC, network policies, or admission controls can create systemic exposure.

Security guardrails for production:

- Enforce least-privilege access for humans and services.
- Centralize secret management with rotation and auditing.
- Encrypt traffic in transit and sensitive data at rest.
- Use immutable, signed artifacts in CI/CD where possible.
- Add runtime detection with actionable alerts, not only dashboards.
- Practice incident response drills that include security failures.

Security outcome metric:

- Optimize for reduced breach impact and fast containment, not only prevention.
