# Incident Handler's Journal (Final)

## Project description

This is my completed incident handler's journal from the Detection and Response course of
the Google Cybersecurity Certificate. Throughout the course I used the journal to document
security incidents and to practice with the tools an analyst relies on day to day. It holds
four dated and numbered entries. Two of them investigate an incident using the 5 W's, and
two of them describe the use and purpose of a cybersecurity tool. Where it helps, I have
noted which phase of the NIST Incident Response Lifecycle the work falls under. The four
phases are Preparation, Detection and Analysis, Containment Eradication and Recovery, and
Post-Incident Activity.

## Entry 1

**Date:** July 20, 2026

**Entry:** 1

**Description:** Documented a ransomware incident at a small health care clinic that began
with a phishing email carrying a malicious attachment. Opening the file encrypted patient
records and shut down operations. This work sits in the Detection and Analysis phase of the
NIST lifecycle, since it is about understanding the nature and scope of the incident.

**Tool(s) used:** None for this entry. In a live response I would use a SIEM to review logs
and endpoint detection and response software to trace the malware.

### The 5 W's

- **Who:** An organized group of attackers known for targeting health care and transportation
  organizations ran the phishing campaign and deployed the ransomware.
- **What:** An employee opened a phishing attachment, which installed malware and encrypted
  critical files, and a ransom note demanded payment for the decryption key.
- **When:** On a Tuesday at approximately 9:00 a.m., when staff arrived and could not access
  their computers or files.
- **Where:** On the employee workstations and file systems of a small primary care health
  care clinic in the United States.
- **Why:** The attackers used targeted phishing to trick employees into running the malware,
  taking advantage of the human element.

**Additional notes:** I would want to know whether offline backups exist, whether the malware
spread beyond the first machine, and whether patient data was stolen before it was encrypted.

## Entry 2

**Date:** July 22, 2026

**Entry:** 2

**Description:** Investigated a suspicious file downloaded on an employee computer after a
phishing alert at a financial services company. I took the file's SHA256 hash and analyzed it
in VirusTotal to confirm it was malicious and to gather related indicators of compromise. This
falls under the Detection and Analysis phase, since it is about identifying and confirming a
threat.

**Tool(s) used:** VirusTotal. VirusTotal is a service that analyzes files, domains, URLs, and
IP addresses against many security vendors and community threat intelligence. I searched the
SHA256 hash, reviewed the vendors' ratio, the community score, and the Detection, Details,
Relations, and Behavior tabs to confirm the verdict and collect other indicators.

### The 5 W's

- **Who:** An external attacker using the Flagpro malware family, which is tied to a known
  threat actor.
- **What:** An employee opened a malicious password protected spreadsheet, which executed a
  payload and created unauthorized executable files on the computer.
- **When:** During the alert window, starting when the file was opened at 1:13 p.m. and
  ending when the intrusion detection system alerted the SOC at 1:20 p.m.
- **Where:** On an employee workstation inside a financial services company's network.
- **Why:** A phishing email delivered the file, and the employee opened it, which let the
  malware run.

**Additional notes:** VirusTotal reports can also list legitimate domains and IP addresses, so
I confirmed the malicious command and control domain rather than treating every contacted
address as an indicator.

## Entry 3

**Date:** July 24, 2026

**Entry:** 3

**Description:** Practiced capturing and analyzing network traffic with two packet sniffers,
Wireshark and tcpdump, to understand how analysts read the flows moving across a network. This
sits in the Detection and Analysis phase, and also in Preparation, since building tool skills
before an incident is part of being ready.

**Tool(s) used:** Wireshark and tcpdump. Wireshark is a graphical protocol analyzer that shows
captured packets in color coded lists and expandable protocol trees, which is strong for deep
visual inspection. tcpdump is a command line sniffer that captures traffic quickly on servers
and remote systems where no graphical tool is available. Both are free and open source, both
save to the pcap format, and both support filtering to narrow a capture to what matters.

**Additional notes:** Capturing with tcpdump on a remote host and then opening the file in
Wireshark is a common workflow that uses the strengths of each tool together.

## Entry 4

**Date:** July 26, 2026

**Entry:** 4

**Description:** Explored network and host based signatures and logs using Suricata to see how
an intrusion detection system inspects traffic and generates alerts. This falls under the
Detection and Analysis phase, since signatures and log review are how analysts detect and
investigate suspicious activity.

**Tool(s) used:** Suricata. Suricata is an open source intrusion detection and prevention
system that inspects network traffic against a set of rules, or signatures, and produces alerts
and log entries when traffic matches. I reviewed how a rule is written, ran it against sample
traffic, and read the resulting alert and event logs to connect a signature to the activity it
was catching.

**Additional notes:** Reading Suricata output alongside the earlier packet captures made it
clearer how raw traffic becomes an actionable alert for a SOC analyst.

## Reflections and Notes

**Were there any specific activities that were challenging for you? Why or why not?** The most
challenging activity was investigating the suspicious file hash in VirusTotal. There was a large
amount of information across the tabs, and learning to separate genuine indicators of compromise
from legitimate contacted addresses took real care and patience before I trusted my conclusion.

**Has your understanding of incident detection and response changed since taking this course?**
Yes, a great deal. I used to think of an incident as a single event, but I now see it as a
lifecycle that runs from preparation through detection, containment, and post incident review.
Documentation and playbooks now feel just as important to me as the technical response itself.

**Was there a specific tool or concept that you enjoyed the most? Why?** I enjoyed working with
VirusTotal and the Pyramid of Pain the most. Turning a single file hash into a full picture of a
threat, and then understanding why some indicators cause an attacker more pain than others, made
the value of good threat intelligence click for me in a way that stuck.

## Summary

This finalized incident handler's journal brings together the incidents I investigated and the
tools I practiced with across the course. Two entries walk through incidents using the 5 W's, a
health care ransomware attack and a malicious file investigation, and two entries document the
tools I used, Wireshark and tcpdump for packet analysis and Suricata for signature based
detection. Keeping this running record made each activity easier to recall and gave me a clear
view of how detection and response fit together as a lifecycle rather than a single moment.
