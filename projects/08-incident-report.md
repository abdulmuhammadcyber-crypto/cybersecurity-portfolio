# Project 8 — Incident Report: Phishing Leading to Malware

Skills: NIST CSF, incident documentation, root-cause analysis, lessons learned.

## Scenario

An employee reported that their workstation was behaving strangely after opening an email attachment. I documented the incident using the NIST Cybersecurity Framework functions.

## Incident Summary

| Field | Detail |
|---|---|
| Incident ID | IR-2024-014 |
| Type | Phishing leading to malware infection |
| Detected | EDR alert and user report |
| Severity | High |
| Affected asset | Employee workstation and a mapped network drive |

## NIST CSF Breakdown

### Identify

- Initial access came from a phishing email with a malicious macro-enabled document.
- Impacted assets were one endpoint with potential lateral movement to a file share.

### Protect

- Existing controls included antivirus and email filtering, which were bypassed by the crafted attachment.
- The gap was that macros were not disabled by policy and there was no MFA on the file share.

### Detect

- EDR flagged an unusual child process (winword.exe spawning powershell.exe).
- An outbound connection to a suspicious external IP address was observed in the firewall logs.

### Respond

- Isolated the workstation from the network.
- Reset the user's credentials and blocked the malicious IP address and domain.
- Collected forensic artifacts, including memory and logs, for analysis.

### Recover

- Reimaged the workstation from a clean baseline.
- Restored files from backup and verified integrity before reconnecting.

## Lessons Learned

1. Disable Office macros through group policy across the fleet.
2. Enhance phishing awareness training.
3. Add MFA to sensitive file shares.
4. Tune EDR rules to detect office applications spawning script interpreters.

## Outcome

I produced a clear, framework-aligned incident report that records the response and drives concrete control improvements to prevent recurrence.
