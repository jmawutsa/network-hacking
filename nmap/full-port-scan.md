# Nmap Full Port Scan

**Date:** 2026-06-14
**Target:** Metasploitable 2
**Command:** `nmap -p- 192.168.9.2`

## Results (Interesting Ports)
| Port | Service |
|------|---------|
| 1524/tcp | bindshell |
| 2121/tcp | ftp |
| 3306/tcp | mysql |
| 5432/tcp | postgresql |
| 5900/tcp | vnc |
| 6667/tcp | irc |

## What I Learned
- Many services run on non-standard ports
- Port 1524 (Ingreslock) gives a root shell with `nc`
- Scanning all 65,535 ports takes 2-5 minutes
- Don't skip this — hidden services are often the easiest targets

## Next Steps
Connect to port 1524 with netcat
