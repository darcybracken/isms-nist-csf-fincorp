---
title: ISMS Project Overview
author: Darcy
date: 2026-03-07
version: "1.0"
status: draft
tags:
  - phase/1-setup
  - type/procedure
---
# ISMS Project Overview
## Objective

To design a framework for protecting organizational data based on industry-standard compliance requirements (NIST CSF) and create a searchable, audit-ready documentation package within a centralized knowledge base.

---
## What Is an ISMS?

An **Information Security Management System** is a structured set of policies, processes, and controls that an organization uses to manage information security risks. It is not a piece of software or a single document, it is a *system of management* that ties together:

**Governance:** Who is responsible, what are the rules, and how are decisions made?

**Risk Management:** What could go wrong, how bad would it be, and what are we doing about it?

**Controls:** What specific safeguards are in place, and do they actually work?

**Continuous Improvement:** How do we know the system is working, and how do we make it better?

The most well-known ISMS standard is ISO/IEC 27001. This project uses **NIST CSF 2.0** as the control framework because it is freely available, widely adopted, and organizes security into six intuitive functions that map well to how organizations actually operate.

---
## Why NIST CSF 2.0?

NIST CSF 2.0 was chosen because:

1. **It is function-oriented.** The six functions (Govern, Identify, Protect, Detect, Respond, Recover) tell a story - from establishing leadership accountability through recovering from incidents.

2. **It added Govern in version 2.0.** The original CSF (1.1) had five functions. Version 2.0 elevated governance to a standalone function, recognizing that policy and leadership are foundational, not optional.

3. **It is framework-agnostic.** NIST CSF is designed to be used *alongside* other standards (ISO 27001, SOC 2, GDPR). The crosswalk table in this project demonstrates that interoperability.

4. **It is free.** No licensing cost, publicly documented, with extensive implementation guidance from NIST.
---
## Mock Organization Profile
To make this project realistic, all policies and controls are written for a fictional organization:

| **Field**              | **Value**                                                |
| ---------------------- | -------------------------------------------------------- |
| Organization Name      | Wayne Financial Services (mock)                          |
| Industry               | Financial Services                                       |
| Size                   | 200 employees                                            |
| Regulatory Environment | Subject to SOC 2, GLBA, and internal audit               |
| Data Sensitivity       | PII, financial records, internal communications          |
| IT Environment         | Hybrid (on-premises + cloud), Microsoft 365, AWS         |
| Risk Appetite          | Low - conservative posture due to regulatory obligations |
*This profile drives every policy decision in the vault. A healthcare company or a startup would make different choices even using the same NIST CSF framework. The mock org exists to demonstrate that controls must be tailored to context.*

---
## Project Phases
### Phase 1: Lab Environment Setup
Establish the documentation infrastructure. Obsidian vault created, folder structure defined, tagging taxonomy implemented. All work is performed on an encrypted volume.

**Deliverables:** Vault structure, tagging system, project overview (this document)
### Phase 2: Execution Steps

Build the three core artifacts of the ISMS:

1. **Framework Mapping** - Map mock organizational needs to NIST CSF 2.0 core functions and subcategories. Produce a master crosswalk table.

2. **Policy Development** - Draft an Acceptable Use Policy (AUP) and Incident Response Plan (IRP) as the "single source of truth" for governance. Link them using Obsidian's features.

3. **Architectural Visualization** - Design a Data Flow Diagram (DFD) in Lucidchart/Visio showing data moving from endpoints to cloud storage, overlaid with NIST controls.

**Deliverables:** NIST crosswalk, AUP, IRP, DFD with control overlay

### Phase 3: ISMS Control Table

Produce the formal mapping table that connects each policy/control to its NIST category, priority, compliance target, and implementation detail. This is the artifact an auditor would review.

**Deliverables:** Control table (see 02_Framework-Mapping/NIST-CSF-Master-Crosswalk)

### Phase 4: Remediation & Findings

Summarize outcomes: what was built, what gaps were found, what was improved. Demonstrate that the ISMS is not just a set of documents but a cycle of assessment and improvement.

**Deliverables:** Findings summary, evidence attachments, lessons learned

---
## Methodology
This project follows a **Plan-Do-Check-Act (PDCA)** cycle, which is the standard continuous improvement model used in ISO 27001 and applicable to any ISMS:

```

┌──────────┐
│   PLAN   │ ← Define scope, select framework, identify risks
└────┬─────┘
     │
┌────▼─────┐
│    DO    │ ← Write policies, map controls, build documentation
└────┬─────┘
     │
┌────▼─────┐
│  CHECK   │ ← Review for gaps, validate crosswalk, test IRP
└────┬─────┘
     │ 
┌────▼─────┐
│   ACT    │ ← Remediate gaps, update policies, document findings
└──────────┘

```

This vault represents one full pass through the PDCA cycle.
