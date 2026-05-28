# AI Risk Assessment Calculator: Instructions

**Version:** 3.1  
**Based on:** AI Agentic Governance Framework v3.1 (2026-05-28)  
**File:** `AI_Risk_Assessment_Calculator_v3.1.xlsx`

---

## Purpose

This workbook calculates the **inherent and residual risk** of implementing AI in an application, system, or software. It evaluates risk based on:

- Information classification (confidentiality, integrity, availability)
- Personal data processing (regular vs. sensitive under GDPR Art. 9)
- Exposure (intranet, B2B, or internet-facing)
- Business criticality
- Regulatory relevance (UNECE R155/R156 for carIT)
- System maturity (forefront, current, legacy, end-of-life)
- AI integration depth and tool access scope
- Implemented governance controls from the framework (107 controls across 14 risk domains)

---

## Workbook Structure

| Sheet | Purpose | Action Required |
|-------|---------|-----------------|
| **Instructions** | Usage guide and scoring reference | Read only |
| **Risk Assessment** | Main input/output — system characteristics and calculated risk | Fill YELLOW cells |
| **Control Selection** | Mark which of the 107 controls are implemented | Fill YELLOW cells (Yes/No/Partial/N/A) |
| **Risk Matrix** | Visual 5x5 matrix and control requirement reference | Read only |
| **Control Catalog** | Full catalog of 107 controls with priority and applicability | Read only |

---

## How to Use

### Step 1: Fill in System Characteristics (Risk Assessment tab)

Open the **Risk Assessment** tab and complete all **YELLOW** cells:

**Header Information:**
- System/Application Name
- Assessment Date
- Assessor
- Business Unit / Owner

**Section 1 — Impact Factors (6 selections):**
Choose from the dropdown lists for each factor.

**Section 2 — Likelihood Factors (5 selections):**
Choose from the dropdown lists for each factor.

### Step 2: Mark Implemented Controls (Control Selection tab)

Open the **Control Selection** tab. For each of the 107 controls, select from the dropdown in the **"Implemented?"** column:

| Selection | Meaning | Weighted Credit |
|-----------|---------|-----------------|
| **Yes** | Control is fully implemented and operational | 100% of weight |
| **Partial** | Control is partially implemented or in progress | 50% of weight |
| **No** | Control is not implemented | 0% |
| **N/A** | Control is not applicable to this system | Excluded from calculation |

Add notes in the **Notes** column to document evidence, exceptions, or planned implementation dates.

### Step 3: Review Results (Risk Assessment tab)

Return to the **Risk Assessment** tab. The GREEN cells now show:

- **Impact Score** (1–5)
- **Likelihood Score** (1–5)
- **Inherent Risk** (1–25) — before controls
- **Control Effectiveness** (0–100%) — from your control selections
- **Residual Risk** (1–25) — after controls

**Section 4** provides automated recommendations for control tiers, data classification handling, GDPR requirements, UNECE relevance, and AI-specific risk controls.

---

## Scoring Model

### Risk Formula

```
Inherent Risk  = Impact Score × Likelihood Score
Residual Risk  = Inherent Risk × (1 - Control Effectiveness %)
```

### Impact Score (normalized 1–5)

Derived from 6 factors with a maximum raw score of 22:

| Factor | Options | Score |
|--------|---------|-------|
| **Confidentiality Level** | Public | 1 |
| | Internal | 2 |
| | Confidential | 3 |
| | Restricted | 4 |
| **Integrity Level** | Low | 1 |
| | Medium | 2 |
| | High | 3 |
| | Very High | 4 |
| **Availability Level** | Low | 1 |
| | Medium | 2 |
| | High | 3 |
| | Mission-Critical | 4 |
| **Personal Data Processing** | None | 0 |
| | Regular Personal Data (names, emails, IDs) | 2 |
| | Sensitive PD — Art. 9 GDPR (health, biometric, ethnic, political) | 4 |
| **Business Criticality** | Supporting | 1 |
| | Important | 2 |
| | Critical | 3 |
| | Mission-Essential | 4 |
| **UNECE R155/R156 (carIT)** | No | 0 |
| | Indirect (supply chain) | 1 |
| | Direct (vehicle systems) | 2 |

**Normalization:** `Impact = 1 + (Sum of Scores / 22) × 4`

### Likelihood Score (normalized 1–5)

Derived from 5 factors with a maximum raw score of 19:

