# Botium Toys — Controls and Compliance Checklist

**Auditor:** Mohammad Saeed
**Framework:** NIST Cybersecurity Framework (CSF)
**Overall risk score:** 8 / 10 (high)

This checklist was completed by reviewing the Botium Toys scope, goals, and risk
assessment report — focusing on the assets managed by the IT department and the
bullet points under "Additional comments" in the risk assessment section.

---

## Controls Assessment

*Yes/No — "Is this control currently in place?"*

| Control | Yes/No | Justification |
|---|---|---|
| Least privilege | No | All employees have access to internally stored data, including cardholder data and PII/SPII |
| Encryption | No | Encryption is not used for credit card information |
| Password policies | Yes | A password policy exists, but its requirements are nominal and below best practice |
| Separation of duties | No | Least privilege and separation of duties have not been implemented |
| Firewall | Yes | Blocks traffic based on an appropriately defined set of security rules |
| Intrusion detection system (IDS) | No | No IDS has been installed |
| Backups | No | No backups of critical data exist |
| Antivirus software | Yes | Installed and monitored regularly |
| Manual monitoring, maintenance, and intervention for legacy systems | No | No regular schedule; intervention methods are unclear |
| Encryption (data confidentiality) | No | No encryption of stored/transmitted sensitive data |
| Password management system | No | No centralized password management system |
| Locks (offices, storefront, warehouse) | Yes | Sufficient locks are in place |
| Closed-circuit television (CCTV) surveillance | Yes | Up-to-date CCTV surveillance is in place |
| Fire detection/prevention | Yes | Functioning fire detection and prevention systems |

---

## Compliance Checklist

*Yes/No — "Is Botium Toys meeting this compliance best practice?"*

### PCI DSS (payment card data)

| Best practice | Yes/No | Justification |
|---|---|---|
| Only authorized users can access cardholder data | No | All employees can access cardholder data |
| Cardholder data is secured and encrypted | No | Credit card information is not encrypted |
| Data encryption procedures are in place | No | Encryption is not currently used |

### GDPR (E.U. customers)

| Best practice | Yes/No | Justification |
|---|---|---|
| E.U. customers' PII/SPII is kept private and secure | No | PII is unencrypted and accessible to all employees |
| Plan to notify authorities within 72 hours of a breach | Yes | 72-hour breach notification plan is established |
| Privacy policies and procedures are developed and documented | Yes | Privacy policies, procedures, and processes are enforced |

### SOC 1 / SOC 2 (data handling and integrity)

| Best practice | Yes/No | Justification |
|---|---|---|
| User access policies are established | No | Access controls and least privilege are not implemented |
| Sensitive data (PII/SPII) is kept confidential | No | All employees can access sensitive data |
| Data integrity is ensured | Yes | Controls integrated to ensure data integrity |
| Data availability is ensured | Yes | Availability has been ensured by the IT department |

---

## Recommendation to the IT Manager

Botium Toys should first close the highest-impact gaps that drive both risk and
regulatory exposure:

1. **Implement least privilege and separation of duties** so only authorized staff
   can reach cardholder data and PII/SPII (addresses PCI DSS, GDPR, and SOC).
2. **Encrypt sensitive data** at rest and in transit — especially credit card data —
   to meet PCI DSS.
3. **Deploy an intrusion detection system (IDS)** and centralized logging to improve
   the Detect function of the NIST CSF.
4. **Establish backups and a disaster recovery plan** to protect business continuity.
5. **Strengthen the password policy** and add a centralized password management
   system that enforces minimum complexity requirements.
6. **Set a regular maintenance schedule** and clear intervention procedures for
   legacy systems.

Physical controls (locks, CCTV, fire prevention), the firewall, antivirus, the
72-hour breach notification plan, documented privacy policies, and data
integrity/availability controls are already in place and should be maintained.
