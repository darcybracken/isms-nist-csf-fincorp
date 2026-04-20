---
title: Incident Response Playbook - Ransomware
policy_id: FC-IRP-PB-001
author: "D'Arcy Bracken"
date: 2026-03-07
version: "1.0"
status: approved
nist_mapping:
  - RS.MI-01
  - RS.MI-02
  - RC.RP-01
  - RC.RP-03
tags:
  - compliance/nist/respond
  - compliance/nist/recover
  - type/procedure
  - phase/2-execution
  - status/approved
---
This playbook supplements the [[Incident-Response-Plan]]. It provides scenario-specific procedures for ransomware incidents. The general IRP stages still apply - this document provides the *what to do specifically* at each stage.

---
## Automatic Classification: P1 - Critical
All confirmed ransomware incidents are automatically classified as **P1 (Critical)** because:

- Encryption is often fast and can spread laterally within minutes
- Business operations are immediately disrupted
- Data integrity and availability are directly compromised
- Regulatory notification obligations may be triggered
---
## Stage-by-Stage Response
### Stage 2: Identification (Ransomware-Specific)
**Indicators of ransomware:**

- Ransom note file appearing on desktops or file shares (e.g., `README_RESTORE.txt`)
- Files renamed with unfamiliar extensions (e.g., `.locked`, `.encrypted`, `.ryuk`)
- Sudden inability to open files across multiple users
- SIEM alerts for mass file renaming or high-volume file system activity
- EDR alert for known ransomware signatures or behaviors

**Immediate actions upon identification:**

1. Do **NOT** shut down affected systems (volatile memory may contain decryption keys or IOCs)
2. Do **NOT** attempt to decrypt or run any tools from the ransom note
3. Document exactly what you see: ransom note text, file extensions, affected systems
4. Assign INC ID and escalate immediately per P1 escalation path

---
### Stage 3: Containment (Ransomware-Specific)
**Time is critical.** Ransomware spreads through network shares, lateral movement, and automated propagation. Every minute of delay increases the blast radius.

**Immediate containment actions (first 15 minutes):**

| Priority | Action | Rationale |
|----------|--------|-----------|
| 1 | Disconnect affected systems from the network (pull cable or disable adapter - do NOT power off) | Stop lateral spread while preserving memory |
| 2 | Disable network shares and mapped drives org-wide | Prevent encryption of shared file systems |
| 3 | Block known ransomware C2 domains/IPs at the firewall | Sever attacker communication |
| 4 | Disable compromised accounts | If initial access was via stolen credentials |
| 5 | Isolate the affected network segment | If segmentation is available (PR.IR-01) |
**Next 1–4 hours:**

- Determine the ransomware variant (check ransom note against known samples on ID Ransomware or similar)
- Assess scope: how many systems are affected? Is encryption still in progress?
- Check if a public decryptor exists (No More Ransom Project)
- Preserve forensic evidence per chain of custody procedures in the IRP

---
### Stage 4: Eradication (Ransomware-Specific)

**Do not attempt to eradicate on encrypted systems.** If a system has been encrypted, it is compromised beyond cleaning. The eradication strategy is:

1. **Identify the initial access vector:** How did the ransomware get in? (Phishing email, RDP brute force, vulnerable public service, supply chain)

2. **Close the entry point:** Patch the vulnerability, disable the exposed service, reset compromised credentials

3. **Scan all systems that were NOT encrypted:** Ensure no dormant malware or persistence mechanisms remain

4. **Verify Active Directory integrity:** Ransomware operators often compromise AD before deploying encryption
---
### Stage 5: Recovery (Ransomware-Specific)

**The ransom decision:**

| Option | Considerations |
|--------|---------------|
| **Do NOT pay** (recommended) | No guarantee of decryption. Funds criminal enterprise. May violate OFAC sanctions. Insurance may not cover. Paying signals willingness to pay again. |
| **Pay** (last resort) | Only if: no backups exist, data is business-critical with no alternative, legal counsel approves, law enforcement is consulted, and payment does not violate sanctions |  
*FinCorp's position: The default decision is to NOT pay. This decision is pre-approved by the CISO and CEO. Deviation requires legal review.*

**Recovery from backups:**

1. Verify backup integrity (hash check, test restore on isolated system)

2. Confirm backup predates the initial compromise (not just the encryption event - attackers often dwell for days/weeks before deploying ransomware)

3. Rebuild affected systems from clean images

4. Restore data from verified backups

5. Redeploy security agents (EDR, SIEM agent)

6. Do NOT reconnect to the production network until scan is clean

  

**Post-recovery validation:**

- Run full antivirus/EDR scan on all restored systems
- Verify file integrity against known-good baselines
- Monitor for 72 hours (extended from standard 48 hours for ransomware)
- Confirm no anomalous network traffic (C2 callbacks, lateral movement)
---
### Stage 6: Lessons Learned (Ransomware-Specific)
In addition to the standard lessons learned questions from the IRP, ransomware incidents require:

- **Initial access timeline:** When did the attacker first get in versus when did they deploy ransomware? (Dwell time matters - long dwell time means detection failed earlier)
- **Backup effectiveness:** Were backups available, intact, and usable? How long did restoration take?
- **Segmentation effectiveness:** Did network segmentation limit the blast radius?
- **Detection gap:** What should have caught this earlier? What SIEM rule or EDR policy needs to be added?
---
## Quick Reference: Do's and Don'ts

| DO | DON'T |
|----|-------|
| Disconnect from network immediately | Power off affected systems |
| Preserve evidence before cleaning | Run any tools from the ransom note |
| Check for public decryptors | Pay the ransom without legal counsel |
| Verify backup integrity before restoring | Assume backups are clean - verify dates |
| Report to law enforcement (FBI IC3) | Negotiate directly with attackers |
| Document every action with timestamps | Delete ransom notes or malware samples |

---
## Related Notes

- [[Incident-Response-Plan]] - General IRP (this playbook supplements it)

- [[02_Framework-Mapping/NIST-CSF-Master-Crosswalk]] - RS.MI, RC.RP controls

- [[01_Governance/Policies/Acceptable-Use-Policy]] - User reporting obligations

- [[Architecture-Index]] - Network segmentation reference