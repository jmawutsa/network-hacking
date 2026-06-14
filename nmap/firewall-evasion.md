# Nmap Firewall Evasion

**Date:** 2026-06-14
**Target:** Firewall-protected host
**Scenario:** Standard scan shows all ports filtered

## The Problem

Standard TCP scan:
nmap -sS 192.168.1.100

Result: All 1000 scanned ports are filtered — firewall is dropping packets.

## Evasion Techniques

### 1. Bypass Ping (Host Discovery)

nmap -Pn 192.168.1.100

Skips ICMP ping. Firewall may block ping but allow port scans.

### 2. Fragment Packets

nmap -f 192.168.1.100

Splits probes into tiny fragments. Some firewalls don't reassemble correctly.

### 3. Source Port Manipulation

nmap --source-port 53 192.168.1.100

Makes scan appear as DNS traffic (port 53). Firewalls often trust DNS.

### 4. Decoy Scans

nmap -D RND:10,ME 192.168.1.100

Hides your real IP among fake decoys. Harder to block.

### 5. Timing Template (Slow Down)

nmap -T1 192.168.1.100

Very slow. Triggers less alarm on IDS/IPS.

## Combined Command

nmap -Pn -f --source-port 53 -D RND:5,ME -T2 -p 80,443 192.168.1.100

Flags:
-Pn = skip ping
-f = fragment packets
--source-port 53 = appear as DNS
-D = decoy IPs
-T2 = polite timing

## What I Learned

- Filtered does not mean dead host — firewall is protecting something
- Evasion is about looking legitimate, not being invisible
- Multiple techniques together work better than one
- Modern firewalls detect most evasion
- Sometimes you cannot bypass; pivot to web or client-side attacks

## When Evasion Fails

If all ports stay filtered:
- Target is well-hardened
- Switch to web application testing (port 80/443 may still be open)
- Consider social engineering or client-side attacks

## Remediation

To prevent this evasion:
- Use stateful inspection firewalls
- Implement rate limiting
- Deploy IDS/IPS with fragment reassembly
- Block unusual source ports
