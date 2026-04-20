---
title: Governance Index
author: Darcy
Start_Date: 2026-03-07
version: "1.0"
status: draft
tags:
  - compliance/nist/govern
  - type/procedure
  - phase/2-execution
---
# Governance Index
## Purpose

This section contains the governance foundation of the ISMS - the policies, roles, and risk appetite statements that define *how* Meridian Financial Services manages information security. In NIST CSF 2.0 terms, this maps primarily to the **Govern (GV)** function.

#### Governance answers three questions:

1. **Who is accountable?** → Labs/Lab-003-ISMS/01_Governance/Roles/RACI-Matrix

2. **What are the rules?** → Acceptable-Use-Policy

3. **How much risk is acceptable?** → Risk appetite statement (below)
---
## Risk Appetite Statement

Meridian Financial Services adopts a **low risk appetite** for information security, consistent with its obligations under SOC 2 and GLBA:

**Data confidentiality** is the highest priority. Unauthorized disclosure of PII or financial records is unacceptable under any circumstance.

**System availability** must meet a 99.5% uptime target for customer-facing services.

**Compliance gaps** must be remediated within 30 days of identification (90 days for low-priority findings).

**Residual risk** is accepted only when formally documented, approved by the CISO, and reviewed quarterly.

*This statement drives every control decision in the ISMS. A startup with a high risk appetite would accept more residual risk and invest less in preventive controls. The risk appetite must match the organization's context - this is what NIST CSF 2.0's GV.OC (Organizational Context) category is about.*

---
## Governance Documents
| Document                     | NIST Category                    | Status        | Link                                            |
| ---------------------------- | -------------------------------- | ------------- | ----------------------------------------------- |
| Acceptable Use Policy (AUP)  | GV.PO (Policy)                   | #status/draft |   Policies/Acceptable-Use-Policy                |
| Incident Response Plan (IRP) | RS.RP (Response Planning)        | #status/draft |   04_Incident-Response/Incident-Response-Plan   |
| RACI Matrix                  | GV.RR (Roles & Responsibilities) | #status/draft |   01_Governance/Roles/RACI-Matrix               | 
| Policy Review Cadence        | GV.PO-02                         | #status/draft |   Policy Review Cadence - 2026                  |

---
## How Governance Connects to the Rest of the ISMS

```

                         ┌──────────────────┐
                         │     GOVERN       │
                         │ Policies, Roles  │
                         │ Risk Appetite    │
                         └────────┬─────────┘
                                  │
                    ┼─────────────┼─────────────┼
                    │             │             │
            ┌─────▼──────┐ ┌──────▼─────┐ ┌──────▼─────────┐
            │ IDENTIFY   │ │ PROTECT    │ │ DETECT/RESPOND.│
            │ Assets,    │ │ Controls,  │ │ Monitoring,    │
            │ Risks      │ │ Encryption │ │ IR Playbooks   │  
            └────────────┘ └────────────┘ └────────────────┘

```

  The Govern function sits above and informs every other function. Without governance, controls exist in isolation - there is no authority to enforce them, no risk context to prioritize them, and no accountability when they fail.

---
## NIST CSF 2.0 - Govern Function Subcategories

|Category|What It Covers|Where It Appears in This Vault|
|---|---|---|
|GV.OC - Organizational Context|Mission, stakeholders, legal requirements|Project-Overview (mock org profile)|
|GV.RM - Risk Management Strategy|Risk appetite, tolerance, methodology|This document (risk appetite statement)|
|GV.RR - Roles, Responsibilities, Authorities|Who does what| 01_Governance/Roles/RACI-Matrix|
|GV.PO - Policy|Cybersecurity policies exist and are maintained|Policies/Acceptable-Use-Policy|
|GV.SC - Supply Chain Risk Management|Third-party risk|Noted in crosswalk; simplified for this project|

---
