---
title: NIST CSF 2.0 Master Crosswalk
version: "1.0"
status: draft
tags:
  - compliance/nist
  - type/crosswalk
  - phase/2-execution
  - phase/3-mapping
---
## Purpose

This crosswalk maps FinCorp internal policies and controls to specific NIST CSF 2.0 categories and subcategories. It serves as the single reference an auditor would use to verify that the organization's security posture has no gaps against the framework.

The crosswalk also demonstrates how NIST CSF maps to other compliance targets (SOC 2, ISO 27001, GLBA) - showing that a well-built ISMS can satisfy multiple regulatory requirements simultaneously.

---
## How to Read This Table

- **Policy/Control:** The internal document or safeguard being mapped

- **NIST Function:** One of the six CSF 2.0 core functions

- **NIST Category/Subcategory:** The specific CSF area being addressed

- **Priority:** Critical / High / Medium / Low - based on the mock org's risk appetite

- **Compliance Target:** Which external standard or regulation this also satisfies

- **Implementation Detail:** What specifically is being done

- **Evidence:** Where the supporting documentation lives in this vault

---
## GOVERN (GV)
*The Govern function establishes and monitors the organization's cybersecurity risk management strategy, expectations, and policy. It is the foundation - without governance, the other five functions lack authority and accountability.*

| Policy/Control            | NIST Subcategory                   | Priority | Compliance Target | Implementation Detail                                                                                                  | Evidence                                         |
| :------------------------ | :--------------------------------- | :------- | :---------------- | :--------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------ |
| Mock Organization Profile | GV.OC-01 (Mission understood)      | High     | Internal Audit    | Organizational mission, risk context, and stakeholder expectations documented. Drives all subsequent policy decisions. | Project-Overview.        |
| Risk Appetite Statement   | GV.RM-01 (Objectives established)  | Critical | SOC 2 / GLBA      | Low risk appetite defined. Residual risk requires CISO approval and quarterly review.                                  | 01_Governance/Governance-Index               |
| Risk Appetite Statement   | GV.RM-02 (Tolerance established)   | Critical | SOC 2 / GLBA      | Specific tolerance thresholds: 30-day remediation for high findings, 90 days for low. 99.5% uptime target.             | 01_Governance/Governance-Index               |
| RACI Matrix               | GV.RR-01 (Leadership accountable)  | High     | ISO 27001 A.5     | CISO accountable for all security activities. CEO accountable for risk appetite.                                       | 01_Governance/Roles/RACI-Matrix              |
| RACI Matrix               | GV.RR-02 (Roles established)       | High     | ISO 27001 A.5     | Full RACI for 14 security activities across 6 organizational roles.                                                    | 01_Governance/Roles/RACI-Matrix              |
| Acceptable Use Policy     | GV.PO-01 (Policy established)      | High     | Internal Audit    | AUP defines acceptable behavior, data handling, prohibited activities. Approved by CISO.                               | 01_Governance/Policies/Acceptable-Use-Policy |
| Policy Review Cadence     | GV.PO-02 (Policy reviewed/updated) | Medium   | ISO 27001         | Quarterly review cycle. Tracked in Obsidian with YAML frontmatter versioning.                                          | Policy Review Cadence - 2026                 |

---
## IDENTIFY (ID)
*The Identify function helps determine the current cybersecurity risk to the organization. You cannot protect what you do not know you have.*

| Policy/Control             | NIST Subcategory              | Priority | Compliance Target     | Implementation Detail                                                                                | Evidence                                         |
| :------------------------- | :---------------------------- | :------- | :-------------------- | :--------------------------------------------------------------------------------------------------- | :----------------------------------------------- |
| Asset Inventory            | ID.AM-01 (Hardware inventory) | High     | SOC 2 / ISO 27001 A.8 | All endpoints, servers, and network equipment cataloged with owner, classification, and criticality. | Planned - Phase 2                                |
| Software Inventory         | ID.AM-02 (Software inventory) | High     | SOC 2 / ISO 27001 A.8 | Approved software list maintained. Unauthorized software detected via endpoint monitoring.           | Planned - Phase 2                                |
| Data Flow Diagram          | ID.AM-03 (Data flows mapped)  | High     | GLBA / GDPR           | DFD shows data journey from endpoints → internal systems → cloud storage. Control overlay applied.   | 03_Architecture/Data-Flow-Diagram            |
| Data Classification Scheme | ID.AM-07 (Data inventoried)   | High     | GLBA / GDPR           | Three-tier classification: Confidential, Internal, Public. Defined in AUP Section 3.3.               | 01_Governance/Policies/Acceptable-Use-Policy |
| Risk Assessment            | ID.RA-03 (Threats identified) | Critical | SOC 2 / ISO 27001     | Threat modeling for mock org: ransomware, insider threat, phishing, third-party breach.              | Findings-Summary                             |
| Risk Assessment            | ID.RA-05 (Risk understood)    | Critical | SOC 2 / ISO 27001     | Likelihood × Impact scoring applied. Risk register maintained.                                       | Findings-Summary                             |
| Risk Response              | ID.RA-06 (Responses chosen)   | High     | Internal Audit        | Four response options: Mitigate, Accept, Transfer, Avoid. Each risk assigned a response.             | Findings-Summary                             |
| Policy/Control             | NIST Subcategory              | Priority | Compliance Target     | Implementation Detail                                                                                | Evidence                                         |

