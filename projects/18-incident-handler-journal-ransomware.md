# Incident Handler's Journal: Health Care Clinic Ransomware

## Project description

This is my first entry in an incident handler's journal, which is the running record I
keep while working through security incident scenarios. In this scenario a small U.S.
health care clinic was hit with ransomware that started from a phishing email, and the
journal captures the facts of the incident in a structured way so the details are easy to
recall later. I documented the entry using the date, an entry number, a description, the
tools involved, the five W's of the incident, and a set of additional notes.

## Journal entry

**Date:** July 26, 2026

**Entry:** 1

**Description:** A small U.S. health care clinic experienced a ransomware attack that
began with a phishing email carrying a malicious attachment. Once the attachment was
opened, malware installed on employee machines and ransomware encrypted critical files,
including patient medical records. Business operations shut down because staff could no
longer reach the files and software they needed, and a ransom note demanded payment in
exchange for the decryption key.

**Tool(s) used:** None. This entry documents the reported details of the incident rather
than a hands-on analysis. In a real response I would expect to use tools such as a SIEM
to review logs, an email security gateway to trace the phishing message, and antivirus or
endpoint detection and response software to identify and contain the malware.

### The 5 W's

**Who caused the incident?** An organized group of unethical hackers known for targeting
organizations in the health care and transportation industries. They ran the phishing
campaign and deployed the ransomware.

**What happened?** Employees opened a phishing email with a malicious attachment, which
installed malware and let the attackers deploy ransomware. The ransomware encrypted
critical files, a ransom note appeared demanding payment for the decryption key, and the
clinic had to shut down its systems, so business operations stopped.

**When did the incident occur?** On a Tuesday morning at approximately 9:00 a.m., when
employees arrived and found they could not access their computers or files.

**Where did the incident happen?** At a small primary-care health care clinic in the
United States, across the employee computers and file systems that make up the clinic's
internal network.

**Why did the incident happen?** The attackers gained access through targeted phishing
emails that tricked employees into downloading a malicious attachment. The underlying
cause was the human element combined with a lack of safeguards that would have caught the
email or stopped the attachment from running.

### Additional notes

The scenario shows how one phishing email can escalate into a full operational shutdown,
which is especially serious for a clinic where locked patient records can affect care.
A few questions I would want answered are whether the clinic kept offline backups that
would let them restore files without paying the ransom, whether the malware spread beyond
the machines that opened the attachment, and whether any patient data was stolen before
the files were encrypted, since that would turn this into a breach with reporting
obligations. It also reinforces how valuable phishing awareness training and email
filtering are as early defenses.

## Summary

This first journal entry records a ransomware incident at a small health care clinic that
started with a phishing email and ended with encrypted patient files and a full shutdown
of operations. Laying it out with the date, entry number, description, tools, and the five
W's keeps the facts organized and makes the entry a useful reference for later incidents.
The scenario is a clear reminder that people and email are common entry points, and that
backups, training, and email security are some of the most effective controls against
this kind of attack.
