---
title: Incident Response Plan
policy_id: MFS-IRP-001
version: "1.0"
status: draft
approved_by: "[CISO Name]"
review_date: 2026-03-07
nist_mapping:
  - RS.MA-01
  - RS.MA-02
  - RS.MA-03
  - RS.AN-03
  - RS.AN-07
  - RS.MI-01
  - RS.MI-02
  - RC.RP-01
  - RC.RP-03
  - RC.CO-03
tags:
  - compliance/nist/respond
  - compliance/nist/recover
  - type/procedure
  - phase/2-execution
  - status/draft
---
# Incident Response Plan

**Wayne Financial Services**
**Policy ID:** WFS-IRP-001
**Effective Date:** [Date]
**Last Reviewed:** [Date]
**Next Review:** Quarterly and after every incident (see [[Policy Review Cadence - 2026]])

---
## 1. Purpose

This plan establishes a structured, repeatable process for responding to cybersecurity incidents at Wayne Financial Services. It ensures that incidents are handled in a way that minimizes damage, reduces recovery time, preserves evidence, and feeds lessons learned back into the ISMS.

This plan follows the six-stage model from **NIST SP 800-61 Rev. 2** (*Computer Security Incident Handling Guide*) and aligns to NIST CSF 2.0 Respond (RS) and Recover (RC) functions.

---
## 2. Scope

This plan covers all cybersecurity incidents affecting Meridian Financial Services' information systems, data, and personnel. An incident is defined as any event that actually or potentially jeopardizes the confidentiality, integrity, or availability of an information system or the information it processes, stores, or transmits.

---
## 3. Severity Classification

| Severity | Label | Definition | Initial Response | Escalation |
|----------|-------|-----------|-----------------|------------|
| **P1** | Critical | Active data breach, ransomware encryption in progress, host compromise with lateral movement | Immediate — all hands | CISO → CEO → Legal → (external: law enforcement, breach counsel) |
| **P2** | High | Confirmed unauthorized access, malware on production system, compromised credentials in use | Within 1 hour | CISO → IT Director → affected business unit |
| **P3** | Medium | Failed attack detected, suspicious but unconfirmed activity, policy violation with security implications | Within 4 hours | Security Team → IT Director |
| **P4** | Informational | Anomalous log entry, minor policy violation, reconnaissance activity (port scan) | Within 24 hours | Security Team (logged, no escalation unless pattern emerges) |

**NIST CSF Alignment:** RS.MA-02 (triage), RS.MA-03 (categorization), RS.MA-04 (escalation)

---

## 4. The Six Stages of Incident Response

### Stage 1: Preparation

> *Before an incident happens — build the capability to respond.*

Preparation is not a response to an incident; it is the ongoing work that makes effective response possible.

**Activities:**
- Maintain this IRP and review quarterly
- Ensure all personnel know how to report incidents (defined in [[Labs/Lab-003-ISMS/01_Governance/Acceptable-use-policy|Acceptable-use-policy]] Section 3.1)
- Maintain SIEM with current detection rules and alert thresholds
- Ensure backups are current and tested monthly (RC.RP-03)
- Maintain a contact list for internal and external stakeholders
- Conduct tabletop exercises at least annually
- Maintain forensic toolkits and evidence collection procedures

**Contacts:**

