# Incident Response Policy

| | |
|--|--|
| **Document Title** | Incident Response Policy |
| **Version** | 1.0 |
| **Effective Date** | June 2026 |
| **Policy Owner** | Security Analyst |
| **Approved By** | Chief Information Security Officer (or designee) |
| **Review Cadence** | Annual |

---

## 1. Purpose

This policy establishes how Veridian Freight & Logistics prepares for, detects, responds to, and recovers from cybersecurity incidents. Veridian operates on AWS cloud infrastructure, uses Microsoft 365, maintains a customer-facing logistics tracking web application, stores customer PII, and processes payment card data through a third-party processor. A security incident affecting any of these systems can disrupt operations, expose customer data, trigger regulatory obligations, and damage enterprise client relationships. Leadership has identified ransomware as a top concern following a recent incident at a direct competitor. This policy exists to ensure that when an incident occurs, Veridian responds in a structured, timely, and effective way rather than improvising under pressure.

---

## 2. Scope

This policy applies to:

- All Veridian Freight & Logistics employees, contractors, and third-party vendors
- All Veridian information systems, including AWS infrastructure, Microsoft 365, the Veridian logistics tracking web application, SaaS platforms (HR, payroll, CRM), and any endpoint used to access Veridian systems
- All locations including headquarters, regional offices, and remote work environments
- All cybersecurity incidents regardless of severity, origin, or whether they result in confirmed data loss

---

## 3. Policy Statements

### 3.1 Incident Definition

A security incident is any event that threatens the confidentiality, integrity, or availability of Veridian systems or data. Incidents include but are not limited to:

- Ransomware infection or any malware execution on Veridian systems or AWS infrastructure
- Phishing attack resulting in credential compromise or unauthorized account access
- Unauthorized access to the Veridian logistics tracking application or any internal system
- Exposure or potential exposure of customer PII or payment card data
- Loss or theft of a company-owned or employee-owned device containing Veridian data
- Denial of service attack affecting Veridian operations or the customer-facing logistics application
- Insider threat activity including unauthorized data access, exfiltration, or sabotage
- Compromise of a third-party vendor or SaaS platform that has access to Veridian data

Events that do not meet the threshold of an incident (such as blocked phishing emails with no user interaction or routine vulnerability scan alerts) are classified as security events and handled through standard IT operations. Any event with uncertainty about its severity must be treated as an incident until confirmed otherwise.

### 3.2 Severity Classification

All incidents are assigned a severity level at the time of initial triage. Severity may be escalated as new information becomes available.

| Severity | Definition | Examples |
|----------|-----------|---------|
| **Critical** | Active incident causing or likely to cause significant operational disruption, confirmed data breach, or regulatory notification obligation. Requires immediate response around the clock. | Ransomware executing on Veridian systems, confirmed exfiltration of customer PII or payment data, complete outage of the logistics tracking application, compromise of AWS root or administrative credentials |
| **High** | Incident with significant potential impact that has not yet caused confirmed data loss or full operational disruption. Requires response within 2 hours. | Phishing attack with confirmed credential compromise, malware detected on endpoint before execution confirmed, unauthorized access to internal systems detected, lost or stolen device with unencrypted Veridian data |
| **Medium** | Incident with limited confirmed impact but potential to escalate. Requires response within 8 hours during business hours. | Phishing email with user click but no confirmed credential entry, unauthorized access attempt blocked but originating from an internal IP, suspicious activity in Microsoft 365 audit logs |
| **Low** | Incident with minimal confirmed or potential impact. Requires response within the next business day. | Lost device with no Veridian data confirmed, policy violation with no data exposure, isolated malware detection on a non-critical system with no lateral movement |

### 3.3 Incident Response Phases

#### 3.3.1 Preparation

Preparation is ongoing and precedes any specific incident. It includes:

