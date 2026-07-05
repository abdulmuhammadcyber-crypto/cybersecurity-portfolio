# Project 1: Internal Security Audit (Botium Toys)

Skills: Risk assessment, NIST Cybersecurity Framework (CSF), controls and compliance, governance and risk.

## Scenario

Botium Toys, a small e-commerce business, required an internal security audit to assess its current security posture and confirm it could protect its assets and meet regulatory requirements such as PCI DSS and GDPR. I performed a controls and compliance assessment aligned with the NIST CSF.

## Objective

Identify gaps in the company's security controls and recommend improvements to reduce risk to assets, with particular attention to customer payment data.

## Scope and Assets

- On-premises equipment, employee devices, servers, and the internal network
- Accounting and payroll systems, customer PII, and payment data
- Legacy systems with no current disaster-recovery plan

## Risk Assessment

| Factor | Finding |
|---|---|
| Risk score | 8 out of 10 (high) due to inadequate controls on critical assets |
| Primary risk | Insufficient access controls and no encryption on stored data |
| Compliance gaps | PCI DSS (payment data) and GDPR (PII handling) |

## Controls Assessment Checklist

*Question answered for each control: "Is this control currently in place?"*

| Control | Yes/No | Justification (from risk assessment report) |
|---|---|---|
| Least privilege | No | All employees have access to internally stored data, including cardholder data and PII/SPII |
| Encryption | No | Encryption is not used for credit card information that is accepted, processed, transmitted, and stored |
| Password policies | Yes | A password policy exists, though its requirements are nominal and below current complexity standards |
| Separation of duties | No | Least privilege and separation of duties have not been implemented |
| Firewall | Yes | The firewall blocks traffic based on an appropriately defined set of security rules |
| Intrusion detection system (IDS) | No | No IDS has been installed |
| Backups | No | The company does not have backups of critical data |
| Antivirus software | Yes | Antivirus software is installed and monitored regularly |
| Manual monitoring, maintenance, and intervention for legacy systems | No | Legacy systems are monitored but have no regular schedule and unclear intervention methods |
| Encryption (data confidentiality) | No | No encryption of stored or transmitted sensitive data |
| Password management system | No | No centralized password management system enforces the policy |
| Locks (offices, storefront, warehouse) | Yes | The physical location has sufficient locks |
| Closed-circuit television (CCTV) surveillance | Yes | Up-to-date CCTV surveillance is in place |
| Fire detection/prevention | Yes | Functioning fire detection and prevention systems are in place |

## Compliance Checklist

*Question answered for each best practice: "Is Botium Toys meeting this compliance requirement?"*

**PCI DSS (payment card data)**

| Best practice | Yes/No | Justification |
|---|---|---|
| Only authorized users can access cardholder data | No | All employees can access cardholder data |
| Cardholder data is secured and encrypted | No | Credit card information is not encrypted |
| Data encryption procedures are in place | No | Encryption is not currently used |

**GDPR (E.U. customers)**

| Best practice | Yes/No | Justification |
|---|---|---|
| E.U. customers' PII/SPII is kept private and secure | No | PII is unencrypted and accessible to all employees |
| Plan to notify authorities within 72 hours of a breach | Yes | A 72-hour breach notification plan is established |
| Privacy policies and procedures are developed and documented | Yes | Privacy policies, procedures, and processes are developed and enforced |

**SOC 1 / SOC 2 (data handling and integrity)**

| Best practice | Yes/No | Justification |
|---|---|---|
| User access policies are established | No | Access controls and least privilege are not implemented |
| Sensitive data (PII/SPII) is kept confidential | No | All employees can access sensitive data |
| Data integrity is ensured | Yes | The IT department integrated controls to ensure data integrity |
| Data availability is ensured | Yes | The IT department has ensured availability |

## Recommendations

1. Implement least-privilege access controls and role-based access control.
2. Deploy an Intrusion Detection System and enable centralized logging.
3. Encrypt customer data at rest and in transit to meet PCI DSS.
4. Establish MFA and enforce a strong password policy.
5. Build a disaster recovery and backup plan.

## Outcome

I delivered a prioritized remediation roadmap mapping each gap to a NIST CSF function (Identify, Protect, Detect, Respond, Recover), enabling leadership to address the highest risks first.
