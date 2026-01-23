# Procurement Agent — Technical Architecture (High-Level)

## 1) Architecture Intent and Design Principles

This architecture is designed to meet two realities in parallel:

1) **Government-grade governance** (auditability, data protection, predictable operations), and  
2) **AI product delivery velocity** (Gitex MVP pressure, iterative rollout across entities).

Design principles applied:

- **Separation of concerns**: isolate Oracle Fusion integration, AI orchestration, and document services to reduce blast radius.
- **Audit-first**: every AI output must be traceable to inputs, versions, and approvals (especially for procurement).
- **Defense-in-depth**: identity, access, encryption, logging, and policy enforcement are not “Phase 2 items”.
- **Phased scalability**: scale patterns proven in Phase 1 before enabling full government-wide rollout.

---

## 2) High-Level System Architecture

### Core Components

**A. Experience Layer**
- Web portal for procurement officers (entity users)
- Admin console for configuration, prompts/policies, templates, and approvals
- API gateway for chatbot/agent access (if required in later phases)

**B. Agent & Orchestration Layer**
- Procurement Agent Orchestrator (workflow engine for RFP creation, evaluation, sourcing)
- Tool/Function Router (routes to ERP, analytics, doc-gen, translation, vector search)
- Policy Guardrails (prompt policies, PII redaction rules, prohibited actions)

**C. AI Services Layer**
- LLM Service (generation, summarization, reasoning)
- Retrieval (vector search over policies, historical RFPs, vendor documents)
- Translation + Arabic language normalization service
- Evaluation Service (structured scoring, rubric alignment, consistency checks)

**D. Data & Integration Layer**
- Oracle Fusion Integration Service (API adaptor + mapping + retry/caching)
- Procurement Data Lake / Storage (curated + raw zones)
- Feature store / analytics store (vendor performance, KPIs)
- Audit event store (immutable logs, approvals, model versions)

**E. Platform & Security Layer**

# Cost Governance Controls

# Monitoring:
- Compute consumption
- AI inference usage
- Storage growth

# Controls:
- Budget alerts
- Resource quotas per entity
- Cost allocation tagging

# Reporting:
Monthly cost optimization review with finance stakeholders.

- Identity via ADFS (federation)
- Key management and secrets vault
- Centralized logging, monitoring, SIEM forwarding
- CI/CD pipelines with gated releases
- Release Governance Workflow

1. Automated testing validation
2. Security scan approval
3. Compliance checkpoint
4. TPM release signoff
5. Steering Committee approval (for production)

Production deployments restricted to approved release windows.

- Observability Architecture

Metrics:
- API latency
- ERP integration success rates
- AI inference response times

Logs:
- Application logs
- Security audit logs
- User action logs

Tracing:
- End-to-end request tracing across agent, ERP, AI services

Dashboards:
Centralized executive dashboard for operational health visibility.

---
## Environment Segmentation Strategy

Separate isolated environments will be maintained:

Development:
- Feature development and experimentation
- Synthetic and masked data only

Testing / Staging:
- Integration testing with Oracle sandbox
- Security validation
- Performance benchmarking

Production:
- Live government workloads
- Restricted access controls
- Full audit logging enabled

Promotion between environments requires gated approval workflows.

## 3) Integration Points with Existing Systems

### Oracle Fusion ERP (Primary Integration)

# Key integration patterns:
- **Read**: supplier master data, purchase orders, historical RFP outcomes, contracts metadata
- **Write**: draft RFP objects, evaluation results, recommendation notes (where policy allows)
- **Near-real-time sync**: event-driven where feasible; otherwise scheduled deltas with strict SLAs
ERP Failure Fallback Behavior

If Oracle Fusion ERP is unavailable:

- Switch system to read-only mode
- Queue write transactions for later replay
- Notify users of temporary limitations
- Preserve audit traceability for delayed operations

Objective:
Maintain continuity without corrupting transactional integrity.


