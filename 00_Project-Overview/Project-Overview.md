# Project Metadata

| **Field**              | **Value**                                                |
| ---------------------- | -------------------------------------------------------- |
| Organization Name      | Wayne Financial Services (mock)                          |
| Industry               | Financial Services                                       |
| Size                   | 200 employees                                            |
| Regulatory Environment | Subject to SOC 2, GLBA, and internal audit               |
| Data Sensitivity       | PII, financial records, internal communications          |
| IT Environment         | Hybrid (on-premises + cloud), Microsoft 365, AWS         |
| Risk Appetite          | Low — conservative posture due to regulatory obligations |
# Roles

| Letter | Meaning     | Definition                                                 |
| ------ | ----------- | ---------------------------------------------------------- |
| **R**  | Responsible | Does the work                                              |
| **A**  | Accountable | Owns the outcome; makes final decisions (only one per row) |
| **C**  | Consulted   | Provides input before a decision is made                   |
| **I**  | Informed    | Notified after a decision or action is taken               |

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

# Acceptable-Use-Policy

#### Purpose: 
This policy defines the acceptable use of information technology resources at Wayne Financial Services. It exists to protect the organization's data, systems, and reputation by establishing clear expectations for all personnel who access company resources.

This policy directly supports **GV.PO-01** (cybersecurity policy is established based on organizational context) and **GV.PO-02** (policy is reviewed and updated).

#### Scope: 
This policy applies to:

- All employees, contractors, and temporary staff
- All company-owned and company-managed devices (laptops, mobile devices, servers)
- All company data regardless of where it is stored or processed
- All network resources including VPN, Wi-Fi, and cloud services (Microsoft 365, AWS)
- Personal devices used to access company resources (BYOD)

#### Allowed Use: 
Company IT resources are provided for business purposes. Limited personal use is permitted provided it does not interfere with work duties, consume excessive resources, or violate any other provision of this policy.

All users must:

- Use company resources only for authorized business activities
- Protect their login credentials and never share passwords
- Lock their workstation when unattended (automatic lock after 5 minutes of inactivity)
- Report suspected security incidents immediately per the [[04_Incident-Response/Incident-Response-Plan]]  
#### Prohibited Activities:
The following activities are prohibited on company resources:

- Accessing, downloading, or distributing illegal content
- Installing unauthorized software without IT approval
- Connecting unauthorized devices to the corporate network
- Attempting to bypass or disable security controls (antivirus, firewall, DLP)
- Sharing company data through unapproved channels (personal email, unauthorized cloud storage)
- Using company resources for cryptocurrency mining or personal commercial ventures
#### Monitoring Notice:
Wayne Financial Services reserves the right to monitor, log, and audit all use of company IT resources. This includes network traffic, email communications, file access, and authentication events. Monitoring data is retained for a minimum of 90 days per the audit logging requirements
#### Violations: 
Violations of this policy may result in:

- Verbal or written warning
- Temporary suspension of IT access
- Termination of employment
- Legal action, where applicable

The severity of the response is proportional to the violation and is determined by the employee's manager in consultation with HR and the CISO.

![[Pasted image 20260308013039.png]]