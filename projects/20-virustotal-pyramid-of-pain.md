# Analyzing a Suspicious File with VirusTotal and the Pyramid of Pain

## Project description

As a level one SOC analyst at a financial services company, I received an alert about a
suspicious file downloaded on an employee's computer. The employee had opened a
password-protected spreadsheet delivered by email, and opening it executed a malicious
payload that dropped several unauthorized executables. I took the SHA256 hash of the file
and ran it through VirusTotal, then used the Pyramid of Pain to record the indicators of
compromise tied to the file. The Pyramid of Pain ranks indicators by how much difficulty
they cause an attacker when defenders block them, from easy to change hash values at the
bottom up to tactics, techniques, and procedures at the top.

## Alert details

The artifact under investigation is the file with this SHA256 hash:

```
54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b
```

Timeline of the event:

- 1:11 p.m. An employee receives an email with a file attachment.
- 1:13 p.m. The employee downloads and opens the file.
- 1:15 p.m. Multiple unauthorized executable files are created on the computer.
- 1:20 p.m. An intrusion detection system flags the executables and alerts the SOC.

## Is the file malicious?

Yes, the file is malicious. The VirusTotal report shows a strong and consistent verdict
across all three of the sections used to judge a file. The vendors' ratio is high, with a
large majority of security vendors flagging the file as malicious rather than clean. The
community score is negative, meaning the VirusTotal community also assessed the file as
harmful. In the security vendors' analysis under the Detection tab, multiple vendors do not
just flag the file, they name it, identifying it as the Flagpro malware family, which is
associated with the BlackTech threat actor known for targeting organizations through
spearphishing. A high vendor ratio, a negative community score, and named malware
detections all pointing the same direction is a reliable sign that the file is malicious.

## Indicators of compromise

I recorded three different types of IoCs from the report, moving up the Pyramid of Pain.

**Hash value (bottom of the pyramid).** In addition to the SHA256 artifact above, the
Details tab lists other hashes that fingerprint the same file. The MD5 hash is:

```
287d612e29b71c90aa54947313810a25
```

Hashes are the easiest indicator for an attacker to change, since altering a single byte
produces a completely new hash, so blocking a hash only stops that exact file.

**Domain name (middle of the pyramid).** Under the Relations tab, the file is tied to the
command and control domain:

```
org.misecure.com
```

The misecure.com domain is a documented Flagpro command and control destination. Domains
cause an attacker more pain than hashes because registering and standing up new malicious
domains takes more effort than recompiling a file.

**Tactics, techniques, and procedures (top of the pyramid).** The Behavior tab maps the
file's sandbox activity to MITRE ATT&CK. Techniques observed for this malware include:

- T1566.001 Phishing: Spearphishing Attachment (initial access, matching how the file
  arrived by email)
- T1204.002 User Execution: Malicious File (the employee opening the attachment)
- T1547.001 Boot or Logon Autostart Execution: Registry Run Keys or Startup Folder
  (persistence)
- T1071.001 Application Layer Protocol: Web Protocols (command and control over the web)
- T1041 Exfiltration Over C2 Channel (stealing data back through the same channel)

TTPs sit at the top of the pyramid because they describe how the attacker behaves rather
than what tool or file they used. Forcing an adversary to change their entire way of
operating causes the most pain of any indicator.

## Additional notes

The timeline lines up cleanly with the behavior VirusTotal reports. The spearphishing
attachment and user execution match the 1:11 to 1:13 window, the unauthorized executables
created at 1:15 match ingress tool transfer and persistence, and the mapped web-protocol
C2 explains what the malware would reach out to next. One thing to keep in mind is that
VirusTotal reports also contain legitimate domains and IP addresses, so not every contacted
address is an IoC. For example, a contacted content-delivery IP can be benign, which is why
I chose the documented C2 domain over a generic contacted IP. In a real investigation I
would confirm these findings with additional tools rather than relying on VirusTotal alone.

## Summary

Running the SHA256 hash through VirusTotal confirmed the file is malicious, backed by a
high vendor ratio, a negative community score, and detections naming it as Flagpro, a
family tied to the BlackTech threat actor. Using the Pyramid of Pain I captured three
different types of indicators: an MD5 hash value at the bottom, the misecure.com command
and control domain in the middle, and a set of MITRE ATT&CK techniques at the top. Reading
them from the bottom up shows why blocking higher-level indicators, especially an
attacker's TTPs, causes far more disruption than blocking a single file hash.

> Verify before submitting: I pulled the malware family, MD5, domain, and TTPs from the
> live VirusTotal report and public MITRE ATT&CK and threat-intelligence sources. Because
> VirusTotal updates over time, open the report on the SHA256 hash yourself and confirm the
> MD5 on the Details tab and the domain on the Relations tab still match before you turn
> this in as your own investigation.
