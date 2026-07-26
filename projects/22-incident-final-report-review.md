# Reviewing an Incident Final Report

## Project description

As a new level one SOC analyst at a midsized retail company, I spent part of my first week
reviewing the final report from a major data breach that happened before I joined. The
company runs both physical stores and an ecommerce operation that brings in about 80 percent
of sales, and the breach exposed the records of more than one million users. A final report
belongs to the post incident phase of the NIST Incident Response Lifecycle, and it gives a
complete review of what happened along with recommendations to stop it from happening again.
My review had four goals, which were to identify what happened, when it happened, what
response actions the company took, and what future recommendations came out of it.

## Goal 1: What happened

The organization was hit by a data theft incident. An attacker found a vulnerability in the
ecommerce web application and used forced browsing to reach files and directories that should
have been restricted. Forced browsing means the attacker manually changed the web address to
navigate to resources that were never meant to be publicly reachable, and because access
controls were missing, that took them straight to sensitive customer data. The result was a
breach affecting more than one million users.

## Goal 2: When it happened

The breach took place before I joined the company, and the report lays out the full sequence
in its timeline section. The timeline records when the attacker first gained access, when the
data was taken, and when the company detected and responded to the incident, so a reader can
follow the incident from start to finish in order.

## Goal 3: Response actions the company took

The report describes how the company worked through the incident once it was detected. The
security team investigated the activity, traced how the attacker got in, and documented the
root cause in the investigation section of the report. The company then contained the problem,
closed off the exploited weakness in the ecommerce application, and provided identity
protection services to the customers whose data was exposed so the people affected had some
protection against follow on fraud.

## Goal 4: Future recommendations

The report closes with the changes the company put in place so the same breach cannot happen
again. Two recommendations stand out. The first was to implement access control mechanisms, so
that users and requests can only reach the resources they are authorized for, which directly
shuts down the forced browsing path the attacker used. The second was to implement routine
vulnerability scans, so that weaknesses in the ecommerce application and the rest of the
environment are found and fixed on a regular schedule instead of being discovered by an
attacker. The company did not simply pay the attacker, and paying a ransom is not a fix,
because it does nothing to close the underlying weakness.

## Report review answers

Reading the report against the four goals, the key facts line up as follows. The incident was
data theft. The root cause is explained in the investigation section of the report. The
attacker exploited the ecommerce web application using forced browsing. The two recommendations
the company implemented were access control mechanisms and routine vulnerability scans.

## Summary

The final report turned a past breach into a clear lesson. A gap in access control on the
ecommerce web application let an attacker use forced browsing to steal the data of more than
one million customers. The report captured what happened, laid out the timeline, documented the
investigation and root cause, and recorded the response the company gave to affected customers.
Most valuable of all, it produced concrete recommendations, access controls and routine
vulnerability scanning, that close the exact gap the attacker used and lower the chance of a
repeat. Reviewing a report like this is a strong reminder of why the post incident phase matters
just as much as the response itself.
