# Procurement Agent — AI/ML Implementation Strategy

## 1) AI Strategy Overview

The Procurement Agent is not a single model; it is a set of AI capabilities assembled into a controlled workflow:

- Document drafting (RFP creation, scopes, clauses)
- Vendor evaluation (scoring against rubrics + compliance checks)
- Sourcing optimization (recommendations driven by performance history)
- Multilingual generation (Arabic + English)
- Governance (traceability, audit readiness, policy alignment)

The strategy below deliberately prioritizes **reliability and defensibility** over “demo magic”, because procurement decisions will be audited.

---

## 2) Recommended Models and Frameworks by Capability

### A) RFP Generation (Drafting + Refinement)
**Purpose:** Generate first-draft RFP sections based on structured inputs and entity templates.

Approach:
- Use an LLM for drafting with strong prompt + template control:
  - output constrained to document sections
  - mandatory citations to internal policy references where applicable
- Use a secondary validation pass:
  - checks for missing required clauses
  - checks for prohibited language
  - checks for bilingual formatting requirements

Framework recommendation:
- Orchestrated agent workflow with function calling / tools
- Prompt templates stored and versioned in configuration repository

### B) Vendor Evaluation (Scoring and Explainability)
**Purpose:** Compare vendor proposals with a consistent rubric and reduce subjective variance.

Approach:
- Convert evaluation into **structured scoring**:
  - rubric criteria → JSON schema output
  - numeric scoring + written justification per criterion
- Add a consistency check pass:
  - verify scoring aligns with cited evidence in the proposal
  - flag low-confidence or missing evidence

Model recommendation:
- LLM for evidence extraction + structured scoring output
- Lightweight classifier/regression model (optional Phase 2) trained on historical scoring to detect anomalies

### C) Sourcing Optimization (Recommendation Engine)
**Purpose:** Recommend suppliers based on performance, risk, delivery history, compliance, and cost.

Approach:
- Phase 1: rule-assisted ranking + analytics baseline
- Phase 2: ML ranking model using curated vendor KPIs (learning-to-rank if feasible)
- Phase 3: predictive models for lead time, risk, and contract cycle

Framework recommendation:
- Begin with explainable models first (e.g., gradient boosting / logistic regression for risk)
- Move to ranking models when data is stable and validated

### D) Retrieval-Augmented Generation (RAG)
**Purpose:** Ground outputs in procurement regulations, entity policies, templates, and prior RFP examples.

Approach:
- Build a curated knowledge base:
  - procurement regulations and internal policy documents
  - standard clauses and templates
  - prior RFPs and outcomes (where permitted)
- Use retrieval to provide citations and reduce hallucinations

Framework recommendation:
- Vector store + metadata filters (entity, category, document type, date)
- Strict citation requirements for compliance-facing outputs

---

## 3) Arabic Language Processing Requirements

Arabic procurement/legal text has practical issues:
- morphology and diacritics
- mixed Arabic/English terms
- OCR artifacts from scanned documents
- legal phrasing that depends on context

### Recommended Arabic NLP Components

**Normalization and preprocessing**
- diacritics handling, punctuation normalization, numeral normalization
- Arabic tokenization and stemming/lemmatization (as needed)

**Bilingual generation**
- For Phase 1, treat bilingual documents as:
  - primary language draft + controlled translation pass
  - followed by layout and terminology consistency checks

**Legal terminology governance**
- Maintain a curated glossary:
  - approved translations for procurement/legal terms
  - entity-specific terminology exceptions
- Use glossary constraints during translation and final generation checks

Practical delivery note:
- Arabic quality should be evaluated with legal/procurement SMEs early. “Model accuracy” without SME acceptance is not useful.

---

## 4) Training Data Requirements and Data Preparation

### Data Sources (Expected)
- Oracle procurement history (8+ years)
- RFP documents, clauses, amendments
- Vendor proposals (where accessible and legally permissible)
- Award decisions and evaluation rubrics (if recorded)
- Contract metadata + delivery performance KPIs

### Data Preparation Approach

**Step 1: Data Inventory and Classification**
- identify what is permissible to use for training vs retrieval
- classify data by sensitivity and retention requirements

**Step 2: Data Cleansing and Standardization (15–20%)**
- normalize vendor IDs, categories, item taxonomies
- correct missing/invalid fields
- de-duplicate proposals and outcomes

**Step 3: Labeling Strategy (Phased)**
- Phase 1: minimal labeling to support rubric-based evaluation checks
- Phase 2: supervised labels for recommendation models:
  - vendor performance outcomes
  - delivery delays
  - contract compliance
- Phase 3: refined labels and continuous learning loops (with governance)

**Step 4: Quality Gates**
- sampling-based validation with SMEs
- accuracy baselines agreed upfront:
  - document generation accuracy target >98% (as per service targets)
  - scoring consistency improvement target 40%

**Step 5: Privacy and Compliance Controls**
- remove or redact personal data (where present)
- apply strict access controls for training datasets
- maintain dataset versioning and lineage for audits

---

## 5) Model Evaluation and Acceptance (What “Good” Means)

Procurement systems need measurable acceptance criteria beyond generic NLP metrics.

**Document generation**
- clause completeness against checklist
- bilingual consistency
- audit traceability (citations and version logs)

**Vendor scoring**
- agreement with SME scoring (inter-rater alignment)
- evidence-backed scoring (each score tied to proposal text)

**Recommendations**
- uplift vs baseline manual sourcing
- bias checks (avoid reinforcing historical vendor lock-in)
- explainability (why this vendor ranks higher)

---

## 6) Operationalization (MLOps-lite for Phase 1)

To meet Gitex timelines, MLOps should be pragmatic:

- model version pinning per environment
- prompt + rubric versioning in repo
- offline evaluation suite with golden datasets
- telemetry: latency, failure rates, confidence flags
- rollback strategy: revert to previous model/prompt version if issues arise