- Maintaining this policy and all supporting incident response playbooks
- Ensuring all employees know how to report a suspected incident (see Section 3.5)
- Maintaining an up-to-date contact list for the Incident Response Team including after-hours contacts
- Ensuring logging is enabled and retained for all critical systems including AWS CloudTrail, Microsoft 365 audit logs, and the Veridian logistics tracking application
- Conducting tabletop exercises at minimum twice per year to test incident response procedures against realistic scenarios including ransomware and phishing-driven account compromise
- Ensuring backup and recovery procedures are documented and tested quarterly

#### 3.3.2 Detection and Analysis

3.3.2.1 Incidents may be detected through automated alerts from security tools, employee reports, vendor notifications, or external parties such as customers or law enforcement.

3.3.2.2 Upon receiving a report or alert, the Security Analyst must assess the event to determine whether it meets the definition of a security incident and assign an initial severity level.

3.3.2.3 The Security Analyst must document all findings, observations, and actions taken from the moment of detection. Documentation must be maintained in a dedicated incident log and must not be deleted or altered once created.

3.3.2.4 The Security Analyst must notify the Incident Response Team within the timeframe defined by the assigned severity level (see Section 3.2).

3.3.2.5 During analysis, the following must be determined as quickly as possible: what systems are affected, what data may have been accessed or exposed, how the incident occurred, and whether the incident is ongoing.

#### 3.3.3 Containment, Eradication, and Recovery

**Containment**

3.3.3.1 The primary goal of containment is to stop the incident from spreading while preserving evidence for investigation.

3.3.3.2 Containment actions must be proportionate to severity. For Critical and High severity incidents, containment may include isolating affected systems from the network, disabling compromised accounts, blocking malicious IP addresses or domains at the firewall, and suspending access to affected AWS resources.

3.3.3.3 Affected systems must not be wiped, reimaged, or powered off without explicit authorization from the Security Analyst, as doing so may destroy evidence required for investigation and regulatory compliance.

3.3.3.4 Evidence must be preserved before containment actions wherever possible. This includes capturing memory images, preserving logs, and taking snapshots of affected AWS instances before any remediation.

**Eradication**

3.3.3.5 Once the incident is contained, the Security Analyst and IT must identify and remove the root cause. This includes removing malware, closing exploited vulnerabilities, revoking compromised credentials, and auditing affected systems for persistence mechanisms.

3.3.3.6 Systems must not be returned to production until the Security Analyst confirms the root cause has been fully addressed.

**Recovery**

3.3.3.7 Systems are restored to normal operation using clean backups where applicable. Restoration must be validated before systems are returned to production.

3.3.3.8 The Security Analyst must monitor restored systems for at least 72 hours following recovery for any sign of reinfection or recurring malicious activity.

3.3.3.9 Recovery timelines must be communicated to affected business units and, where applicable, to customers or enterprise clients.

#### 3.3.4 Post-Incident Activity

3.3.4.1 A post-incident review must be conducted within 14 days of incident closure for all High and Critical severity incidents and within 30 days for Medium severity incidents.

3.3.4.2 The post-incident review must produce a written after-action report documenting: a timeline of the incident, root cause analysis, effectiveness of the response, and specific corrective actions to prevent recurrence.

3.3.4.3 Corrective actions must be assigned to named owners with target completion dates and tracked to closure by the Security Analyst.

3.3.4.4 Lessons learned from each incident must be used to update response playbooks, this policy, and security awareness training content where applicable.

### 3.4 Incident Response Team

| Role | Responsibility |
|------|---------------|
| Security Analyst (IR Lead) | Owns the incident response process. Leads detection, analysis, containment, and post-incident review. Maintains incident documentation. |
| IT Lead | Executes technical containment and eradication actions. Manages system isolation, credential revocation, and system restoration. |
| Executive Sponsor (CEO or COO) | Receives briefings on High and Critical severity incidents. Authorizes significant business decisions during an incident (e.g., taking systems offline, notifying customers). |
| Legal Counsel | Engaged for any incident with potential regulatory notification obligations or litigation risk. Advises on customer and regulator communication. |
| Communications Lead | Manages internal employee communication and, in coordination with Legal, any external communication to customers or enterprise clients. |
| HR | Engaged for incidents involving insider threat activity or employee policy violations. |

