# Site Reliability Engineering (SRE)

## 1. What is SRE?

SRE (Site Reliability Engineering) is a discipline that applies software
engineering principles to operations problems.

Core mission:

> Ensure system reliability at scale through measurable engineering
> practices.

SRE focuses on stability, availability, scalability, and controlled
risk.

------------------------------------------------------------------------

# 2. Job Boundary of SRE

## What SRE Owns

-   System reliability and availability
-   SLO / SLA definition and monitoring
-   Incident response and postmortem analysis
-   Error budget management
-   Capacity planning
-   Observability systems (metrics, logs, tracing)
-   Automation for remediation and recovery
-   Production risk assessment

SRE answers:

-   How reliable is the system?
-   How much failure is acceptable?
-   Are we burning error budget too fast?
-   Can the system scale safely?

------------------------------------------------------------------------

## What SRE Does NOT Own

-   Business logic implementation
-   Product feature design
-   UI/UX decisions
-   Domain modeling

SRE must understand the system behavior, but does not implement
domain-level business rules.

------------------------------------------------------------------------

# 3. SRE vs DevOps vs Backend

  Role               Core Focus
  ------------------ -------------------------
  Backend Engineer   Business correctness
  DevOps Engineer    Delivery automation
  SRE                Reliability engineering

Backend ensures the system works correctly.

DevOps ensures the system can be delivered efficiently.

SRE ensures the system remains reliable under real-world conditions.

------------------------------------------------------------------------

# 4. Key Concepts SRE Must Master

## 4.1 SLI / SLO / SLA

-   SLI: measurable metric (latency, error rate, availability)
-   SLO: target objective (99.9% uptime, 95% under 200ms)
-   SLA: business-level agreement

Understanding error budget is critical.

------------------------------------------------------------------------

## 4.2 Observability

SRE must deeply understand:

-   Metrics systems (Prometheus)
-   Logging systems (ELK)
-   Distributed tracing
-   Alerting systems

Without observability, reliability cannot be engineered.

------------------------------------------------------------------------

## 4.3 Incident Management

-   Rapid response procedures
-   Root cause analysis (RCA)
-   Postmortem writing
-   Preventive action design

The goal is not only fixing incidents, but preventing recurrence.

------------------------------------------------------------------------

## 4.4 Distributed System Failure Modes

SRE must understand:

-   Network partitions
-   Cascading failures
-   Thread pool exhaustion
-   Connection pool limits
-   GC pauses
-   Resource starvation

Reliability requires understanding how systems fail.

------------------------------------------------------------------------

## 4.5 Capacity & Scaling

-   Load testing
-   Traffic forecasting
-   Autoscaling strategies
-   Resource optimization

SRE ensures performance under growth.

------------------------------------------------------------------------

## 4.6 Automation & Self-Healing

-   Infrastructure as Code
-   Auto-remediation scripts
-   Chaos engineering
-   Failure injection testing

Automation reduces operational risk.

------------------------------------------------------------------------

# 5. When Does a Company Need SRE?

SRE becomes necessary when:

-   Downtime is expensive
-   Traffic scale is large
-   Microservices are complex
-   System reliability directly impacts revenue

Small teams may combine DevOps and SRE, but large-scale systems separate
them.

------------------------------------------------------------------------

# 6. Career Insight

SRE is a system-level role.

It requires:

-   Strong programming ability
-   Deep understanding of infrastructure
-   Strong distributed system knowledge
-   Clear thinking about risk and trade-offs

SRE is not manual operations.

It is reliability engineering.

------------------------------------------------------------------------

# 7. One Sentence Summary

SRE engineers are software engineers who design, measure, and enforce
system reliability using engineering principles and measurable
objectives.
