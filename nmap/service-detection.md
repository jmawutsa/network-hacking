# Nmap Service Detection

**Date:** 2026-06-14
**Target:** Metasploitable 2
**Command:** `nmap -sV 192.168.9.2`

## Results
| Port | Service | Version |
|------|---------|---------|
| 21/tcp | ftp | vsftpd 2.3.4 |
| 22/tcp | ssh | OpenSSH 4.7 |
| 23/tcp | telnet | Linux telnetd |
| 80/tcp | http | Apache httpd 2.2.8 |

## What I Learned
- `-sV` reveals software versions
- vsftpd 2.3.4 has a known backdoor (CVE-2011-2523)
- Old versions are often vulnerable to public exploits

## Next Steps
Research vsftpd 2.3.4 exploit
