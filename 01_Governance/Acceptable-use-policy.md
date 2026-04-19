---
title: Acceptable Use Policy
policy_id: MFS-POL-001
author: Darcy
date: 2026-03-07
version: "1.0"
status: draft
approved_by: "[CISO Name]"
review_date: 2026-06-01
nist_mapping:
  - GV.PO-01
  - GV.PO-02
  - PR.AA-05
tags:
  - compliance/nist/govern
  - compliance/nist/protect
  - type/policy
  - phase/2-execution
  - status/draft
---
# Acceptable Use Policy

**Wayne Financial Services**

**Policy ID:** MFS-POL-001

**Effective Date:** [Date]

**Last Reviewed:** [Date]

**Next Review:** Quarterly (see [[Policy Review Cadence - 2026]])

---
## 1. Purpose

This policy defines the acceptable use of information technology resources at Wayne Financial Services. It exists to protect the organization's data, systems, and reputation by establishing clear expectations for all personnel who access company resources.

**NIST CSF Alignment:** This policy directly supports **GV.PO-01** (cybersecurity policy is established based on organizational context) and **GV.PO-02** (policy is reviewed and updated).

---
## 2. Scope

This policy applies to:

- All employees, contractors, and temporary staff
- All company-owned and company-managed devices (laptops, mobile devices, servers)
- All company data regardless of where it is stored or processed
- All network resources including VPN, Wi-Fi, and cloud services (Microsoft 365, AWS)
- Personal devices used to access company resources (BYOD)

---
## 3. Policy Statements
### 3.1 General Use

Company IT resources are provided for business purposes. Limited personal use is permitted provided it does not interfere with work duties, consume excessive resources, or violate any other provision of this policy.

All users must:

- Use company resources only for authorized business activities
- Protect their login credentials and never share passwords
- Lock their workstation when unattended (automatic lock after 5 minutes of inactivity)
- Report suspected security incidents immediately per the [[04_Incident-Response/Incident-Response-Plan]]  
### 3.2 Prohibited Activities

The following activities are prohibited on company resources:

- Accessing, downloading, or distributing illegal content
- Installing unauthorized software without IT approval
- Connecting unauthorized devices to the corporate network
- Attempting to bypass or disable security controls (antivirus, firewall, DLP)
- Sharing company data through unapproved channels (personal email, unauthorized cloud storage)
- Using company resources for cryptocurrency mining or personal commercial ventures
### 3.3 Data Handling
All company data must be handled according to its classification:

| Classification | Definition | Handling Requirements |
|---------------|-----------|----------------------|
| **Confidential** | PII, financial records, credentials, trade secrets | Encrypted at rest (AES-256) and in transit (TLS 1.2+). Access restricted to need-to-know. No external sharing without CISO approval. |
| **Internal** | Internal communications, non-public reports, procedures | Store on approved company systems only. Do not share externally without manager approval. |
| **Public** | Published marketing materials, press releases | No special handling required. |

**NIST CSF Alignment:** Data classification supports **PR.DS-01** (data-at-rest protection), **PR.DS-02** (data-in-transit protection), and **ID.AM-07** (data inventory and metadata).
### 3.4 Email and Communications

- Company email must not be used for personal financial transactions
- Sensitive data must not be sent via email without encryption
- Users must verify sender identity before clicking links or opening attachments
- Suspected phishing emails must be reported to the security team immediately
### 3.5 Remote Access

- Remote access to company resources requires VPN with multi-factor authentication (MFA)
- Company data must not be stored on personal devices unless the device is enrolled in the MDM program
- Public Wi-Fi must not be used to access company resources without an active VPN connection
### 3.6 Physical Security

- Laptops must be physically secured when in public spaces
- Removable media (USB drives) are prohibited unless explicitly approved by IT
- Printed confidential documents must be retrieved promptly and shredded when no longer needed
---
## 4. Enforcement
### 4.1 Monitoring

Meridian Financial Services reserves the right to monitor, log, and audit all use of company IT resources. This includes network traffic, email communications, file access, and authentication events. Monitoring data is retained for a minimum of 90 days per the audit logging requirements (see [[02_Framework-Mapping/NIST-CSF-Master-Crosswalk]] — DE.AE).

### 4.2 Violations
Violations of this policy may result in:

- Verbal or written warning
- Temporary suspension of IT access
- Termination of employment
- Legal action where applicable

The severity of the response is proportional to the violation and is determined by the employee's manager in consultation with HR and the CISO.

---
## 5. Roles and Responsibilities

| Role | Responsibility |
|------|---------------|
| **All Users** | Read, understand, and comply with this policy |
| **IT Department** | Implement technical controls that enforce this policy; respond to violations |
| **CISO** | Approve policy; make risk-based exceptions; oversee compliance |
| **HR** | Ensure policy is acknowledged during onboarding; support enforcement actions |
| **Managers** | Ensure team members are aware of and comply with this policy |
See [[01_Governance/Roles/RACI-Matrix]]  for the full responsibility assignment matrix

---
## 6. Exceptions

Exceptions to this policy require written approval from the CISO. Exception requests must include:

- The specific policy provision being excepted
- Business justification
- Duration of the exception
- Compensating controls in place
- Risk assessment

Approved exceptions are logged in the risk register and reviewed quarterly.

---
## 7. Review and Maintenance

This policy is reviewed **quarterly** and updated as needed based on:

- Changes in regulatory requirements
- Findings from audits or security incidents
- Changes in technology or business operations
- Results from the PDCA improvement cycle

The review schedule is tracked in [[Policy Review Cadence - 2026]].

**NIST CSF Alignment:** Review cadence supports **GV.PO-02** (policy for managing cybersecurity risks is reviewed, updated, communicated, and enforced).

---
## 8. Acknowledgment
All personnel must sign an acknowledgment confirming they have read, understood, and agree to comply with this policy. Acknowledgment is required at onboarding and annually thereafter.

```

I, _________________________, acknowledge that I have read and understood

the Meridian Financial Services Acceptable Use Policy (MFS-POL-001).

I agree to comply with all provisions of this policy.

  

Signature: _________________________ Date: _______________

```

  

---
## Document History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | [Date] | [Your Name] | Initial draft 
  
---
## Related Notes

- [[04_Incident-Response/Incident-Response-Plan]] — Referenced in Section 3.1 for incident reporting

- [[01_Governance/Roles/RACI-Matrix]] — Referenced in Section 5 for responsibility assignments

- [[02_Framework-Mapping/NIST-CSF-Master-Crosswalk]] — Full NIST CSF control mapping

- [[Policy Review Cadence - 2026]] — Review schedule