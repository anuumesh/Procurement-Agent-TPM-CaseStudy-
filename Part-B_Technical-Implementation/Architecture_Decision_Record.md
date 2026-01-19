# Architecture Decision Record (ADR)
Procurement Agent Program — AI Factory

Document Purpose:  
This ADR captures key technical and architectural decisions made during the design phase of the Procurement Agent platform. The intent is to document rationale, trade-offs, and constraints in a transparent manner suitable for audit, governance, and long-term maintainability.

---

## ADR-001: Adopt Layered Architecture with Orchestration Layer

### Decision  
Implement a layered architecture with a dedicated orchestration layer between user-facing applications and backend services.

### Context  
The Procurement Agent integrates AI services, ERP systems, document generation, translation services, and compliance workflows. A direct point-to-point integration model would increase coupling and operational risk.

### Rationale  
- Enables separation of AI logic from ERP integration complexity  
- Improves traceability and audit control over workflow steps  
- Allows independent scaling of AI inference and integration services  
- Simplifies future expansion of new agents or workflows  

### Alternatives Considered  
- Monolithic AI service directly calling ERP APIs  
- Event-only architecture without centralized orchestration  

### Why Rejected  
- Monolithic approach increases deployment risk and audit complexity  
- Pure event-driven model adds unnecessary operational overhead for Phase 1 delivery timeline  

---

## ADR-002: Use Retrieval-Augmented Generation (RAG) Instead of Pure LLM Generation

### Decision  
Adopt a retrieval-augmented generation pattern for all compliance-related outputs.

### Context  
Procurement outputs must align with government regulations, approved clauses, and internal policies. Free-form generation without grounding introduces compliance and legal risk.

### Rationale  
- Enables citation-based outputs  
- Reduces hallucination risk  
- Improves audit traceability  
- Allows policy updates without retraining base models  

### Alternatives Considered  
- Fully fine-tuned domain model  
- Prompt-only grounding  

### Why Rejected  
- Full fine-tuning is costly and slow for regulatory changes  
- Prompt-only grounding is difficult to validate and audit  

---

## ADR-003: Structured Vendor Evaluation Instead of Free-Text AI Assessment

### Decision  
Design vendor evaluation as a structured scoring workflow rather than open-ended AI-generated assessments.

### Context  
Procurement evaluations require defensible, consistent scoring aligned to published rubrics.

### Rationale  
- Enables standardized scoring across entities  
- Improves explainability and acceptance by audit teams  
- Reduces reviewer subjectivity  
- Supports future analytics and benchmarking  

### Alternatives Considered  
- Narrative-only AI summaries  
- Manual evaluation assisted by AI suggestions  

### Why Rejected  
- Narrative outputs are harder to audit  
- Manual-heavy workflows do not meet cycle time reduction targets  

---

## ADR-004: ERP Integration via Anti-Corruption Layer

### Decision  
Implement an abstraction layer between the Procurement Agent platform and Oracle Fusion ERP.

### Context  
Oracle Fusion APIs are partially documented and vary between environments and modules.

### Rationale  
- Protects platform logic from ERP schema changes  
- Enables consistent internal data model  
- Simplifies testing and sandbox simulation  
- Improves resilience against upstream failures  

### Alternatives Considered  
- Direct API integration per use case  

### Why Rejected  
- Tight coupling increases maintenance cost  
- Higher operational risk during upgrades  

---

## ADR-005: Phased Scalability Instead of Immediate Full Government Rollout

### Decision  
Adopt phased rollout starting with controlled MVP deployment before enabling full government-wide usage.

### Context  
System stability, integration reliability, and AI accuracy must be proven in real operational conditions before scaling.

### Rationale  
- Reduces operational risk  
- Enables performance tuning based on real usage patterns  
- Allows security controls to be validated under load  
- Improves stakeholder confidence  

### Alternatives Considered  
- Big-bang multi-entity deployment  

### Why Rejected  
- High risk of service disruption  
- Difficult incident management across multiple departments  

---

## ADR-006: Hybrid Cloud AI Service Strategy

### Decision  
Use managed cloud AI services initially, with architecture flexibility to introduce self-hosted models later if required by policy.

### Context  
Time-to-market constraints for Gitex require rapid deployment, while future regulatory requirements may mandate tighter model control.

### Rationale  
- Accelerates MVP delivery  
- Reduces infrastructure complexity  
- Keeps future on-premise or sovereign AI options open  

### Alternatives Considered  
- Fully self-hosted LLM infrastructure  
- Vendor-locked single-provider AI stack  

### Why Rejected  
- Self-hosting adds operational complexity and delays Phase 1  
- Hard vendor lock-in reduces long-term flexibility  

---

## ADR-007: Asynchronous Processing for Heavy Workloads

### Decision  
Use asynchronous job processing for large document evaluations and batch comparisons.

### Context  
Some procurement evaluations involve large files and multiple vendor submissions.

### Rationale  
- Maintains responsive user experience  
- Prevents API timeouts  
- Enables better resource utilization  

### Alternatives Considered  
- Synchronous blocking requests  

### Why Rejected  
- Violates response time SLAs  
- Poor user experience for complex workflows  

---

## ADR-008: Prompt and Model Version Governance

### Decision  
Treat prompts, rubrics, and model versions as governed configuration artifacts.

### Context  
Changes to prompts and evaluation logic directly affect procurement outcomes.

### Rationale  
- Enables rollback capability  
- Supports audit traceability  
- Allows controlled experimentation  
- Aligns with ISO change management practices  

### Alternatives Considered  
- Hardcoded prompt logic inside application services  

### Why Rejected  
- High operational risk  
- No version traceability  
- Difficult incident recovery  

---

## Summary

These architecture decisions were made with the following guiding priorities:

- Regulatory compliance and auditability  
- Delivery reliability under public-sector constraints  
- Phased scalability and risk control  
- Operational maintainability  
- Business outcome alignment  

All decisions will be reviewed periodically as the platform evolves across Phase 2 and Phase 3 rollouts.

