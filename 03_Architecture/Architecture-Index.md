---
title: Architecture Index
version: "1.0"
status: draft
tags:
  - compliance/nist/identify
  - compliance/nist/protect
  - type/diagram
  - phase/2-execution
---
## Purpose

This section contains the architectural documentation for FinCorp's IT environment. The primary artifact is a **Data Flow Diagram (DFD)** that visualizes the "data journey" - how data moves from user endpoints through internal systems to cloud storage - and overlays NIST CSF controls at each point where security must be enforced.

This is what "Security by Design" looks like in practice: you don't add controls after the architecture exists. You design the architecture with controls built in.

---

## Data Flow Diagram

> Diagram complete. <img width="100%" alt="FinCorp Data Flow Architecture — NIST CSF 2.0 Control Overlay" src="https://github.com/user-attachments/assets/cac9bf3e-79b3-4d95-98bc-791d027e6fff" />

### What the DFD Should Show

The diagram illustrates data moving through four zones, with NIST controls overlaid at each boundary and processing point.

---

## Lucidchart 

When building the formal diagram, use these specifications:
### Color Coding

| Zone                   | Color        |
| ---------------------- | ------------ |
| User Endpoints         | Light Blue   |
| Internal Network       | Light Green  |
| Cloud Environment      | Light Orange |
| Security Operations    | Light Purple |
| Firewalls / Boundaries | Red border   |
### Elements to Include

- [x] Four zones with distinct color backgrounds
- [x] Directional arrows showing data flow (labeled with data type: "PII", "Logs", "Backups")
- [x] Firewall/boundary icons between zones
- [x] NIST control labels in call-out boxes at each enforcement point
- [x] Legend explaining colors, icons, and NIST reference format
- [x] Title block: FinCorp - Data Flow Architecture with NIST CSF Control Overlay
- [x] Version number and date

### Data Flow Labels

| Flow | Source → Destination | Data Type | Key Control |
|------|---------------------|-----------|-------------|
| 1 | Endpoint → Internal (via VPN) | User data, documents | PR.DS-02 (TLS), PR.AA-01 (MFA) |
| 2 | Internal → Cloud (S3/RDS) | Financial records, PII | PR.DS-01 (AES-256), PR.DS-02 (TLS) |
| 3 | All Zones → SIEM | Log data | PR.PS-04, DE.CM-01 |
| 4 | Cloud → Backup | Encrypted backups | RC.RP-03, PR.DS-01 |
| 5 | SIEM → IRP trigger | Alert data | RS.MA-01, DE.AE-08 |

---

## Why a DFD Matters for an ISMS

A Data Flow Diagram is not just a pretty picture. It answers critical audit questions:

1. **Where does sensitive data live?** → Drives PR.DS-01 (encryption at rest)
2. **How does data move between systems?** → Drives PR.DS-02 (encryption in transit)
3. **Where are the trust boundaries?** → Drives PR.IR-01 (network segmentation)
4. **Where should we monitor?** → Drives DE.CM-01 (continuous monitoring)
5. **What needs to be backed up?** → Drives RC.RP-03 (backup verification)

Without a DFD, an auditor cannot verify that controls are placed where they are needed. The DFD is the bridge between policy (what you say you do) and architecture (where you actually do it).

---