---
## PROTECT (PR)
*The Protect function provides safeguards to manage the organization's cybersecurity risks. These are the actual controls that reduce the likelihood or impact of threats.*

| Policy/Control | NIST Subcategory | Priority | Compliance Target | Implementation Detail | Evidence |
|:---|:---|:---|:---|:---|:---|
| Access Control / MFA | PR.AA-01 (Identities managed) | Critical | SOC 2 / GLBA | All user accounts require MFA. Privileged accounts use hardware tokens. Service accounts inventoried. | Planned - technical implementation |
| Least Privilege | PR.AA-05 (Access permissions defined) | High | SOC 2 / ISO 27001 A.8 | Role-based access control (RBAC). Quarterly access reviews. Defined in AUP Section 3.1. | 01_Governance/Policies/Acceptable-Use-Policy |
| Security Awareness Training | PR.AT-01 (Awareness provided) | Medium | SOC 2 / GLBA | Annual training for all staff. Phishing simulation quarterly. New hire training during onboarding. | Planned - training program |
| Data Encryption (at rest) | PR.DS-01 (Data-at-rest protected) | High | SOC 2 / GDPR | AES-256 encryption for all data at rest. Full disk encryption on all endpoints. Database encryption enabled. | DFD control overlay |
| Data Encryption (in transit) | PR.DS-02 (Data-in-transit protected) | High | SOC 2 / GDPR | TLS 1.2+ enforced on all connections. VPN required for remote access. Internal certificates managed via PKI. | DFD control overlay |
| Configuration Baselines | PR.PS-01 (Config management) | Medium | CIS Benchmarks | CIS Benchmark Level 1 applied to all servers and endpoints. Baselines documented and deviations tracked. | Planned - hardening |
| Patch Management | PR.PS-02 (Software maintained) | High | SOC 2 | Critical patches: 72 hours. High: 7 days. Medium: 30 days. Low: 90 days. Automated where possible. | Planned - patching SOP |
| Audit Logging | PR.PS-04 (Logs generated) | High | SOC 2 / ISO 27001 | All systems generate logs. Centralized in SIEM. 90-day minimum retention. | See DE.AE row below |
| Network Segmentation | PR.IR-01 (Network protected) | High | SOC 2 / PCI-DSS | Network zones: DMZ, Internal, Management. Firewall enforces inter-zone policies. | 03_Architecture/Data-Flow-Diagram |

---
## DETECT (DE)
*The Detect function finds and analyzes possible cybersecurity attacks and compromises. Without detection, you are operating blind.*

| Policy/Control | NIST Subcategory | Priority | Compliance Target | Implementation Detail | Evidence |
|:---|:---|:---|:---|:---|:---|
| SIEM / Continuous Monitoring | DE.CM-01 (Networks monitored) | High | SOC 2 / ISO 27001 | SIEM deployed for centralized event correlation. Network traffic analyzed for anomalies. | Planned - SIEM architecture |
| Endpoint Monitoring | DE.CM-09 (Computing assets monitored) | High | SOC 2 | EDR on all endpoints. File integrity monitoring on critical servers. | Planned - EDR deployment |
| Audit Logging & Retention | DE.AE-02 (Events analyzed) | Medium | ISO 27001 | 90-day retention for all SIEM logs. Automated correlation rules for known attack patterns. | Control table (this document) |
| Alert Correlation | DE.AE-03 (Information correlated) | Medium | SOC 2 | Multi-source log correlation: endpoint + network + authentication + application. | Planned - SIEM rules |
| Incident Declaration Criteria | DE.AE-08 (Incidents declared) | High | NIST SP 800-61 | Clear thresholds defined for when an anomaly becomes a declared incident. | 04_Incident-Response/Incident-Response-Plan |
  
