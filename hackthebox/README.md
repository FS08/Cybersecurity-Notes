# 💣 HackTheBox Walkthroughs

This directory is for documenting HTB boxes you've worked on.

## 📁 Structure

One file per machine, organized like so (Optional subfolders if I include screenshots, payloads, or notes):

```bash
hackthebox/
├── oopsie.md
├── netmon.md
└── mr-robot.md
```

## 📝 What to Include
- Recon steps (nmap, gobuster, etc.)
- Exploitation method and tools used
- Privilege escalation path
- Flags obtained and how
- Post-exploitation steps
- Screenshots or logs if relevant

---

## 🧾 Template (Copy This into a New Box Writeup)

Paste this for a new HTB Box:

````markdown
# Box Name - [HTB Box Link]

## 🧠 Recon
```bash
nmap -sC -sV -oN boxname.nmap target_ip
```

## 🔍 Web/Service Enumeration
What ports/services were found?

## 💥 Exploitation
How the initial shell was obtained.

## 🪜 Privilege Escalation
Technique to get root/system access.

## 🏁 Flags
- user.txt: `flag{...}`
- root.txt: `flag{...}`

## 💬 Notes
- Any gotchas or clever tricks
````