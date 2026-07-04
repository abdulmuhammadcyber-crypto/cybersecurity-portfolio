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

## Controls Assessment Checklist (excerpt)

| Control | In place | Priority |
|---|---|---|
| Least privilege and role-based access control | No | High |
| Firewall | Yes | n/a |
| Intrusion Detection System | No | High |
| Data encryption at rest and in transit | No | High |
| Disaster recovery plan | No | High |
| Password policy and MFA | Partial | High |
| Antivirus software | Yes | n/a |
| Backups | No | Medium |

## Recommendations

1. Implement least-privilege access controls and role-based access control.
2. Deploy an Intrusion Detection System and enable centralized logging.
3. Encrypt customer data at rest and in transit to meet PCI DSS.
4. Establish MFA and enforce a strong password policy.
5. Build a disaster recovery and backup plan.

## Outcome

I delivered a prioritized remediation roadmap mapping each gap to a NIST CSF function (Identify, Protect, Detect, Respond, Recover), enabling leadership to address the highest risks first.
