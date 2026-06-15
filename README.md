# Network Reconnaissance Labs

Documenting my journey learning network reconnaissance, port scanning, service detection, traffic analysis, and firewall evasion.

## Tools & Techniques

### Nmap
- [Basic Scan](nmap/basic-scan.md) - Top 1000 ports
- [Service Detection](nmap/service-detection.md) - Version fingerprinting
- [Full Port Scan](nmap/full-port-scan.md) - All 65,535 ports
- [Firewall Evasion](nmap/firewall-evasion.md) - Filtered ports analysis 

### Wireshark
- [TCP Handshake](wireshark/tcp-handshake.md) - Three-way handshake analysis
- [HTTP Traffic](wireshark/http-analysis.md) - Web request inspection

### Netdiscover
- [Host Discovery](netdiscover/host-discovery.md) - ARP-based scanning

## Target Environment
| Component | Details |
|-----------|---------|
| Attacker | Kali Linux (VMware) |
| Targets | Metasploitable 2, Metasploitable 3 |
| Network | VMware NAT / Host-Only |

## Progress
- [x] Basic Nmap scan
- [x] Service detection
- [x] Full port scan
- [x] Firewall evasion
- [ ] Wireshark analysis
- [ ] Netdiscover

## Why This Matters
Understanding network reconnaissance is the first step in any penetration test. These labs document my ability to discover hosts, identify services, and analyze network traffic — foundational skills for red teaming and security assessments.
