# Project 3: Network Traffic Analysis

Skills: TCP/IP, Wireshark, tcpdump, packet inspection, protocol analysis.

## Scenario

A web server became unreachable and users received a connection timed out error. I analyzed captured network traffic to identify the root cause.

## Tools

- Wireshark for graphical packet capture and analysis
- tcpdump for command-line packet capture

## Investigation

### Symptoms

- HTTP requests to the web server received no response
- Users experienced repeated connection timeouts

### Packet Analysis Findings

Reviewing the capture, I observed an abnormally high volume of TCP SYN packets arriving from many source IP addresses, with no completed three-way handshakes (no SYN-ACK followed by ACK).

```
# Filter used in tcpdump
sudo tcpdump -i eth0 'tcp[tcpflags] & tcp-syn != 0' -n

# Wireshark display filters
tcp.flags.syn == 1 && tcp.flags.ack == 0     # incoming SYN flood
tcp.analysis.retransmission                  # server struggling to respond
```

### Root Cause

The server was the target of a SYN flood denial-of-service attack. The connection table filled with half-open connections, exhausting server resources so legitimate users could not connect.

## Recommendations

1. Enable SYN cookies on the server.
2. Deploy rate limiting or a firewall rule to drop excessive SYN packets from single sources.
3. Use a DDoS mitigation or upstream scrubbing service.
4. Add IDS signatures to alert on SYN flood patterns.

## Outcome

I identified a network-layer denial-of-service condition through packet analysis and recommended layered mitigations to restore and protect availability, the availability component of the CIA triad.
