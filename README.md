# ISMS Portfolio Project: NIST CSF 2.0
### Built by D'Arcy Bracken | Cybersecurity & Information Assurance, WGU

---

## What This Is

A student-built **Information Security Management System (ISMS)** designed from scratch for a mock financial services organization (FinCorp) aligned to **NIST Cybersecurity Framework 2.0** (February 2024).

This project answers one practical question: *What does it actually take to protect organizational data in a structured, auditable way?*

The result is a complete documentation package, including governance policies, control mappings, architecture diagrams, and incident response procedures, structured the way a GRC analyst would build it in a real organization.

---

## Mock Organization

| Field | Value |
|-------|-------|
| **Organization** | FinCorp (mock) |
| **Industry** | Financial Services |
| **Size** | 200 employees |
| **Regulatory Environment** | SOC 2, GLBA Safeguards Rule |
| **Data Sensitivity** | PII, financial records, internal communications |
| **IT Environment** | Hybrid on-premises + AWS, Microsoft 365 |
| **Risk Appetite** | Low / conservative |

---

## Architecture Overview

The diagram below shows how data flows through FinCorp's four security zones, with NIST CSF 2.0 controls overlaid at every enforcement point.

![FinCorp Data Flow Architecture — NIST CSF 2.0 Control Overlay](99_Attachments/ISMS_Architecture.png)

---

## What Was Built

| Artifact | Purpose | NIST Function |
|----------|---------|---------------|
| [Acceptable Use Policy](01_Governance/Acceptable-use-policy.md) | Defines acceptable behavior, data handling, and prohibited activities | Govern (GV) |
| [RACI Matrix](01_Governance/Roles/RACI-Matrix.md) | Assigns accountability across 14 security activities and 6 roles | Govern (GV) |
| [NIST CSF Master Crosswalk](02_Framework-Mapping/NIST-CSF-Master-Crosswalk.md) | Maps every control to NIST subcategories with SOC 2, ISO 27001, and GLBA cross-references | All 6 functions |
| [Data Flow Architecture](03_Architecture/Architecture-Index.md) | Four-zone DFD with NIST control overlay at every boundary and enforcement point | Identify, Protect |
| [Incident Response Plan](04_Incident-Response/Incident-Response-Plan.md) | Six-stage response lifecycle (NIST SP 800-61), severity matrix, evidence chain of custody | Respond, Recover |
| [Ransomware Playbook](04_Incident-Response/Incident-Response-Playbook-Ransomware.md) | Scenario-specific procedures: containment, eradication, recovery, ransom decision framework | Respond, Recover |
| [Gap Analysis & Findings](05_Remediation-Findings/Findings-Summary.md) | POA&M style gap tracking across all six NIST functions | All 6 functions |
| [Policy Review Cadence](06_Templates/Policy-Review-Cadence-2026.md) | Quarterly review schedule with PDCA improvement cycle | Govern (GV) |

---

## Frameworks Covered

| Framework | How It's Applied |
|-----------|-----------------|
| **NIST CSF 2.0** | Primary framework for all six functions (Govern, Identify, Protect, Detect, Respond, Recover) |
| **NIST SP 800-61 Rev. 2** | Incident response lifecycle structure |
| **SOC 2 (AICPA TSC 2017)** | Cross-referenced in the Master Crosswalk |
| **ISO 27001** | Cross-referenced in the Master Crosswalk |
| **GLBA Safeguards Rule** | Regulatory driver for the mock org's ISMS requirement |

---

## Repository Structure

```
├── 00_Project-Overview/       # Scope, methodology, mock org context
├── 01_Governance/             # AUP, RACI Matrix, risk appetite
├── 02_Framework-Mapping/      # NIST CSF Master Crosswalk (all 6 functions)
├── 03_Architecture/           # Data Flow Diagram with control overlay
├── 04_Incident-Response/      # IRP + Ransomware Playbook
├── 05_Remediation-Findings/   # Gap analysis, POA&M, lessons learned
├── 06_Templates/              # Policy review cadence, reusable templates
└── 99_Attachments/            # Exported diagrams and evidence
```

---

## Key Design Decisions

**Governance before controls.** Every document in this project traces back to a risk appetite statement and an organizational context. Controls exist to serve governance not the other way around.

**One ISMS, multiple frameworks.** The Master Crosswalk demonstrates that a single well-built control program can simultaneously satisfy NIST CSF, SOC 2, ISO 27001, and GLBA compliance, which is about mapping, not rebuilding.

**Audit-ready documentation.** Every policy includes YAML frontmatter with version, author, NIST mapping, and status. Every control in the crosswalk links to evidence. An auditor can follow the chain from risk appetite → policy → control → evidence without leaving the repository.

---

## About

**D'Arcy Bracken**
B.S. Cybersecurity and Information Assurance, Western Governors University (In Progress)
CompTIA A+ Certified | Pursuing Security+

[LinkedIn](https://linkedin.com/in/darcyvbracken)
