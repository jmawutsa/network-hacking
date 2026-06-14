# Nmap Firewall Evasion

**Date:** 2026-06-14
**Target:** Metasploitable 3 (Windows VM)
**IP:** 192.168.9.3
**Firewall:** Windows Defender Firewall (enabled by default)
**Scenario:** Standard scan shows filtered ports

## The Problem

Standard TCP scan:
nmap -sS 192.168.9.3

Result: Many ports show filtered — firewall is dropping packets without response.

## Evasion Techniques Tested

### 1. Bypass Ping (Host Discovery)

nmap -Pn 192.168.9.3

Skips ICMP ping. Firewall may block ping but allow port scans.

### 2. Fragment Packets

nmap -f 192.168.9.3

Splits probes into tiny fragments. Some firewalls don't reassemble correctly.

### 3. Source Port Manipulation

nmap --source-port 53 192.168.9.3

Makes scan appear as DNS traffic (port 53). Firewalls often trust DNS.

### 4. Decoy Scans

nmap -D RND:10,ME 192.168.9.3

Hides your real IP among fake decoys. Harder to block.

### 5. Timing Template (Slow Down)

nmap -T1 192.168.9.3

Very slow. Triggers less alarm on IDS/IPS.

## Combined Command

nmap -Pn -f --source-port 53 -D RND:5,ME -T2 -p 80,443 192.168.9.3

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
- Modern firewalls (like Windows Defender) detect many evasion attempts
- Sometimes you cannot bypass; pivot to web or client-side attacks

## When Evasion Fails

If all ports stay filtered after evasion attempts:
- Target is well-hardened
- Switch to web application testing (port 80/443 may still be open)
- Consider social engineering or client-side attacks
- In a real pentest, move to a different attack vector

## Remediation (Defender's View)

To prevent this evasion:
- Use stateful inspection firewalls
- Implement rate limiting
- Deploy IDS/IPS with fragment reassembly
- Block unusual source ports
- Keep firewall rules up to date
- Don't rely on security through obscurity