| Role | Name | Contact | When to Notify |
|------|------|---------|----------------|
| CISO | [Name] | [Phone/Email] | All P1/P2; P3 by judgment |
| IT Director | [Name] | [Phone/Email] | P1/P2/P3 |
| Legal Counsel | [Name/Firm] | [Phone/Email] | P1; any suspected breach |
| HR Director | [Name] | [Phone/Email] | Insider threat; employee involvement |
| CEO | [Name] | [Phone/Email] | P1 only |
| Cyber Insurance | [Carrier] | [Policy #] | P1; any claim-worthy event |

---

### Stage 2: Identification

> *Detect the incident and determine its nature and scope.*

**Trigger Sources:**
- SIEM alert exceeding threshold (DE.AE-08)
- User report (per AUP requirements)
- Third-party notification (vendor, law enforcement, customer)
- Automated tool (EDR, vulnerability scanner, FIM)

**Procedure:**
1. **Receive alert or report.** Log the initial notification: who reported it, when, what was observed.
2. **Validate the event.** Is this a true positive? Check logs, cross-reference with known activity, consult change records.
3. **Classify severity.** Use the matrix in Section 3. If uncertain, classify one level higher than your best estimate.
4. **Assign incident ID.** Format: `INC-YYYY-MM-DD-NNN` (e.g., INC-2026-03-07-001).
5. **Begin incident log.** From this point forward, every action is timestamped and attributed.

**NIST CSF Alignment:** DE.AE-08, RS.MA-02

---

### Stage 3: Containment

> *Stop the damage from spreading. Preserve evidence before acting.*

Containment has two sub-phases:

**Short-term containment** — Immediately limit the blast radius:
- Isolate affected system(s) from the network
- Disable compromised user accounts
- Block malicious IP addresses or domains at the firewall
- Redirect DNS if applicable

**Long-term containment** — Stabilize the environment while investigation continues:
- Apply temporary patches or configuration changes
- Implement enhanced monitoring on adjacent systems
- Create forensic copies of affected systems before any remediation
- Maintain business operations on clean systems

**Critical Rule:** *Take a forensic image or snapshot BEFORE you clean anything.* Evidence preservation is legally and operationally essential. Once you eradicate, the evidence may be gone.

**Evidence Preservation Checklist:**

| Step | Action | Tool/Method |
|------|--------|-------------|
| 1 | Document current system state | Screenshots, notes |
| 2 | Capture volatile data | Memory dump, process list, network connections |
| 3 | Create forensic image | Disk image with hash verification |
| 4 | Export SIEM alerts | JSON/CSV export from SIEM |
| 5 | Hash all evidence | SHA-256; record in chain of custody log |
| 6 | Secure evidence | Store on write-protected media; restrict access |

**Chain of Custody Format:**
```
Evidence ID:      EVD-YYYY-MM-DD-NNN
Incident ID:      INC-YYYY-MM-DD-NNN
Description:      [What was collected]
Source System:    [Hostname / IP / Asset ID]
Collected By:     [Name]
Date/Time (UTC):  [Timestamp]
Hash (SHA-256):   [Hash value]
Storage Location: [Physical or logical location]
Transfer Log:     [Date | From | To | Purpose]
```

**NIST CSF Alignment:** RS.MI-01, RS.AN-07

---

### Stage 4: Eradication

> *Remove the root cause and all artifacts of the incident.*

**Procedure:**
1. Identify the root cause (vulnerability exploited, misconfiguration, social engineering vector)
2. Remove all malicious artifacts: malware, unauthorized accounts, persistence mechanisms, backdoors
3. Patch the vulnerability that was exploited
4. Verify removal by rescanning with appropriate tools (antivirus, FIM, manual review)
5. Update detection rules to catch this specific attack pattern going forward

**Do not skip eradication.** Containment without eradication means the attacker still has a foothold. If you cannot confidently identify and remove the root cause, rebuild the system from a known-good state.

**NIST CSF Alignment:** RS.MI-02

---

### Stage 5: Recovery

> *Restore systems to normal operations and verify they are clean.*

**Procedure:**
1. **Choose restoration method:**
   - *Clean and restore in-place* — if root cause is clear and eradication is verified
   - *Restore from backup* — if system integrity is uncertain (verify backup predates compromise)
   - *Full rebuild* — if compromise is deep or persistent
2. **Restore systems** per the chosen method
3. **Validate functionality** — confirm services are running, data is intact, users can access what they need
4. **Monitor closely** — enhanced monitoring for minimum 48 hours post-recovery to detect recurrence
5. **Declare recovery complete** when no anomalous activity is detected in the monitoring period

**Backup Verification:** Before restoring from backup, confirm:
- Backup was created before the incident began (check incident timeline)
- Backup integrity hash matches the recorded hash
- Backup does not contain the same malicious artifacts

**NIST CSF Alignment:** RC.RP-01, RC.RP-03, RC.RP-05

---

### Stage 6: Lessons Learned

> *The most important stage — and the one most often skipped.*

**Timeline:** Conduct lessons learned review within **5 business days** of incident closure.

**Participants:** All personnel involved in the response (in a real org, this is a meeting; for this project, it is a structured self-review).

**Questions to Answer:**

1. What happened? (Objective timeline, not blame)
2. When did it happen, and when did we detect it? (Calculate MTTD — Mean Time to Detect)
3. What was the root cause?
4. Were the IRP procedures adequate? Did we follow them?
5. What would we do differently?
6. What specific changes will we make? (Assign owners and deadlines)

**Deliverables:**
- Post-incident report (filed in `99_Attachments/`)
- Updated IRP (if process improvements identified)
- Updated detection rules (if detection gaps found)
- Updated risk register (new or modified risk entries)
- Updated crosswalk (evidence links to demonstrate control effectiveness)

**NIST CSF Alignment:** ID.IM-01, ID.IM-02, RC.CO-03

---

## 5. Incident Types

| Type | Description | Typical Severity | Specific Playbook |
|------|-------------|-----------------|-------------------|
| Ransomware | Encryption of systems or data with extortion demand | P1 | [[Incident-Response-Playbook-Ransomware]] |
| Phishing | Fraudulent communication to steal credentials or deliver malware | P2–P3 | Follow general IRP |
| Unauthorized Access | Confirmed access by an unauthorized party | P2 | Follow general IRP |
| Data Breach | Confirmed unauthorized disclosure of sensitive data | P1 | Follow general IRP + legal notification |
| Insider Threat | Malicious or negligent action by an authorized user | P2–P3 | Follow general IRP + HR involvement |
| DDoS | Denial of service attack against company resources | P2–P3 | Follow general IRP + ISP contact |
| Malware | Virus, trojan, worm, or other malicious software detected | P2–P3 | Follow general IRP |

---

## 6. Compliance Cross-Reference

This IRP satisfies requirements under:

| Standard | Requirement | How This IRP Addresses It |
|----------|------------|--------------------------|
| NIST CSF 2.0 | RS.MA, RS.AN, RS.MI, RC.RP, RC.CO | Six-stage plan maps directly to RS and RC subcategories |
| NIST SP 800-61 Rev. 2 | Incident handling lifecycle | Six-stage model follows SP 800-61 structure |
| SOC 2 (CC7.3, CC7.4) | Incident identification and response | Sections 3–4 cover identification through recovery |
| ISO 27001 (A.16) | Information security incident management | Full incident management lifecycle documented |
| GLBA (Safeguards Rule) | Response program for security events | Plan covers detection, containment, and notification |

> *This cross-reference demonstrates a key ISMS principle: one well-built control can satisfy multiple compliance requirements simultaneously.*

---

## 7. Review and Maintenance

This plan is reviewed:
- **Quarterly** as part of the standard policy review cycle
- **After every incident** (lessons learned drive updates)
- **After significant changes** to the IT environment
- **After tabletop exercises** (findings drive updates)

---

## Document History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | [Date] | [Your Name] | Initial draft |

---

## Related Notes

- [[01_Governance/Policies/Acceptable-Use-Policy]] — User reporting obligations
- [[01_Governance/Roles/RACI-Matrix]] — Response role assignments
- [[Incident-Response-Playbook-Ransomware]] — Scenario-specific playbook
- [[02_Framework-Mapping/NIST-CSF-Master-Crosswalk]] — RS and RC control mapping
- [[Architecture-Index]] — SIEM trigger flow
- [[Policy Review Cadence - 2026]] — Review schedule