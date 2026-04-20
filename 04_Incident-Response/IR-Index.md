---
title: Incident Response Index
version: "1.0"
status: draft
tags:
  - compliance/nist/respond
  - compliance/nist/recover
  - phase/2-execution
---
## Purpose

This section contains all incident response documentation for the Meridian Financial Services ISMS. The core document is the **Incident Response Plan (IRP)**, which defines the organization's structured approach to handling security incidents. A **Ransomware Playbook** provides scenario-specific procedures.

In NIST CSF 2.0 terms, this section covers:
- **RS (Respond):** How we handle incidents when they occur
- **RC (Recover):** How we restore operations and learn from incidents

---
## Documents

| Document | NIST Mapping | Link |
|----------|-------------|------|
| Incident Response Plan | RS.MA, RS.AN, RS.MI, RC.RP | [[Incident-Response-Plan]] |
| Ransomware Playbook | RS.MI-01, RS.MI-02 | [[Incident-Response-Playbook-Ransomware]] |

---

## How IRP Connects to Other ISMS Components

The IRP does not exist in isolation. It is triggered by detection capabilities (DE) and governed by organizational policies (GV):

- The **AUP** ([[01_Governance/Policies/Acceptable-Use-Policy]]) requires users to report incidents (Section 3.1)
- The **SIEM** (referenced in the DFD) generates alerts that trigger the IRP
- The **RACI Matrix** ([[01_Governance/Roles/RACI-Matrix]]) defines who responds
- **Lessons learned** feed back into the risk assessment and policy review cycle

This feedback loop is the PDCA cycle in action.

---

## Related Notes

- [[01_Governance/Governance-Index]]
- [[02_Framework-Mapping/NIST-CSF-Master-Crosswalk]] - RS and RC sections
- [[Architecture-Index]] - SIEM → IRP trigger flow