# Project 10: Incident Report Analysis Using the NIST CSF

Skills: NIST Cybersecurity Framework, network security, DoS analysis, incident documentation, firewall and IDS/IPS controls.

## Scenario

I work as a cybersecurity analyst at a multimedia company that provides web design, graphic design, and social media marketing services to small businesses. The company recently experienced a denial of service attack that took the internal network offline for about two hours before the incident management team resolved it. During the attack the network services stopped responding because of an incoming flood of ICMP packets, and normal internal traffic could not reach any network resources. The response team blocked incoming ICMP packets, took non critical services offline, and restored the critical services.

After the network was stable, the security team investigated and found that a malicious actor had sent a flood of ICMP pings into the network through a firewall that had not been configured correctly. That gap let the attacker overwhelm the network and cause the outage. I used the NIST Cybersecurity Framework to document the event and to build a plan for reducing the risk of it happening again.

## Incident Summary

| Field | Detail |
|---|---|
| Incident ID | IR-2024-031 |
| Type | Network denial of service, ICMP flood |
| Cause | Misconfigured firewall that allowed unrestricted inbound ICMP traffic |
| Attack source | External malicious actor using spoofed source IP addresses |
| Detected | Sudden loss of network service availability reported across the internal network |
| Duration | Roughly two hours from onset to recovery |
| Severity | High |
| Affected assets | Internal network, perimeter firewall, and the internal servers and services that host company resources |
| Impact | Internal users lost access to network resources for the length of the outage, which interrupted client work and internal operations |

## Identify

The attack was a denial of service carried out through an ICMP flood, sometimes called a ping flood. The attacker sent a very high volume of ICMP echo request packets toward the network faster than the systems could process them, which exhausted resources and denied service to legitimate users.

The perimeter firewall was the entry point because it was not configured to limit or filter inbound ICMP traffic. From there the flood affected the internal network and the servers and services that employees rely on to do their work. The business processes that were interrupted were the day to day operations that depend on network access, including web design, graphic design, and social media marketing work for clients. The people who need access to the affected systems are the internal staff who use these network resources and the IT and security team who manage and defend them.

## Protect

The most important fix is the firewall itself, since the misconfiguration is what let the attack succeed. The security team added a firewall rule to limit the rate of incoming ICMP packets so that a sudden flood no longer overwhelms the network. They also enabled source IP address verification on the firewall to check for spoofed addresses on inbound ICMP traffic, which makes this style of attack harder to carry out.

Beyond the firewall, access to the affected systems should be limited to trusted internal users and administrators, and non trusted external sources should be blocked from reaching internal services. The IT and security teams and company leadership need to be made aware of the incident and the steps taken to prevent it. Firewall firmware and the operating systems and software on the affected devices should be reviewed and updated so that known weaknesses are closed. As a longer term protective measure, the team deployed an intrusion detection and prevention system to filter suspicious ICMP traffic, which adds another layer of defense in front of the internal network.

## Detect

Continuous monitoring of network traffic is what would have surfaced this attack sooner, so the team added network monitoring software that watches for abnormal traffic patterns such as a spike in inbound ICMP packets from untrusted or spoofed addresses. A security information and event management tool would help by collecting logs from the firewall and other devices and alerting the security staff when it sees anomalies or a threshold is crossed.

The intrusion detection and prevention system also serves a detection role by inspecting traffic for the characteristics of an ICMP flood and flagging or filtering it. Together these tools let the team track normal versus abnormal traffic volume, separate authorized from unauthorized sources, and detect unusual activity early enough to act before service is lost.

## Respond

For future incidents the team needs a clear and repeatable response plan. To contain an event, the team can block the offending traffic at the firewall and isolate or take offline the affected devices and non critical services so the damage does not spread, which is the same containment approach that worked during this incident. To neutralize the threat, the team can apply firewall rules that drop the malicious traffic, verify source addresses, and rely on the intrusion prevention system to filter suspicious ICMP packets.

Firewall logs, network monitoring data, and IDS and IPS alerts provide the information needed to analyze what happened, where it came from, and how it moved through the network. The response procedures should be communicated to the security team, IT staff, and affected end users so that everyone understands their role and knows the status of the event. After each incident the team should review what worked and update the response plan so that mitigation is faster and more effective the next time.

## Recover

Recovery focuses on returning the affected systems to normal operation. The information needed to recover quickly includes an up to date inventory of the affected systems, current backups of system data and configurations, and documented recovery procedures. In this incident the team restored the critical network services first and then brought the non critical services back online once the network was stable and the malicious traffic was blocked.

Going forward, the recovery process can be improved by keeping tested backups and a known good baseline for critical systems, by confirming that services are healthy before reconnecting them, and by reviewing the recovery steps after each event to remove delays. Restoration status should be communicated to the security team, IT staff, and end users so that everyone knows when resources are available again.

## Lessons Learned

1. Review and correctly configure firewall rules so that inbound ICMP and other unnecessary traffic is rate limited or filtered by default.
2. Enable source IP verification to reduce the effectiveness of spoofed traffic.
3. Keep continuous network monitoring and a SIEM in place so that floods and anomalies are detected early.
4. Maintain an IDS and IPS in front of the internal network to filter suspicious traffic automatically.
5. Keep tested backups and a documented, practiced response and recovery plan so that outages are shorter.

## Outcome

I produced a framework aligned incident report that summarizes the denial of service event, identifies the attack type and the systems it affected, and lays out protection, detection, response, and recovery plans. The analysis turns a single incident into concrete improvements that lower the chance of a repeat and shorten the recovery time if a similar attack happens again.
