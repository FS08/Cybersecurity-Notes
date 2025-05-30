# 💣 HackTheBox Walkthroughs

This directory is for documenting HTB boxes you've worked on.

### 📁 Structure
- One markdown file per box: `boxname.md`
- Optional subfolders if you include screenshots, payloads, or notes

### 📝 What to Include
- Recon steps (nmap, gobuster, etc.)
- Exploitation method and tools used
- Privilege escalation path
- Flags obtained and how
- Post-exploitation steps
- Screenshots or logs if relevant

---

### 🧾 Template (Copy This into a New Box Writeup)

```markdown
# HTB Box Name - Difficulty Level

## 🧠 Recon
```bash
nmap -sC -sV -oN boxname.nmap target_ip
```

## 🔍 Web/Service Enumeration
Details on discovered services and potential attack vectors.

## 💥 Exploitation
Step-by-step to initial shell access.

## 🪜 Privilege Escalation
Technique and commands used to escalate privileges.

## 🏁 Flags
- user.txt: `flag{...}`
- root.txt: `flag{...}`

## 💬 Notes
- Important tricks or tools
- Resources or similar boxes
```
