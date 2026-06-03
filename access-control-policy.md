# Access Control Policy

| | |
|--|--|
| **Document Title** | Access Control Policy |
| **Version** | 1.0 |
| **Effective Date** | June 2026 |
| **Policy Owner** | Security Analyst |
| **Approved By** | Chief Information Security Officer (or designee) |
| **Review Cadence** | Annual |

---

## 1. Purpose

This policy defines how access to Veridian Freight & Logistics systems, data, and infrastructure is granted, maintained, modified, and removed. Veridian operates on AWS cloud infrastructure, Microsoft 365, a customer-facing logistics tracking web application, and multiple SaaS platforms handling HR, payroll, and CRM data. With a hybrid workforce spread across a headquarters and two regional offices, access control failures represent one of the most likely paths to data exposure, ransomware spread, and regulatory liability. This policy ensures that access to Veridian systems is always intentional, appropriately scoped, and actively managed throughout the employee lifecycle.

---

## 2. Scope

This policy applies to:

- All Veridian Freight & Logistics employees, contractors, temporary staff, and third-party vendors with any level of access to Veridian systems or data
- All Veridian information systems including AWS cloud infrastructure and IAM, Microsoft 365 (Entra ID / Active Directory), the Veridian logistics tracking web application, SaaS platforms (HR, payroll, CRM), and any other system containing Veridian or customer data
- All access types including standard user accounts, administrative accounts, privileged accounts, service accounts, and third-party vendor access
- All locations including headquarters, regional offices, and remote work environments

---

## 3. Policy Statements

### 3.1 Core Principles

All access decisions at Veridian must be governed by the following principles:

**3.1.1 Least Privilege:** Every user, system, and service account must be granted only the minimum level of access required to perform its defined function. Access must never be granted in excess of what the role requires.

**3.1.2 Need to Know:** Access to data must be limited to individuals whose job function requires that specific data. Access to customer PII, payroll data, and payment-related systems must be explicitly justified and approved.

**3.1.3 Separation of Duties:** No single individual should have the ability to perform and approve the same high-risk action without a second authorized party. Critical functions such as approving financial transactions, modifying production AWS infrastructure, or administering identity management systems must be distributed across at least two individuals.

### 3.2 Account Lifecycle

#### 3.2.1 Provisioning

3.2.1.1 Access to Veridian systems is provisioned only upon written request submitted by the new hire's manager to IT, specifying the systems required, the level of access needed, and the business justification.

3.2.1.2 IT must provision access only after receiving written manager approval. Access must not be granted based on verbal requests.

3.2.1.3 New hire access must be configured in accordance with a role-based access profile defined for that job function. Role profiles are maintained by IT in coordination with the Security Analyst.

3.2.1.4 All new accounts must be provisioned through Veridian's Microsoft Entra ID (Azure Active Directory) as the identity source of record. Access to AWS, SaaS platforms, and the logistics tracking application must be linked to this identity where technically feasible.

3.2.1.5 Contractors and third-party vendors must receive time-limited accounts scoped to the minimum access required for their engagement. Contractor accounts must expire automatically at the end of the contract period unless explicitly renewed with manager approval.

3.2.1.6 New accounts must not be provisioned with administrative or privileged access by default. Elevated access requires a separate approval process (see Section 3.5).

#### 3.2.2 Modification

3.2.2.1 When an employee changes roles, transfers to a different team, or takes on new responsibilities, their access must be reviewed and updated within 5 business days of the effective date of the change.

3.2.2.2 The employee's manager must submit a written access modification request to IT specifying what access should be added and what access should be removed.

3.2.2.3 Access associated with the previous role must be revoked at the time new access is granted. Employees must not accumulate access from prior roles.

3.2.2.4 IT must notify the Security Analyst of all access modifications involving privileged or administrative accounts.

#### 3.2.3 Deprovisioning

3.2.3.1 When an employee separates from Veridian, whether voluntarily or involuntarily, all system access must be revoked on the employee's last day of employment. For involuntary separations, access must be revoked at the time the separation is communicated, before the employee is notified where operationally feasible.

3.2.3.2 HR must notify IT of all pending separations no later than the business day before the employee's last day. For involuntary separations, HR must notify IT immediately.

3.2.3.3 Deprovisioning must include: disabling the Microsoft Entra ID account, revoking all active sessions and tokens in Microsoft 365, removing or disabling AWS IAM credentials, revoking access to the Veridian logistics tracking application, and removing access from all SaaS platforms including HR, payroll, and CRM systems.

3.2.3.4 IT must confirm in writing to the Security Analyst that deprovisioning is complete within 24 hours of the employee's separation. Any delays must be escalated to the Security Analyst immediately.

3.2.3.5 Company-owned devices must be returned and wiped. Personal devices enrolled in Veridian MDM must have company data remotely wiped upon separation.

3.2.3.6 Shared or generic accounts associated with a departing employee must have their credentials rotated immediately upon that employee's separation.

### 3.3 Authentication Requirements

