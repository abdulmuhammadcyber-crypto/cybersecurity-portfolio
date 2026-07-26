# Applying a Phishing Playbook to Resolve an Alert Ticket

## Project description

As a level one SOC analyst at a financial services company, I worked a phishing alert
tied to the malicious file I had already verified in the previous activity. A playbook
lays out the step-by-step actions for responding to a specific type of incident, which
keeps the response fast and consistent and helps limit the damage. Here I followed the
organization's phishing playbook and flowchart to evaluate the alert, confirm the email
carried a malicious attachment, and then update the alert ticket with the correct status
and a clear explanation of what I found.

## Investigation using the playbook

Following the playbook, I first set the ticket status to Investigating and opened a new
entry in my incident handler's journal to record my findings. I then moved to the Evaluate
the alert step and reviewed the ticket details, including the sender information, the
subject line and message body, and the attachment.

Several details pointed to a real phishing attempt rather than a false alarm:

- The email carried a file attachment, and that attachment's SHA256 hash had already been
  verified as malicious in the previous VirusTotal investigation, identified as the Flagpro
  malware family associated with a known threat actor.
- The sender details did not line up with a trusted internal source, which is a common sign
  of an impersonation attempt.
- Opening the attachment led directly to unauthorized executable files being created on the
  employee's machine, which an intrusion detection system then flagged. Legitimate email
  does not behave this way.

### The 5 W's of the incident

**Who caused the incident?** An external attacker running a phishing campaign, using the
malicious attachment tied to the Flagpro malware family.

**What happened?** An employee received a phishing email with a malicious attachment, opened
it, and the payload executed and created unauthorized executable files on the computer.

**When did the incident take place?** During the reported alert window, beginning when the
employee received and opened the email and ending when the intrusion detection system raised
the alert to the SOC.

**Where did the incident occur?** On the employee's workstation inside the financial services
company's network.

**Why did it happen?** The attacker used a phishing email with a malicious attachment to
trick the employee into executing malware, taking advantage of the human element.

## Playbook decision

Working through Step 3.0 and Step 3.1 of the playbook, I confirmed the email contains an
attachment and that the attachment is malicious, since its file hash was already verified.
Because a verified malicious attachment executed on a company device, the flowchart directs
the analyst to escalate rather than close, so I proceeded to the escalation path.

## Alert ticket update

**Ticket status:** Escalated

**Ticket comments:** A phishing email delivered a malicious attachment to an employee, who
downloaded and opened it, which executed a payload and created unauthorized executable files
on the workstation. I am escalating this ticket for three reasons. First, the attachment's
SHA256 hash was already verified as malicious and identified as the Flagpro malware family,
so this is a confirmed threat and not a false positive. Second, the malware executed
successfully and created unauthorized files on a company device, meaning the endpoint is
compromised and needs containment and remediation beyond a level one analyst. Third, the
company is in financial services and the Flagpro family is tied to a targeted threat actor,
so the potential impact to sensitive data justifies escalating to the incident response team
for a deeper investigation.

## Summary

Using the phishing playbook kept the response structured and defensible. I evaluated the
alert, answered the 5 W's, and confirmed through the earlier hash analysis that the email
carried a verified malicious attachment that ran on the employee's machine. Following the
flowchart, the right action was to escalate the ticket rather than close it, because a
confirmed compromise on a company device at a financial services firm needs a full incident
response. The playbook made the decision clear and gave me solid, evidence-based reasons to
support it.