| Factor | Options | Score |
|--------|---------|-------|
| **Exposure / Attack Surface** | Intranet only | 1 |
| | B2B/Partner network | 2 |
| | Internet-facing | 3 |
| **System Age / Technology** | Forefront/New | 1 |
| | Current/Maintained | 2 |
| | Legacy | 3 |
| | End-of-Life | 4 |
| **AI Integration Depth** | Isolated task (code suggestions) | 1 |
| | Workflow integrated | 2 |
| | Autonomous agent | 3 |
| | Multi-agent system | 4 |
| **Data Volume Processed by AI** | Minimal (<100 files) | 1 |
| | Moderate (100–1000) | 2 |
| | Large (1000–10000) | 3 |
| | Massive/Continuous (>10000) | 4 |
| **AI Tool Access Scope** | Read-only (code review) | 1 |
| | Read+Write (edit files) | 2 |
| | Shell execution | 3 |
| | Full access (Network+Shell+Files) | 4 |

**Normalization:** `Likelihood = 1 + (Sum of Scores / 19) × 4`

### Control Effectiveness (weighted %)

Controls are weighted by priority:

| Priority | Weight | Requirement |
|----------|--------|-------------|
| P1 — Critical | 3 | Mandatory for all risk levels |
| P2 — High | 2 | Mandatory for High/Critical risk; Recommended for Medium |
| P3 — Medium | 1 | Mandatory for Critical; Recommended for High; Optional for Medium/Low |

```
Effectiveness = Sum(Implemented Weight) / Sum(Total Weight)
```

Where:
- "Yes" = full weight
- "Partial" = 50% of weight
- "No" = 0
- "N/A" = excluded from both numerator and denominator

---

## Risk Levels

| Score | Level | Color | Meaning |
|-------|-------|-------|---------|
| **20–25** | CRITICAL | Red | AI implementation **PROHIBITED** without full P1+P2+P3 controls and CISO+DPO+CTO approval |
| **12–19** | HIGH | Orange | All P1 controls mandatory. P2 strongly recommended. CISO formal risk acceptance required |
| **6–11** | MEDIUM | Yellow | P1 mandatory. P2 recommended. Standard Tech Lead approval |
| **1–5** | LOW | Green | Standard guardrails sufficient. Self-service approval |

---

## Control Requirements by Risk Level

| Risk Level | P1 Controls | P2 Controls | P3 Controls | Approval Authority | DPIA Required | Review Cycle |
|------------|-------------|-------------|-------------|-------------------|---------------|--------------|
| **Critical** | MANDATORY | MANDATORY | MANDATORY | CISO + DPO + CTO | Always | Quarterly |
| **High** | MANDATORY | MANDATORY | Recommended | CISO | If personal data | Semi-annual |
| **Medium** | MANDATORY | Recommended | Optional | Tech Lead | If sensitive PD | Annual |
| **Low** | MANDATORY | Optional | Optional | Self-service | Only if Art. 9 data | Annual |

---

## Data Classification and AI Access Rules

| Classification | AI Access Rule | Required Controls |
|---------------|----------------|-------------------|
| **Public** (Score 1) | Unrestricted use with AI assistants | Standard output review |
| **Internal** (Score 2) | Permitted with standard guardrails | DLP scanning, audit logging |
| **Confidential** (Score 3) | Restricted: DLP verification, PII redaction, approval | Full DLP pipeline, PII tokenization, manager approval, enhanced logging |
| **Restricted** (Score 4) | **PROHIBITED** from AI assistant transmission | Block at network/DLP layer. No exceptions without CISO + DPO approval |

---

## GDPR Decision Logic

| Personal Data Selection | Automated Recommendation |
|------------------------|--------------------------|
| **None** | No personal data processing — standard controls apply |
| **Regular Personal Data** | GDPR applies. Legal basis required (Art. 6). PII tokenization before AI processing. Processing records (Art. 30) |
| **Sensitive PD (Art. 9)** | DPIA MANDATORY (Art. 35). Full GDPR controls (GD-01 to GD-10) required. Special category data safeguards |

---

## UNECE R155/R156 Decision Logic

| Selection | Automated Recommendation |
|-----------|--------------------------|
| **No** | Not carIT relevant. Standard framework controls apply |
| **Indirect** | Consider CSMS alignment and automotive supply chain controls (SC-01 to SC-08) |
| **Direct** | Vehicle CSMS integration required. AI controls must align with automotive cybersecurity management system |

