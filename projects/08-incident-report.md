# Project 8 — Incident Report: Phishing → Malware

**Skills:** NIST CSF · Incident documentation · Root-cause analysis · Lessons learned

## 📌 Scenario
An employee reported that their workstation was behaving strangely after opening an email
attachment. I documented the incident using the **NIST Cybersecurity Framework** functions.

## 🗂️ Incident Summary
| Field | Detail |
|---|---|
| Incident ID | IR-2024-014 |
| Type | Phishing leading to malware infection |
| Detected | EDR alert + user report |
| Severity | High |
| Affected asset | Employee workstation, mapped network drive |

## 🔄 NIST CSF Breakdown

### Identify
- Initial access: **phishing email** with a malicious macro-enabled document.
- Impacted assets: one endpoint, potential lateral movement to a file share.

### Protect
- Existing controls: antivirus, email filtering (bypassed by the crafted attachment).
- Gap: macros were **not disabled** by policy; no MFA on the file share.

### Detect
- EDR flagged an unusual child process (`winword.exe → powershell.exe`).
- Outbound connection to a suspicious external IP observed in firewall logs.

### Respond
- Isolated the workstation from the network.
- Reset the user's credentials; blocked the malicious IP/domain.
- Collected forensic artifacts (memory, logs) for analysis.

### Recover
- Reimaged the workstation from a clean baseline.
- Restored files from backup; verified integrity before reconnecting.

## 📝 Lessons Learned
1. **Disable Office macros** via group policy across the fleet.
2. Enhance **phishing awareness training**.
3. Add **MFA** to sensitive file shares.
4. Tune EDR rules for `office-app → script-interpreter` chains.

## 🧾 Outcome
Produced a clear, framework-aligned incident report that both records the response and drives
concrete control improvements to prevent recurrence.