3.3.1 Multi-factor authentication (MFA) is required for all remote access to Veridian systems including VPN, Microsoft 365, AWS Management Console, and the Veridian logistics tracking application.

3.3.2 MFA is required for all administrative and privileged accounts without exception, regardless of whether the access originates from an office location or remotely.

3.3.3 MFA must be configured through Microsoft Entra ID for all Microsoft 365 access. AWS IAM accounts must have MFA enforced at the account level.

3.3.4 Passwords for all Veridian accounts must meet the following minimum requirements: minimum 12 characters in length, include a combination of uppercase and lowercase letters, numbers, and special characters, and must not reuse any of the previous 10 passwords.

3.3.5 Passwords must not be shared, written down in accessible locations, or stored in unsecured files. Use of a company-approved password manager is encouraged.

3.3.6 Default or vendor-supplied credentials must be changed before any system or device is connected to the Veridian network or AWS environment.

3.3.7 Accounts must be locked after 10 consecutive failed login attempts. Account unlocking requires verification through IT.

### 3.4 Privileged Access

3.4.1 Privileged access includes any access that grants the ability to modify system configurations, manage user accounts, access all data within a system, or administer cloud infrastructure in AWS.

3.4.2 Privileged accounts must be separate from standard user accounts. An employee with both standard and administrative responsibilities must use a dedicated privileged account for administrative tasks and a separate standard account for daily work activities such as email and document access.

3.4.3 Privileged accounts must not be used for routine work activities including web browsing, email, or accessing non-administrative applications.

3.4.4 All privileged account activity must be logged. AWS CloudTrail must be enabled for all accounts and regions. Microsoft 365 unified audit logging must be enabled and retained for a minimum of 90 days.

3.4.5 Privileged access to production AWS environments must require approval from the Security Analyst for any change that is not part of a pre-approved maintenance window.

3.4.6 Service accounts used for automated processes must be inventoried, owned by a named individual, and reviewed quarterly. Service account credentials must be rotated at minimum annually or immediately following any suspected compromise.

3.4.7 The number of individuals with privileged access must be kept to the minimum necessary. The Security Analyst must review and approve all privileged access grants.

### 3.5 Access Reviews

3.5.1 IT must conduct a quarterly access review of all user accounts across Microsoft 365, AWS IAM, the Veridian logistics tracking application, and all SaaS platforms.

3.5.2 During each quarterly review, managers must certify that each of their direct reports has access that is appropriate for their current role. Access that cannot be justified must be revoked within 5 business days of the review.

3.5.3 Privileged and administrative accounts must be reviewed monthly. Any privileged account that has not been used within 30 days must be disabled pending review.

3.5.4 The Security Analyst must review all access review results and track any identified gaps to remediation.

3.5.5 Access review results must be documented and retained for a minimum of 12 months.

### 3.6 Remote Access

3.6.1 Remote access to Veridian internal systems must be conducted through Veridian's approved VPN. Employees must not access internal systems over unencrypted or unapproved channels.

3.6.2 MFA is required for all VPN connections (see Section 3.3).

3.6.3 Employees must not use public or unsecured Wi-Fi networks for VPN connections without explicit approval from IT. If a public network must be used, the VPN must be active before any Veridian system is accessed.

3.6.4 Remote access sessions must be configured to time out and require reauthentication after 30 minutes of inactivity.

3.6.5 Third-party vendors requiring remote access to Veridian systems must use a dedicated, time-limited account and must access systems through an IT-approved secure remote access method. Vendor access must be monitored and must not be persistent.

---

## 4. Roles and Responsibilities

| Role | Responsibility |
|------|---------------|
| All Employees | Use only the access assigned to them. Report suspected unauthorized access immediately. Return company devices upon separation. |
| Managers | Submit access requests for direct reports. Certify access appropriateness during quarterly reviews. Notify HR and IT of role changes and separations in advance. |
| HR Department | Notify IT of all new hires, role changes, and separations within required timeframes. Coordinate device return at offboarding. |
| IT Department | Provision, modify, and deprovision access per policy. Conduct quarterly access reviews. Maintain access logs. Confirm deprovisioning completion to Security Analyst. |
| Security Analyst | Own and maintain this policy. Approve privileged access grants. Review access review results. Investigate access control violations. Conduct annual policy review. |

---

## 5. Enforcement

Violations of this policy including unauthorized access attempts, sharing of credentials, failure to report a separation, or circumvention of access controls may result in disciplinary action up to and including termination. Violations involving unauthorized access to customer PII or payment data will be escalated to Legal Counsel and may be reported to law enforcement.

---

## 6. Review Cadence

This policy will be reviewed annually by the Security Analyst. It will also be reviewed following any security incident in which an access control failure was identified as a contributing factor.

---

## 7. Revision History

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 1.0 | June 2026 | Josh Gouvisis, Security Analyst | Initial policy creation |

---

*NIST CSF 2.0 Alignment: PR.AA-01, PR.AA-02, PR.AA-03, PR.AA-05, PR.AC-01, PR.AC-03, PR.AC-04, PR.AC-07, PR.PS-01*