# Integration considerations:
- Legacy APIs may be inconsistent. We will implement an **anti-corruption layer**:
  - canonical procurement data model
  - schema mapping + validation
  - idempotent writes
  - retry policies + dead-letter handling

### Active Directory Federation Services (ADFS)
- SSO for government users
- Role mapping by entity and procurement role (e.g., requester, evaluator, approver)
- Access decisions enforced both at UI and API gateway

### Compliance / Audit Systems (If Applicable)
- Exportable audit trail reports (who generated what, on what data, who approved)
- Event streaming to existing government SIEM or monitoring platforms

---

## 4) Scalability for Government-Wide Deployment

### Deployment Model
- Start with a **single-tenant-per-entity logical model** on shared infrastructure:
  - strong logical isolation (RBAC + data partitioning)
  - per-entity configuration & templates
  - per-entity encryption keys (recommended)

# Scale-out capabilities:
- horizontally scalable stateless services (orchestrator, API gateway, doc-gen)
- separate scaling policies for:
  - inference workloads
  - retrieval workloads
  - integration workloads
 
 # Disaster Recovery Strategy

Recovery Objectives:
RTO (Recovery Time Objective): 2 hours
RPO (Recovery Point Objective): 15 minutes

Controls:
- Automated backups
- Cross-zone replication
- Infrastructure-as-code redeployment capability

Failover Testing:
Quarterly DR simulation exercises to validate readiness.


### Key Scaling Controls
- request throttling per entity (to protect Oracle Fusion + platform stability)
- caching of reference data (vendor master, policy texts, template libraries)
- async processing for heavy operations (large document evaluation, bulk comparisons)

Performance target alignment:
- Response time < 8 seconds for standard queries:
  - “standard” defined as typical RFP generation and structured summary tasks
  - long-running evaluations should return a job ID + progress status

Availability target alignment:
- 99.5% uptime:
  - multi-zone deployment where applicable
  - graceful degradation patterns (read-only mode if ERP is unstable)

---

## 5) Security and Compliance Considerations

### Data Protection
- encryption in transit (TLS) and at rest
- restricted access by role and entity boundary
- retention rules aligned with procurement regulation and audit requirements
- data minimization: only store what is needed for traceability and performance
- Data Lifecycle Management

Retention Policies:
- Procurement transaction data retained as per regulatory mandate
- Audit logs retained for minimum compliance duration
- Temporary inference artifacts purged automatically

Archival Strategy:
Cold storage for historical RFPs and closed procurement records.

Deletion Controls:
Role-based approval required for any permanent deletion.


### Model & Prompt Governance
- versioned prompts, templates, rubrics
- approval workflow for production prompt changes
- model version pinning per environment (dev/test/prod)
- AI Safety Controls

Hard Guardrails:
- Prohibited content filters
- Financial and legal output validation rules

Human-in-the-Loop:
- Mandatory approval for final RFP submissions
- Manual override for critical procurement decisions

Fallback Handling:
Low-confidence AI outputs routed to manual review queues.

### Auditability
Every AI output must record:
- user identity and entity
- input sources and document IDs
- retrieved references (policy sections, previous RFPs)
- model version + prompt version
- approval decision and timestamps

### Compliance Alignment (Practical Controls)
- ISO 27001 controls mapped to:
  - asset management (data classification)
  - access control (RBAC, least privilege)
  - logging and monitoring (immutable logs, SIEM forwarding)
  - change management (gated release approvals)
- UAE Data Protection:
  - residency requirements (within approved cloud region / boundary)
  - PII handling controls (redaction, restricted retrieval)

---

## 6) Key Technical Decisions and Trade-offs (Documented)

- **Decision:** Use an orchestration layer instead of a single monolithic agent.
  - Rationale: reduces risk, improves auditability, and isolates ERP integration.
- **Decision:** Treat vendor evaluation as “structured scoring” rather than free-form LLM output.
  - Rationale: defensible outcomes, consistent evaluation, easier audit reviews.
- **Decision:** Introduce async processing for heavyweight tasks.
  - Rationale: keeps user experience responsive while meeting <8s requirement for standard tasks.

