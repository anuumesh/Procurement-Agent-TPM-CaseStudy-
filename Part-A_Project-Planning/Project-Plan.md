# Procurement Agent – Delivery Plan

## Delivery Approach

Given the public-sector environment and dependency on legacy systems, the project has been structured using a controlled phased rollout approach.

This enables early delivery of high-value automation capabilities while progressively de-risking data quality, system integration, and regulatory approval processes.

## Program Governance Structure

# Steering Committee:
- CIO (Executive Sponsor)
- Head of Procurement
- Cybersecurity Director
- Legal Compliance Officer

# Responsibilities:
- Monthly milestone approval
- Budget gate approvals
- Risk acceptance decisions
- Production go-live authorization

# Delivery Authority:
The TPM retains operational ownership with escalation authority to the Steering Committee for scope, risk, and compliance decisions.


---

## Phase 1 – MVP (Gitex Release)

### Core Objectives

The primary focus of Phase 1 is to demonstrate tangible automation impact while maintaining delivery reliability.

Key deliverables include:

- Automated RFP document generation
- Initial vendor evaluation scoring model
- Oracle Fusion ERP integration (read/write workflows)
- Arabic and English document generation
- Security baseline and access controls

---

### Phase 1 Work Breakdown Structure

**Program Setup**
- Governance framework establishment  
- Architecture design approval  
- Security baseline alignment
- Program Reporting Cadence

Weekly:
Delivery progress report
Risk register update
Dependency tracking

Monthly:
Executive steering update
Budget and KPI review

**Data Enablement**

- Procurement data profiling  
- Data cleansing pipeline development  
- Oracle schema normalization  

**AI Platform Development**

- RFP generation pipeline  
- Evaluation scoring model  
- Arabic NLP preprocessing module  

**Integration Layer**

- ERP API integration  
- Identity federation (ADFS)  
- Role-based access control
- Data Residency Controls

- All workloads hosted in UAE cloud regions
- No procurement data stored outside national boundaries
- Encryption at rest and transit enabled
- Access restricted through government IAM

**Testing & Validation**

- User acceptance testing  
- Performance benchmarking  
- Security penetration testing  

Operational Incident SLAs

P0 (System Outage):
Response: 15 minutes
Resolution Target: 2 hours

P1 (Partial Failure):
Response: 1 hour
Resolution Target: 6 hours

Post-Incident:
Mandatory RCA within 48 hours

---

## Major Milestones

| Milestone | Target Timeline |
---------------------------
Architecture Approval | Week 2
Data Pipeline Ready | Week 4
AI MVP Functional | Week 6
ERP Integration Complete | Week 7
Security Certification | Week 8
Gitex Go-Live | Week 9

# Approval Control Gates

Gate 1 – Architecture Approval (Week 2)
- Security architecture sign-off
- Integration design approval

Gate 2 – Data Governance Approval (Week 4)
- Data classification validation
- Privacy compliance clearance

Gate 3 – Pre-GoLive Approval (Week 7)
- Security certification
- Performance benchmark approval

Gate 4 – Production Release Authorization (Week 8)
- Steering Committee sign-off

---

## Critical Path Dependencies

The following dependency chain has been identified as schedule-critical:

Oracle Fusion API Access  
→ Historical Data Cleansing  
→ AI Model Training  
→ Integration Testing  
→ Security Accreditation  
→ Production Deployment  

Delays in any of these stages will directly impact the Gitex delivery milestone.

---

## Resource Allocation Strategy

Given the 12 FTE constraint, the delivery team has been structured to balance technical delivery capacity with governance and compliance oversight.

# Responsibility Matrix (RACI)

# Program Delivery
Responsible: TPM
Accountable: CIO
Consulted: Product, Security
Informed: Business Stakeholders

# ERP Integration
Responsible: Backend Lead
Accountable: TPM
Consulted: Oracle Vendor
Informed: IT Operations

# Security Compliance
Responsible: Security Lead
Accountable: CISO
Consulted: Legal
Informed: Steering Committee

# AI Accuracy
Responsible: ML Lead
Accountable: TPM
Consulted: Procurement SMEs
Informed: QA Team

| Role | Allocation |
-------------------------
Technical Program Manager | 1
Product Manager | 1
AI Engineers | 3
Backend Engineers | 3
Data Engineers | 2
Security Engineer | 1
QA Engineer | 1

Where required, short-term specialist vendors will be engaged for Arabic NLP fine-tuning and Oracle ERP advisory support.

---

# Change Management Strategy

- Early stakeholder demos during Phase 1
- Procurement user pilot group onboarding
- Training sessions before Gitex launch
- Feedback capture loop during MVP phase

# Objective:
Ensure business adoption readiness prior to public launch exposure.

## Training & Enablement Plan

# Training Modules:
- Procurement Officer Portal Usage
- Vendor Interaction Handling
- AI Escalation Workflow

# Delivery Method:
- Live workshops
- Recorded training modules
- Knowledge base documentation

# Target Adoption:
Minimum 70% procurement staff onboarded before Phase 2.



## Risk Management – Priority Risks

### ERP Integration Risk  
Oracle Fusion APIs are partially documented and inconsistent across environments.

Mitigation:  
An abstraction layer will be implemented to isolate downstream services from ERP instability. Caching and asynchronous retries will be used to protect system availability.

---

### Data Quality Risk  
Historical procurement data contains estimated 15–20% inconsistencies.

Mitigation:  
Automated cleansing rules combined with targeted manual sampling will be implemented during Phase 1.

---

### Arabic Legal Language Accuracy Risk  

Mitigation:  
Fine-tuning will be performed using government legal and procurement document datasets to improve contextual understanding.

---

### Security Approval Timeline Risk  

Mitigation:  
Security teams will be embedded into sprint planning from project initiation to avoid late-stage compliance bottlenecks.

---

### Budget Control Risk  

Mitigation:  
Phase-based funding gates and milestone-based vendor payments will be enforced.

---

## Go / No-Go Decision Gates

# Post Go-Live Support Model

# Hypercare Period:
First 14 days after Gitex release

# Support Coverage:
- Dedicated on-call engineering support
- Real-time monitoring dashboard
- Incident triage team

# Stabilization Exit Criteria:
- Zero P0 incidents for 5 consecutive days
- Performance SLA stability achieved


### Phase 1 Release Criteria

- RFP document generation accuracy ≥ 95%  
- ERP transaction latency under 5 seconds  
- Security penetration testing approval  
- Business user sign-off  

---

### Phase 2 Expansion Criteria

- Vendor scoring accuracy improvement ≥ 40%  
- System uptime stable at 99.5%  
- Multi-entity onboarding readiness  

---

### Phase 3 Enterprise Rollout Criteria

- Verified annual cost savings ≥ AED 5M  
- Performance stability under peak workloads  
- Regulatory compliance audit approval  