For incidents where a dedicated CISO has not yet been hired, the Security Analyst reports directly to the Executive Sponsor.

### 3.5 Reporting and Escalation

3.5.1 All employees must report suspected security incidents immediately to IT by emailing security@veridianfreight.com or calling the IT help desk. Employees must not attempt to investigate or remediate suspected incidents themselves.

3.5.2 Employees must report the following without delay regardless of time of day: ransomware or malware alerts on any device, suspected phishing with credential entry, loss or theft of any device containing Veridian data, and any unusual system behavior that may indicate unauthorized access.

3.5.3 Upon receiving a report, IT must notify the Security Analyst within 30 minutes.

3.5.4 The Security Analyst must escalate to the Executive Sponsor within 1 hour for any incident classified as Critical or High severity.

3.5.5 Legal Counsel must be notified within 2 hours for any incident involving confirmed or suspected exposure of customer PII or payment card data.

### 3.6 Communication

**Internal Communication**

3.6.1 The Security Analyst must provide status updates to the Incident Response Team at a cadence appropriate to severity: every hour for Critical incidents, every 4 hours for High, and at the close of each business day for Medium.

3.6.2 Employees not on the Incident Response Team must not discuss incident details outside of authorized communication channels. Information about active incidents must be treated as confidential.

**External Communication**

3.6.3 All external communication regarding a security incident, including communication to customers, enterprise clients, regulators, and media, must be approved by Legal Counsel and the Executive Sponsor before release.

3.6.4 Veridian must notify affected customers within 72 hours of confirming that their PII has been exposed, in compliance with applicable state and federal notification requirements.

3.6.5 Regulatory notification timelines must be tracked by Legal Counsel and met without exception.

### 3.7 Evidence Handling

3.7.1 All evidence related to a security incident must be preserved from the moment the incident is detected. Evidence includes system logs, email records, network traffic captures, AWS CloudTrail logs, Microsoft 365 audit logs, memory images, and any other data relevant to understanding the incident.

3.7.2 Evidence must be stored securely and access restricted to members of the Incident Response Team and Legal Counsel.

3.7.3 Evidence must not be altered, deleted, or overwritten. Any action taken on an affected system must be documented in the incident log before it is taken.

3.7.4 Evidence must be retained for a minimum of 12 months following incident closure or longer if required by legal or regulatory obligation.

---

## 4. Roles and Responsibilities

| Role | Responsibility |
|------|---------------|
| All Employees | Report suspected incidents immediately. Do not attempt self-remediation. Cooperate fully with the Incident Response Team. |
| Managers | Ensure direct reports know how to report an incident. Support the IR Team by providing information about affected employees or systems. |
| IT Department | Receive and triage employee incident reports. Execute technical containment and recovery actions under direction of the Security Analyst. |
| Security Analyst | Lead all incident response activities. Maintain this policy and incident playbooks. Conduct post-incident reviews. Report to Executive Sponsor on High and Critical incidents. |
| Legal Counsel | Advise on regulatory notification obligations. Review and approve all external communications. |
| Executive Sponsor | Authorize major response decisions. Receive briefings on High and Critical incidents. |

---

## 5. Enforcement

Failure to report a suspected incident in a timely manner, interference with an active incident investigation, or intentional destruction of evidence may result in disciplinary action up to and including termination. Employees who experience or witness a security incident and do not report it will be held accountable under this policy regardless of whether they were involved in causing the incident.

---

## 6. Review Cadence

This policy will be reviewed annually by the Security Analyst. It will also be reviewed and updated following any High or Critical severity incident where gaps in current procedures are identified.

---

## 7. Revision History

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 1.0 | June 2026 | Josh Gouvisis, Security Analyst | Initial policy creation |

---

*NIST CSF 2.0 Alignment: DE.AE-02, DE.AE-03, DE.CM-01, RS.MA-01, RS.MA-02, RS.AN-01, RS.AN-03, RS.MI-01, RS.CO-02, RS.CO-03, RC.RP-01, RC.CO-01*