---
## RESPOND (RS)
*The Respond function takes actions regarding a detected cybersecurity incident. Speed and structure matter - ad hoc responses cause more damage than the incident itself.*

| Policy/Control | NIST Subcategory | Priority | Compliance Target | Implementation Detail | Evidence |
|:---|:---|:---|:---|:---|:---|
| Incident Response Plan | RS.MA-01 (IRP executed) | Critical | NIST SP 800-61 | Six-stage response plan: Preparation, Identification, Containment, Eradication, Recovery, Lessons Learned. | 04_Incident-Response/Incident-Response-Plan |
| Incident Triage | RS.MA-02 (Reports triaged) | Critical | NIST SP 800-61 | Severity classification: P1 (Critical) through P4 (Informational). Defined escalation paths. | 04_Incident-Response/Incident-Response-Plan |
| Incident Categorization | RS.MA-03 (Incidents categorized) | High | SOC 2 | Incident types: malware, phishing, unauthorized access, data breach, DDoS, insider threat. | 04_Incident-Response/Incident-Response-Plan |
| Ransomware Playbook | RS.MI-01 (Incidents contained) | Critical | NIST SP 800-61 | Specific containment, eradication, and recovery steps for ransomware scenarios. | 04_Incident-Response/Incident-Response-Playbook-Ransomware |
| Evidence Preservation | RS.AN-07 (Data preserved) | High | Legal / Forensic | Chain of custody procedures. Evidence hashing (SHA-256). Forensic image requirements. | 04_Incident-Response/Incident-Response-Plan |
  
  ---
## RECOVER (RC)
*The Recover function restores assets and operations affected by a cybersecurity incident. Recovery is not just technical restoration - it includes communication and improvement.*

| Policy/Control | NIST Subcategory | Priority | Compliance Target | Implementation Detail | Evidence |
|:---|:---|:---|:---|:---|:---|
| Recovery Procedures | RC.RP-01 (Recovery plan executed) | High | SOC 2 | Restore from verified backups. Service restoration priority order defined. | 04_Incident-Response/Incident-Response-Plan |
| Backup Verification | RC.RP-03 (Backup integrity verified) | High | SOC 2 / ISO 27001 | Monthly backup restoration tests. Backup integrity hashing. Offsite backup verified. | Planned - backup SOP |
| Post-Incident Review | RC.CO-03 (Recovery communicated) | Medium | NIST SP 800-61 | Lessons learned report within 5 business days. Stakeholder communication plan. | 04_Incident-Response/Incident-Response-Plan |
  
  ---
## Summary: ISMS Control Table (Audit View)
*This condensed table matches the format from the project specification - the view an auditor would use for quick assessment.*

| Policy/Control | NIST Category | Priority | Compliance Target | Implementation Detail |
|:---|:---|:---|:---|:---|
| **Acceptable Use Policy** | GV.PO (Policy) | High | Internal Audit | Defines acceptable behavior, data handling, prohibited activities for all personnel. |
| **Incident Response Plan** | RS.RP (Respond) | Critical | NIST SP 800-61 | 6-stage response plan with ransomware-specific playbook. |
| **Data Encryption** | PR.DS (Protect) | High | SOC 2 / GDPR | AES-256 for data at rest; TLS 1.2+ for data in transit. |
| **Audit Logging** | DE.AE (Detect) | Medium | ISO 27001 | 90-day retention for SIEM logs. Multi-source correlation. |
| **Access Control (MFA)** | PR.AA (Protect) | Critical | SOC 2 / GLBA | MFA required for all users. Hardware tokens for privileged accounts. |
| **Risk Assessment** | ID.RA (Identify) | Critical | SOC 2 / ISO 27001 | Likelihood × Impact scoring. Formal risk register with response assignment. |
| **Network Segmentation** | PR.IR (Protect) | High | SOC 2 / PCI-DSS | DMZ, Internal, Management zones. Firewall-enforced inter-zone policies. |
| **RACI Matrix** | GV.RR (Govern) | High | ISO 27001 A.5 | CISO accountable for all security activities across 14 domains. |
| **Configuration Baselines** | PR.PS (Protect) | Medium | CIS Benchmarks | CIS Level 1 benchmarks on all systems. Deviation tracking. |
| **Ransomware Playbook** | RS.MI (Respond) | Critical | NIST SP 800-61 | Scenario-specific containment, eradication, and recovery procedures. |

---
## Gap Analysis Note

Controls marked "Planned" indicate areas where the policy or procedure has been defined but the technical implementation has not yet been deployed. In a real organization, these would appear on a Plan of Action and Milestones (POA&M) document. The gap analysis is captured in Findings-Summary.
