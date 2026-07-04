# Project 2 — Incident Response Playbook

**Skills:** IR lifecycle · Playbook design · Escalation · NIST SP 800-61

## 📌 Scenario
An organization needs a repeatable playbook so analysts respond to security incidents consistently.
I built a playbook for a **ransomware / malware** incident aligned with the **NIST Incident Response
Lifecycle**.

## 🔄 NIST IR Lifecycle
1. **Preparation** — tooling, contacts, backups, training
2. **Detection & Analysis** — alerts, triage, scoping
3. **Containment, Eradication & Recovery** — isolate, remove, restore
4. **Post-Incident Activity** — lessons learned, reporting

## 📖 Playbook — Ransomware Detected

### Phase 1: Detection & Analysis
- [ ] Confirm alert from SIEM / EDR (encrypted files, ransom note, mass file changes)
- [ ] Identify affected hosts, users, and data
- [ ] Determine ransomware variant and initial access vector (e.g., phishing)
- [ ] Assign severity and open an incident ticket

### Phase 2: Containment
- [ ] **Isolate** infected hosts from the network (disable NIC / quarantine in EDR)
- [ ] Disable compromised accounts
- [ ] Block malicious IPs/domains at the firewall
- [ ] Preserve evidence (memory, disk images, logs)

### Phase 3: Eradication & Recovery
- [ ] Remove malware and persistence mechanisms
- [ ] Patch the exploited vulnerability
- [ ] Restore data from clean backups
- [ ] Verify systems are clean before reconnecting

### Phase 4: Post-Incident
- [ ] Conduct a lessons-learned review
- [ ] Update detection rules and controls
- [ ] Document timeline and impact in the final report

## 🚨 Escalation Matrix
| Severity | Escalate to | SLA |
|---|---|---|
| Low | Tier 1 analyst | 24h |
| Medium | Tier 2 / SOC lead | 4h |
| High/Critical | CISO + IR team | Immediate |

## 🧾 Outcome
A reusable, checklist-driven playbook that reduces mean-time-to-respond (MTTR) and ensures
consistent, defensible handling of incidents.
