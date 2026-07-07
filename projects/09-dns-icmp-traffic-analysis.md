# Cybersecurity Incident Report: Network Traffic Analysis

Skills used: TCP/IP model, DNS, ICMP, tcpdump, packet analysis.

## Part 1: Summary of the problem found in the DNS and ICMP traffic log

The UDP protocol reveals that my computer sent DNS requests over UDP to the DNS server at 203.0.113.2 on port 53 to get the IP address for www.yummyrecipesforme.com, but those requests were never delivered to a working service.

This is based on the results of the network analysis, which show that the ICMP reply returned the error message: "udp port 53 unreachable."

The port noted in the error message is port 53, which is used for DNS. DNS is the service that resolves a domain name into an IP address.

The most likely issue is that the DNS server had no service listening on port 53, so the UDP requests could not be delivered and the domain name never resolved to an IP address. Because of that, the browser could not reach the website.

## Part 2: Analysis of the data and a likely cause of the incident

Time incident occurred: 13:24:32, which is 1:24 p.m., taken from the timestamp on the first packet in the tcpdump log.

How the IT team became aware of the incident: customers of our clients reported that they could not reach www.yummyrecipesforme.com and were seeing a "destination port unreachable" error after the page failed to load.

Actions taken by the IT department to investigate the incident: I tried to load the website myself and received the same "destination port unreachable" error. I then opened the tcpdump network analyzer and reloaded the page so I could capture the traffic and see what was actually happening on the wire.

Key findings of the investigation: the log shows a DNS request going out over UDP from my computer at 192.51.100.15 to the DNS server at 203.0.113.2 on port 53. Instead of a DNS answer, the server returned ICMP packets carrying the message "udp port 53 unreachable." This same error came back three times in a row. Since port 53 is the port used for DNS, the request never reached a working DNS service, so the name could not be resolved and the HTTPS request to the web server was never sent.

Likely cause of the incident: the DNS service on the server was down or was not listening on port 53. This could be caused by the service crashing, a bad configuration, a firewall blocking the port, or a denial of service condition. With nothing answering on port 53, every DNS request came back as an ICMP port unreachable error, which explains why the website could not be reached.
