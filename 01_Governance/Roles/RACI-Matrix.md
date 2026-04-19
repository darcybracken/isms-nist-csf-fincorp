---
"title:": RACI Matrix — Information Security
author: D'Arcy
Start_Date: 2026-03-07
version: "1.0"
status: active
nist_mapping:
  - GV.RR-01
  - GV.RR-02
  - GV.RR-03
tags:
  - compliance/nist/govern
  - type/procedure
  - phase/2-execution
---
## What Is RACI?
RACI is a responsibility assignment model that clarifies who does what for each task or decision. It prevents ambiguity - the number one governance failure in information security.

| Letter | Meaning     | Definition                                                 |
| ------ | ----------- | ---------------------------------------------------------- |
| **R**  | Responsible | Does the work                                              |
| **A**  | Accountable | Owns the outcome; makes final decisions (only one per row) |
| **C**  | Consulted   | Provides input before a decision is made                   |
| **I**  | Informed    | Notified after a decision or action is taken               |

---

## Wayne Financial Services — Security RACI

| Activity                       | CEO | CISO | IT Director | Security Team | HR  | All Staff |
| ------------------------------ | --- | ---- | ----------- | ------------- | --- | --------- |
| Approve security policies      | I   | A    | C           | R             | C   | I         |
| Define risk appetite           | A   | R    | C           | I             | I   | I         |
| Conduct risk assessments       | I   | A    | C           | R             | I   | I         |
| Implement technical controls   | I   | A    | R           | R             | I   | I         |
| Monitor security events (SIEM) | I   | A    | I           | R             | I   | I         |
| Respond to security incidents  | I   | A    | C           | R             | C   | I         |
| Manage user access             | I   | A    | R           | R             | C   | I         |
| Security awareness training    | I   | A    | C           | R             | R   | R         |
| Audit and compliance review    | C   | A    | C           | R             | I   | I         |
| Third-party risk assessment    | I   | A    | C           | R             | I   | I         |
| Incident post-mortem review    | I   | A    | R           | R             | C   | I         |
| Policy exception approval      | I   | A    | C           | I             | I   | I         |
| Data classification decisions  | I   | A    | R           | C             | I   | R         |
| Backup and recovery testing    | I   | A    | R           | R             | I   | I         |

---

## Key Observations

**The CISO is Accountable for nearly everything.** This is by design in a small-to-mid-size organization. The CISO is the single point of accountability for security decisions, even when the work is delegated. This aligns with NIST CSF **GV.RR-01** (organizational leadership is responsible and accountable).

**"All Staff" is Responsible for training and data classification.** Security is not just an IT problem. Every employee handles data and must classify it correctly. This reflects the NIST CSF principle that security culture is a governance function.

**HR is Consulted on incidents and enforcement.** Personnel actions resulting from security violations require HR involvement. This is a compliance safeguard — it prevents ad hoc disciplinary decisions.

---
## NIST CSF Alignment

| NIST Subcategory | How This Matrix Supports It |
|------------------|-----------------------------|
| GV.RR-01 | Leadership accountability is explicitly assigned (CEO/CISO rows) |
| GV.RR-02 | Roles, responsibilities, and authorities are defined for every security activity |
| GV.RR-03 | Resource allocation is implicit — the "R" column shows where work is assigned |

---

## Related Notes

- [[Governance-Index]]
- [[Labs/Lab-003-ISMS/01_Governance/Acceptable-use-policy]] — Section 5 (Roles and Responsibilities)
- [[02_Framework-Mapping/NIST-CSF-Master-Crosswalk]] — GV.RR subcategories