# Project 1 — Internal Security Audit (Botium Toys)

**Skills:** Risk assessment · NIST Cybersecurity Framework (CSF) · Controls & compliance · GRC

## 📌 Scenario
Botium Toys, a small e-commerce business, needs an internal security audit to assess its current
security posture and ensure it can protect assets and comply with regulations (e.g., **PCI DSS**,
**GDPR**). I performed a controls and compliance assessment aligned with the **NIST CSF**.

## 🎯 Objective
Identify gaps in the company's security controls and recommend improvements to reduce risk to
assets, especially customer payment data.

## 🔎 Scope & Assets
- On-premises equipment, employee devices, servers, internal network
- Accounting/payroll systems, customer PII and payment data
- Legacy systems with no current disaster-recovery plan

## 🧮 Risk Assessment
| Factor | Finding |
|---|---|
| **Risk score** | 8 / 10 (high) — inadequate controls on critical assets |
| **Primary risk** | Insufficient access controls & no encryption on stored data |
| **Compliance gaps** | PCI DSS (payment data), GDPR/PII handling |

## ✅ Controls Assessment Checklist (excerpt)
| Control | In place? | Priority |
|---|---|---|
| Least-privilege / RBAC | ❌ No | High |
| Firewall | ✅ Yes | — |
| Intrusion Detection System (IDS) | ❌ No | High |
| Data encryption (at rest / in transit) | ❌ No | High |
| Disaster recovery plan | ❌ No | High |
| Password policy & MFA | ⚠️ Partial | High |
| Antivirus software | ✅ Yes | — |
| Backups | ❌ No | Medium |

## 🛠️ Recommendations
1. Implement **least-privilege access controls** and RBAC.
2. Deploy an **IDS** and enable centralized logging.
3. Encrypt customer data **at rest and in transit** to meet PCI DSS.
4. Establish **MFA** and a strong password policy.
5. Build a **disaster recovery & backup** plan.

## 🧾 Outcome
Delivered a prioritized remediation roadmap mapping each gap to a NIST CSF function
(**Identify, Protect, Detect, Respond, Recover**), enabling leadership to reduce the highest
risks first.
