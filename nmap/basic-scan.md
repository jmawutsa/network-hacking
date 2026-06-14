# Nmap Basic Scan

**Date:** 2026-06-14
**Target:** Metasploitable 2
**Command:** `nmap 192.168.9.2`

## Results
| Port | State | Service |
|------|-------|---------|
| 21/tcp | open | ftp |
| 22/tcp | open | ssh |
| 23/tcp | open | telnet |
| 80/tcp | open | http |

## What I Learned
- Nmap scans the top 1000 ports by default
- Telnet (port 23) is insecure
