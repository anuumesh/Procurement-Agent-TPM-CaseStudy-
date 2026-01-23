# Risk Scenario 2 — Arabic NLP Accuracy Shortfall

## Scenario Overview

During system testing, Arabic legal document processing accuracy is measured at approximately 65%, significantly below the target threshold of 95%. The external Arabic AI vendor proposes an additional four months of development effort and a 40% budget increase.

This scenario presents both quality and commercial risk requiring immediate strategic response.

---

# Risk Ownership

Primary Owner:
TPM – Program coordination and executive communication

Technical Owner:
AI/ML Lead – Model performance remediation

Business Owner:
Procurement Legal Lead – Validation workflow oversight

Vendor Management Owner:
Commercial Lead – Contract renegotiation and performance enforcement


## Immediate Action Plan

### 1. Conduct Root Cause Analysis Workshop

A joint technical and business workshop will be conducted involving:

- AI Factory engineering team  
- Arabic NLP vendor specialists  
- Procurement legal subject matter experts  
- Data engineering team  

Objectives:

- Identify root causes of accuracy degradation  
- Separate data quality issues from model architecture limitations  
- Assess labeling coverage gaps  
- Evaluate terminology mismatch in legal vocabulary  

---

### 2. Segment Arabic NLP Use Cases by Complexity

Arabic NLP requirements will be categorized into tiers:

**Tier 1 — Standard Procurement Templates**  
- Common RFP clauses  
- Standard legal language patterns  

**Tier 2 — Entity-Specific Variations**  
- Department-specific formats  
- Specialized procurement terminology  

**Tier 3 — Complex Legal Interpretations**  
- Regulatory edge cases  
- Contractual dispute language  

This segmentation allows phased capability rollout rather than treating all use cases as equal complexity.

---

### 3. Implement Human-in-the-Loop Validation Layer

To protect business usability, a controlled validation workflow will be introduced:

- AI generates Arabic draft content  
- Legal or procurement SME reviews and approves  
- Feedback is captured to improve training datasets  

This ensures compliance while allowing AI capability to mature progressively.

---

## Impact Assessment

### Timeline Impact

- Phase 1 delivery remains on schedule  
- Full autonomous Arabic legal interpretation deferred to Phase 2  
- Manual validation incorporated into initial rollout  

---

### Budget Impact

- Vendor request for 40% increase is rejected  
- Internal AI Factory engineering resources reallocated  
- Performance-based milestone renegotiation with vendor  

Expected budget impact maintained within existing contingency buffer (under 10%).

---

### Scope Impact

**Phase 1 Scope Adjustment:**

- Arabic document drafting enabled  
- Assisted legal review workflow introduced  
- Fully autonomous legal interpretation postponed  

This preserves bilingual functionality while maintaining compliance standards.

---

# AI Risk Classification

High-Risk Use Case:
Arabic legal interpretation and contract-related outputs

Medium-Risk Use Case:
Arabic RFP drafting and summarization

Control Strategy:
High-risk outputs require mandatory human validation.
Medium-risk outputs allowed with sampling-based review.

# Decision Authority

Model Architecture Changes:
Approved by AI Governance Committee

Scope Changes:
Approved by Steering Committee

Validation Workflow Changes:
Approved by Legal Compliance Office

# Post-Phase 1 Improvement Plan

Month 1–2:
Expand labeled Arabic datasets

Month 3:
Retrain domain-specific language model

Month 4:
Reduce manual validation coverage by 30%

Quarterly:
Governance review of automation readiness



## Alternative Solutions and Trade-Off Analysis

### Option A — Accept Vendor Proposal  
**Decision: Rejected**

**Pros:**
- Potential long-term accuracy improvement  

**Cons:**
- Budget overrun  
- Phase 1 delivery delay  
- Weak cost governance signal  

---

### Option B — Remove Arabic Support from Phase 1  
**Decision: Rejected**

**Pros:**
- Simplified AI implementation  

**Cons:**
- Politically unacceptable  
- Violates inclusivity and language policy requirements  
- Reduces user adoption potential  

---

### Option C — Progressive Automation with Validation Layer (Selected)

**Pros:**
- Maintains bilingual support  
- Protects delivery timeline  
- Reduces operational risk  
- Improves model performance iteratively  

**Cons:**
- Temporary operational overhead for reviewers  

**Rationale:**  
Government procurement environments accept staged automation when auditability and accuracy controls are preserved.

---

## Outcome Objective

The objective is to achieve reliable Arabic language support for Phase 1 delivery while establishing a sustainable improvement path toward full automation without sacrificing governance or budget discipline.
