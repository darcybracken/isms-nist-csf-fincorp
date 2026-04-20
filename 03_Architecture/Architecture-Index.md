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

> Diagram complete. Exported PNG saved to: `99_Attachments/ISMS_Architecture.png`

### What the DFD Should Show

The diagram illustrates data moving through four zones, with NIST controls overlaid at each boundary and processing point.

### DFD Zones and Data Flow

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│   ZONE 1: User Endpoints                                        │
│   ┌──────────┐  ┌──────────┐  ┌──────────┐                      │
│   │ Laptop   │  │ Mobile   │  │ Remote   │                      │
│   │ (Corp)   │  │ (BYOD)   │  │ (VPN)    │                      │
│   └────┬─────┘  └────┬─────┘  └────┬─────┘                      │
│        │             │             │                            │
│   Controls:  PR.AA-01   (MFA)                                   │
│              PR.DS-01   (Full Disk Encryption)                  │
│              PR.AA-05   (Least Privilege / RBAC)                │
│                                                                 │
└────────────────────────┬────────────────────────────────────────┘
                         │
                    ┌────▼────┐
                    │Firewall │  ← PR.IR-01 (Network Segmentation)
                    │  / WAF  │    DE.CM-01 (Network Monitoring)
                    └────┬────┘
                         │
┌────────────────────────▼───────────────────────────────────────┐
│                                                                │
│   ZONE 2: Internal Network (Corporate LAN)                     │
│   ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │
│   │ App Server   │  │ File Server  │  │ Email Server │         │
│   │ (M365)       │  │ (On-Prem)    │  │ (Exchange)   │         │
│   └──────┬───────┘  └──────┬───────┘  └──────┬───────┘         │
│          │                 │                 │                 │
│   Controls:  PR.DS-02 (TLS 1.2+ in transit)                    │
│              PR.PS-04 (Audit Logging → SIEM)                   │
│              DE.CM-09 (Endpoint Monitoring / EDR)              │
│              PR.PS-01 (CIS Baselines)                          │
│                                                                │
└────────────────────────┬───────────────────────────────────────┘
                         │
                    ┌────▼────┐
                    │Firewall │  ← PR.IR-01 (Zone Boundary)
                    │  Rules  │    PR.DS-02 (Encrypted Transit)
                    └────┬────┘
                         │
┌────────────────────────▼───────────────────────────────────────┐
│                                                                │
│   ZONE 3: Cloud Environment (AWS)                              │
│   ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │
│   │ S3 Storage   │  │ RDS Database │  │ CloudWatch   │         │
│   │              │  │              │  │ (Logging)    │         │
│   └──────────────┘  └──────────────┘  └──────────────┘         │
│                                                                │
│   Controls:  PR.DS-01 (AES-256 at rest / SSE-S3)               │
│              PR.AA-01 (IAM policies / least privilege)         │
│              DE.AE-02 (CloudTrail → SIEM correlation)          │
│              RC.RP-03 (Backup integrity / S3 versioning)       │
│                                                                │
└────────────────────────┬───────────────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────────────────┐
│                                                                 │
│   ZONE 4: Security Operations (Management)                      │
│   ┌──────────────┐  ┌──────────────┐                            │
│   │ SIEM         │  │ Backup       │                            │
│   │ (Centralized │  │ (Offsite /   │                            │
│   │  Logging)    │  │  Immutable)  │                            │
│   └──────────────┘  └──────────────┘                            │
│                                                                 │
│   Controls:  DE.AE-03 (Multi-source correlation)                │
│              DE.CM-01 (Continuous monitoring)                   │
│              RS.MA-01 (IRP triggers from SIEM alerts)           │
│              RC.RP-01 (Recovery from verified backups)          │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

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
