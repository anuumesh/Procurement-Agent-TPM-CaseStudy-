# Risk Management and Problem Solving — Procurement Agent Program

This section outlines response strategies for two high-impact risk scenarios that may occur during delivery. The approach focuses on maintaining business commitments, protecting regulatory obligations, and preserving stakeholder confidence while managing technical constraints.

---

# Scenario 1  
ERP System Requires Major Upgrade with 6-Week Downtime  
(Project Launch Cannot Be Delayed)

## Situation Summary

Three months into delivery, it is identified that Oracle Fusion ERP requires a mandatory version upgrade. The upgrade introduces a 6-week downtime window. Phase 1 delivery timeline (Gitex) cannot be postponed due to public commitments and executive visibility.

---

## Immediate Action Plan (First 72 Hours)

### 1. Establish War Room Governance

- Initiate joint task force involving:
  - Department of Finance ERP team
  - Oracle vendor support
  - AI Factory engineering leads
  - Program governance representatives
- Daily checkpoint cadence initiated immediately.

---

### 2. Technical Impact Assessment Sprint (48 Hours)

- Identify:
  - Which Procurement Agent features depend on live ERP writes
  - Which features only require read access
  - Data objects impacted by version changes
- Categorize workflows into:
  - ERP-dependent
  - ERP-independent
  - ERP-optional

---

### 3. Activate Business Continuity Architecture

Implement temporary fallback strategies:

- Snapshot procurement master data prior to downtime
- Enable read-only cached datasets for Phase 1 demo workflows
- Disable production write-back features for MVP release window

---

### 4. Executive Alignment

- Conduct emergency Steering Committee session
- Re-baseline Phase 1 scope while preserving public demo commitments
- Secure approval for controlled functional degradation plan

---

## Impact Assessment

### Timeline Impact

- Core AI development timeline remains unchanged
- ERP write-back integration postponed to post-upgrade window
- Phase 1 delivery date preserved

---

### Budget Impact

- Minor increase in engineering effort for temporary abstraction layer
- No major vendor or infrastructure cost impact
- Contingency buffer allocation used (~5–8%)

---

### Scope Impact

Phase 1 adjusted scope:

**Delivered:**
- RFP automation
- Vendor evaluation AI
- Analytics dashboards
- Document generation

**Deferred:**
- Live ERP transaction write-back
- Automated procurement submission

ERP transactional automation moved to Phase 2 stabilization sprint.

---

## Alternative Solutions and Trade-Off Analysis

### Option A — Delay Phase 1 Launch  
❌ Rejected

Pros:
- Clean integration timeline

Cons:
- Public commitment failure
- Executive credibility impact
- Reputational risk during Gitex

---

### Option B — Proceed Without ERP Integration Entirely  
❌ Rejected

Pros:
- Simplifies deployment

Cons:
- Weak business value demonstration
- Reduced stakeholder confidence

---

### Option C — Hybrid MVP Mode (Selected)

Pros:
- Preserves public delivery milestone
- Demonstrates AI value immediately
- Maintains ERP compatibility readiness

Cons:
- Temporary manual reconciliation required
- Additional coordination effort

Rationale:
This approach balances political, business, and technical realities without sacrificing delivery credibility.

---

# Scenario 2  
Arabic NLP Accuracy at 65% vs Required 95%  
Vendor Requests 4-Month Delay and 40% Budget Increase

## Situation Summary

During testing, Arabic legal document processing accuracy is significantly below target. External AI vendor proposes extended timeline and major cost increase.

---

## Immediate Action Plan (First 7 Days)

### 1. Root Cause Analysis Workshop

Joint working session involving:

- AI Factory engineers
- Arabic NLP vendor
- Procurement legal SMEs
- Data engineering team

Objective:
Identify whether accuracy issues stem from:
- Data quality
- Labeling gaps
- Domain vocabulary mismatch
- Model architecture limitations

---

### 2. Segment Use Case Complexity

Split Arabic NLP requirements into tiers:

- Tier 1: Standard procurement clauses
- Tier 2: Entity-specific templates
- Tier 3: Complex legal interpretations

This allows prioritization instead of blanket accuracy expectations.

---

### 3. Implement Controlled Human-in-the-Loop Process

Introduce validation layer for high-risk legal outputs:

- AI generates draft
- SME reviews and approves
- Feedback loop feeds model improvement

This ensures business usability while AI matures.

---

## Impact Assessment

### Timeline Impact

- Phase 1 delivery remains on schedule
- Full automation accuracy target deferred to Phase 2
- Manual validation layer introduced temporarily

---

### Budget Impact

- Reject 40% vendor increase proposal
- Reallocate internal AI Factory engineering resources
- Negotiate performance-based vendor milestones

Expected net increase: under 10% contingency buffer.

---

### Scope Impact

Phase 1 adjusted expectations:

- Arabic document drafting enabled
- Legal validation workflow added
- Full autonomous legal interpretation deferred

---

## Alternative Solutions and Trade-Off Analysis

### Option A — Accept Vendor Proposal  
❌ Rejected

Pros:
- Potential quality improvement

Cons:
- Budget overrun
- Delivery delay
- Weak commercial leverage

---

### Option B — Remove Arabic Support from Phase 1  
❌ Rejected

Pros:
- Simplifies technical risk

Cons:
- Politically unacceptable
- Breaks government inclusivity mandate

---

### Option C — Hybrid Automation with Progressive Improvement (Selected)

Pros:
- Preserves bilingual capability
- Maintains Phase 1 timeline
- Reduces risk exposure
- Allows gradual accuracy improvement

Cons:
- Requires temporary manual validation overhead

Rationale:
Government procurement tolerates staged automation provided audit controls remain intact.

---

# Program-Level Risk Management Principles Applied

Across both scenarios, the following principles guided decisions:

- Protect public delivery commitments  
- Preserve regulatory compliance  
- Maintain executive stakeholder trust  
- Prioritize business continuity  
- Avoid single-vendor dependency  
- Use phased capability maturity  

These principles ensure resilience across political, technical, and operational constraints.