---

## AI Integration Depth Decision Logic

| Selection | Automated Recommendation |
|-----------|--------------------------|
| **Isolated task** | Standard operational guardrails (Section 11) sufficient |
| **Workflow integrated** | Plugin/tool exchange (TE-01–07) and session isolation (SI-01–07) controls recommended |
| **Autonomous agent** | Memory poisoning (MP-01–07), agent identity (AI-01–07), and Agentic SOAR (MP-05) controls required |
| **Multi-agent system** | All agent controls mandatory plus sub-agent isolation (TE-07), credential chain breaking (AI-04), and multi-agent verification (ST-04) |

---

## Risk Domains and Control Families

The 107 controls are organized into 14 risk domains:

| ID Prefix | Risk Domain | # Controls |
|-----------|-------------|------------|
| PI | Prompt Injection & Jailbreaking | 8 |
| DL | Data Leakage (Code, Secrets, PII) | 10 |
| CE | Unauthorized Code Execution | 8 |
| SC | Supply Chain Risks | 8 |
| HO | Human Oversight & Accountability | 7 |
| GD | GDPR & Data Privacy | 10 |
| AI | Agent Identity & Credential Exposure | 7 |
| SA | Shadow AI & Unsanctioned Data Flows | 7 |
| TE | Tool, Plugin & Agent Data Exchange | 7 |
| MC | Multimodal & Context Window Risks | 7 |
| EA | Endpoint & Browser Overreach | 6 |
| SI | Session Isolation & Inference Attacks | 7 |
| MP | Agent Memory Poisoning & Agentic Defensive Ops | 7 |
| ST | AI-as-Security-Tool Governance | 8 |

---

## Applicability Filter

Not all controls apply to every system. The **Applicability** column indicates:

| Value | Meaning |
|-------|---------|
| **All tiers** | Applies regardless of data classification |
| **Internal+** | Applies to Internal, Confidential, and Restricted data |
| **Confidential+** | Applies only to Confidential and Restricted data |

When a control's applicability does not match your system's data classification, mark it **N/A** in the Control Selection tab. It will be excluded from the effectiveness calculation.

---

## Interpreting Results

### If Residual Risk is CRITICAL (20–25)
- AI implementation **must not proceed**
- Implement all remaining P1, P2, and P3 controls
- Obtain CISO + DPO + CTO written approval
- Complete DPIA regardless of data type
- Quarterly reassessment mandatory

### If Residual Risk is HIGH (12–19)
- Ensure 100% of P1 controls are implemented
- Strongly consider all P2 controls
- Formal risk acceptance by CISO required
- Document accepted residual risk with justification
- Semi-annual reassessment

### If Residual Risk is MEDIUM (6–11)
- Ensure P1 controls are implemented
- Evaluate P2 controls for cost-benefit
- Tech Lead approval sufficient
- Annual reassessment

### If Residual Risk is LOW (1–5)
- Standard operational guardrails in place
- Self-service approval acceptable
- Annual reassessment
- Monitor for changes in scope, data, or exposure

---

## When to Reassess

Trigger a new assessment when:
- Data classification of the system changes
- AI tool access scope is expanded
- New personal data categories are introduced
- System exposure changes (intranet → internet)
- AI integration depth increases (isolated → autonomous)
- Major AI tool version upgrade or provider change
- New regulatory requirements apply (UNECE, EU AI Act)
- Security incident involving the AI tool
- Organizational change affecting business criticality

---

## Framework Alignment

This calculator is aligned to:

| Framework | Coverage |
|-----------|----------|
| Google SAIF | 6 core security elements |
| CSA AI Controls Framework | 10 control families |
| MITRE ATLAS | Adversarial tactics & techniques |
| NIST AI RMF 1.0 | Govern, Map, Measure, Manage |
| ISO/IEC 42001:2023 | Annex A controls |
| OWASP Top 10 for LLM (2025) | 10 prioritized LLM risks |
| OWASP AI Exchange | Comprehensive AI security & privacy |
| OWASP Agentic Security | Autonomous AI agent controls |
| OWASP GenAI Data Security (2026) | 21 data security risks (DSGAI01–21) |
| Anthropic Zero Trust for AI Agents | Agent memory, identity, Agentic SOAR |
| Anthropic LLM Code Security | Scanning agent governance, verification |

---

*AI Risk Assessment Calculator v3.1 — AI Agentic Governance Framework*
