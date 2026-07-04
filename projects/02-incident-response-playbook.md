# Project 2 — Incident Response Playbook

Skills: Incident response lifecycle, playbook design, escalation, NIST SP 800-61.

## Scenario

An organization needed a repeatable playbook so analysts respond to security incidents consistently. I built a playbook for a ransomware and malware incident aligned with the NIST Incident Response Lifecycle.

## NIST Incident Response Lifecycle

1. Preparation — tooling, contacts, backups, and training
2. Detection and Analysis — alerts, triage, and scoping
3. Containment, Eradication, and Recovery — isolate, remove, and restore
4. Post-Incident Activity — lessons learned and reporting

## Playbook — Ransomware Detected

### Phase 1: Detection and Analysis

- Confirm the alert from the SIEM or EDR (encrypted files, ransom note, mass file changes)
- Identify affected hosts, users, and data
- Determine the ransomware variant and initial access vector, such as phishing
- Assign a severity level and open an incident ticket

### Phase 2: Containment

- Isolate infected hosts from the network by disabling the network interface or quarantining in EDR
- Disable compromised accounts
- Block malicious IP addresses and domains at the firewall
- Preserve evidence, including memory, disk images, and logs

### Phase 3: Eradication and Recovery

- Remove the malware and any persistence mechanisms
- Patch the exploited vulnerability
- Restore data from clean backups
- Verify systems are clean before reconnecting them

### Phase 4: Post-Incident

- Conduct a lessons-learned review
- Update detection rules and controls
- Document the timeline and impact in the final report

## Escalation Matrix

| Severity | Escalate to | Response time |
|---|---|---|
| Low | Tier 1 analyst | 24 hours |
| Medium | Tier 2 or SOC lead | 4 hours |
| High or Critical | CISO and IR team | Immediate |

## Outcome

The result is a reusable, checklist-driven playbook that reduces mean time to respond and ensures consistent, defensible handling of incidents.
