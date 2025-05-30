# 🛡️ Cybersecurity Notes & Labs

Welcome to my cybersecurity notes!  
This repo is a structured, hands-on knowledge base I use to document what I learn while preparing for a cybersecurity internship and solving CTFs.

It includes notes from:
- TryHackMe labs
- HackTheBox boxes
- Scripting and automation
- Blue Team tools (SIEM, detection, forensics)
- Red Team methods (pentesting, privilege escalation)
- Cheat sheets and personal writeups

---

## 📁 Structure

```bash
cybersecurity-notes/
├── tryhackme/              # Notes and writeups from THM rooms
├── hackthebox/             # HTB box walkthroughs
├── notes/                  # Concept-based notes (XSS, networking, etc.)
├── cheatsheets/            # Copy-paste command summaries
├── scripts/                # Python/Bash automation for pentesting/SOC
└── glossary.md             # My personal infosec dictionary
```

---

## 📝 My Learning Plan & Progress Tracker

This is a living list of tasks and accomplishments that I update regularly as I learn and explore cybersecurity topics. I use it to track what I've done, what I'm currently working on, and what I plan to do next.

### ✅ Completed
- [x] Finished TryHackMe 'Intro to Cyber Security'
- [x] Set up Kali VM and note-taking GitHub repo
- [x] Wrote initial glossary.md and README.md

### 🔄 In Progress
- [ ] Practice SQLi/XSS on DVWA
- [ ] Work through 'Log Analysis' and 'SIEM' rooms
- [ ] Add full write-up for Mr. Robot (HTB Starting Point)
- [ ] Python script for brute force with `requests`
- [ ] Complete 'Linux Fundamentals' rooms (1–3)

### ⬜ To Do / Upcoming
- [ ] Complete 'Windows Privilege Escalation' lab
- [ ] Create a SIEM dashboard (Splunk or Wazuh)
- [ ] Explore memory forensics using Volatility
- [ ] Build and document a custom `log-analyzer.py` script
- [ ] Write a sample vulnerability report
- [ ] Study Windows event logs (Event Viewer, Sysmon)
- [ ] Analyze `.pcap` files in Wireshark
- [ ] Join a live CTF from CTFtime.org
- [ ] Solve 'Vulnversity' box on TryHackMe
- [ ] Learn basic usage of `nmap` and `netcat`

---

## 🔄 How I Update Progress

I update this table weekly as I complete TryHackMe rooms, CTFs, write reports, or build scripts.  
Each task I finish is also documented in its relevant folder with:
- Screenshots or payloads
- Lessons learned
- Exploits or logs used

---

## 🧭 Modular Learning Path (To-Do Style)

Below is a categorized learning path I use to track progress and add new goals as I grow. ✅ = done, 🔄 = in progress, ⬜ = not started.

### 🔐 Foundations
- [x] Understand CIA triad, threats, attack types
- [x] TryHackMe: 'Intro to Cyber Security'
- [x] Linux CLI basics + Linux Fundamentals 1–3
- [x] Set up Kali Linux VM and notes repo

### 🌐 Networking & Enumeration
- [ ] TryHackMe: 'Networking Fundamentals'
- [ ] Learn: `nmap`, `netcat`, `dig`, `traceroute`
- [ ] Run banner grabs and create TCP/IP notes

### 🌐 Web Security & OWASP Top 10
- [ ] TryHackMe: 'OWASP Top 10'
- [ ] TryHackMe: 'Burp Suite Basics'
- [ ] Practice XSS, SQLi, IDOR on DVWA
- [ ] Start notes on common payloads & mitigations

### 🔍 Scanning & Recon Tools
- [ ] TryHackMe: 'Vulnversity'
- [ ] Practice: `gobuster`, `nikto`, `dirsearch`
- [ ] Write a Python scanner (open ports, dirs)

### 🚨 Privilege Escalation
- [ ] TryHackMe: 'Linux Privilege Escalation'
- [ ] Learn: linPEAS, SUID, PATH hijack, `sudo` rules
- [ ] Document escalation paths with examples
- [ ] TryHackMe: 'Windows Privilege Escalation'

### 🧪 Scripting for Security
- [ ] Learn: Python (`requests`, `argparse`, `subprocess`, `socket`)
- [ ] Scripts: brute-forcer, recon, log parser
- [ ] Add useful tools to `scripts/` directory

### 🛡️ Blue Team (SOC + Logs)
- [ ] TryHackMe: 'SIEM', 'Splunk Basics', 'Log Analysis'
- [ ] Explore `auth.log`, `syslog`, Windows event logs
- [ ] Build basic SIEM dashboard & alert script

### 🔎 Digital Forensics & Static Analysis
- [ ] TryHackMe: 'Digital Forensics Introduction'
- [ ] Use: Volatility, CyberChef, exiftool
- [ ] Analyze memory dumps or malware samples

### 🧨 Realistic Pentest Practice
- [ ] HackTheBox: Starting Point (Oopsie, Mr. Robot)
- [ ] Redo Vulnversity with full report
- [ ] Simulate a complete pentest from recon to reporting

### 🧾 Internship Readiness Tasks
- [ ] Write vulnerability report template
- [ ] Script: log parser or alert generator
- [ ] Practice packet analysis with `.pcap` in Wireshark
- [ ] Record a 5-minute walkthrough or demo