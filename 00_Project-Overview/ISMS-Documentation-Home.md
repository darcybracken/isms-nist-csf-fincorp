# ISMS Documentation - Home

  A student-built Information Security Management System aligned to NIST CSF 2.0, designed to demonstrate GRC competency from framework selection through audit-ready documentation.

---
## What This Is

This was put together in an Obsidian vault, a **centralized knowledge base** that contains all the artifacts needed to design, document, and demonstrate an Information Security Management System (ISMS) for a mock organization. It was built from scratch to answer one question: *What does it actually take to protect organizational data in a structured, auditable way?*

The regulatory framework used is **NIST Cybersecurity Framework 2.0** (February 2024).

---
## Vault Navigation

| Section                     | Purpose                                      | Entry Point                                        |
| --------------------------- | -------------------------------------------- | -------------------------------------------------- |
| 00 - Project Overview       | Objective, scope, phases, methodology        | *you are here*                                     |
| 01 - Governance             | Policies, roles, risk appetite               | 01_Governance/Governance-Index                 |
| 02 - Framework Mapping      | NIST CSF 2.0 crosswalk and control table     | 02_Framework-Mapping/NIST-CSF-Master-Crosswalk |
| 03 - Architecture           | Data flow diagrams, control overlay          | Architecture-Index                             |
| 04 - Incident Response      | IRP, ransomware playbook, response stages    | 04_Incident-Response/IR-Index                  |
| 05 - Remediation & Findings | Gap analysis, outcome summary                | Findings-Summary                               |
| 06 - Templates              | Reusable templates for policies and tracking | Template-Index                                 |

---
## Tagging System

This vault uses a consistent tagging taxonomy so any artifact can be retrieved instantly during an audit or review.

**By compliance framework:**
`#compliance/nist` · `#compliance/nist/govern` · `#compliance/nist/identify` · `#compliance/nist/protect` · `#compliance/nist/detect` · `#compliance/nist/respond` · `#compliance/nist/recover`

**By document type:**
`#type/policy` · `#type/procedure` · `#type/diagram` · `#type/evidence` · `#type/template` · `#type/crosswalk`

**By status:**
`#status/draft` · `#status/review` · `#status/approved` · `#status/archived`

**By phase:**
`#phase/1-setup` · `#phase/2-execution` · `#phase/3-mapping` · `#phase/4-remediation`

---
## Project Metadata

| **Field**            | **Value**                                                |
| -------------------- | -------------------------------------------------------- |
| **Author**           | Darcy                                                   |
| **Date Started**     | 2026-03-07                                               |
| **Framework**        | NIST Cybersecurity Framework (CSF) 2.0                   |
| **Tools**            | Obsidian MD, Lucidchart, Python (for automation scripts) |
| **Host Machine**     | MacBook Air M4                                           |
| **Classification**   | Student Project - GRC Portfolio                          |

---
## How to Use This Vault

**Phase 1 (Setup):** Start in `00_Project-Overview` to understand the scope. Ensure your **YAML frontmatter** is filled out in every file to power the tracking tags.

**Phase 2 (Execution):** Navigate through `01_Governance` to see the **Acceptable Use Policy** and `04_Incident-Response` for the **IRP**. These are the "living" documents that define your security posture.

**Phase 3 (Mapping):** View the `02_Framework-Mapping` folder. This contains the **Master Crosswalk**, which maps your internal policies to **NIST CSF 2.0, SOC 2, and ISO 27001**.

**Phase 4 (Remediation):** Check `05_Remediation-Findings` for the gap analysis. This is where you document what you've built and what still needs work.
