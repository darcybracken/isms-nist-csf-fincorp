---
title: NIST CSF 2.0 Reference
author: Darcy
date: 2026-03-07
version: "1.0"
tags:
  - compliance/nist
  - type/procedure
---
## Overview

The NIST Cybersecurity Framework (CSF) 2.0 was published in **February 2024** by the National Institute of Standards and Technology. It is a voluntary framework that provides organizations with a structured approach to managing cybersecurity risk.

**Key change from CSF 1.1 to 2.0:** The addition of **Govern** as a sixth core function, elevating governance from a background concern to an explicit, foundational requirement.

---

## The Six Core Functions

| Function | Code | Purpose | Question It Answers |
|----------|------|---------|---------------------|
| **Govern** | GV | Establish and monitor risk management strategy, policy, and roles | "Who is in charge, and what are the rules?" |
| **Identify** | ID | Understand assets, risks, and the environment | "What do we have, and what could go wrong?" |
| **Protect** | PR | Implement safeguards for critical services | "How do we prevent bad things from happening?" |
| **Detect** | DE | Discover cybersecurity events and anomalies | "How do we know when something bad is happening?" |
| **Respond** | RS | Take action regarding detected incidents | "What do we do when something bad happens?" |
| **Recover** | RC | Restore capabilities and services | "How do we get back to normal?" |

---
## How the Functions Relate

```
        ┌──────────────────────────────┐
        │          GOVERN (GV)          │
        │   Strategy, Policy, Roles     │
        │   Oversees all functions      │
        └──────────────┬───────────────┘
                       │
     ┌─────────────────┼─────────────────┐
     │                 │                 │
┌────▼────┐      ┌─────▼─────┐     ┌─────▼─────┐
│IDENTIFY │      │ PROTECT   │     │  DETECT   │
│(ID)     │      │ (PR)      │     │  (DE)     │
│Know your│──────│Safeguard  │─────│Find       │
│assets & │      │assets     │     │problems   │
│risks    │      │           │     │           │
└─────────┘      └───────────┘     └─────┬─────┘
                                         │
                                   ┌─────▼─────┐
                                   │ RESPOND   │
                                   │ (RS)      │
                                   │Handle     │
                                   │incidents  │
                                   └─────┬─────┘
                                         │
                                   ┌─────▼─────┐
                                   │ RECOVER   │
                                   │ (RC)      │
                                   │Restore    │
                                   │operations │
                                   └───────────┘
```

Govern surrounds and informs all other functions. Identify → Protect is proactive. Detect → Respond → Recover is reactive. A mature ISMS addresses both sides.

---
## Official Resources

- **NIST CSF 2.0 Full Document:** https://csf.tools/ (interactive browser) or https://www.nist.gov/cyberframework
- **NIST SP 800-61 Rev. 2:** Computer Security Incident Handling Guide (referenced by the IRP)
- **NIST CSF 2.0 Quick Start Guides:** Available on the NIST website for small businesses, enterprises, and specific sectors

---
## How This Vault Uses CSF 2.0

Every document in this vault maps to one or more CSF subcategories via:
1. **YAML frontmatter** - each document lists its `nist_mapping` field
2. **Tags** - `#compliance/nist/govern`, `#compliance/nist/protect`, etc.
3. **Master Crosswalk** - 02_Framework-Mapping/NIST-CSF-Master-Crosswalk ties everything together
