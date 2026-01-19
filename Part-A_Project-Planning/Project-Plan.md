# Procurement Agent – Delivery Plan

## Delivery Approach

Given the public-sector environment and dependency on legacy systems, the project has been structured using a controlled phased rollout approach.

This enables early delivery of high-value automation capabilities while progressively de-risking data quality, system integration, and regulatory approval processes.

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

**Testing & Validation**

- User acceptance testing  
- Performance benchmarking  
- Security penetration testing  

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
