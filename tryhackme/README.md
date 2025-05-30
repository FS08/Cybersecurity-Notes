# 🧪 TryHackMe Writeups

This folder contains notes and full writeups for TryHackMe rooms.

### 📁 Structure
- One subfolder or markdown file per room
- Use consistent naming like `vulnversity.md`, `owasp-top10.md`

### 📝 What to Include
- Room objective and topic
- Key tools and commands used
- Enumeration steps
- Exploits and payloads
- Flags and how they were captured
- Lessons learned

---

### 🧾 Template (Copy This into a New Room Writeup)

```markdown
# Room Name - [TryHackMe Room Link]

## 🧠 Summary
Brief overview of what the room teaches and its objectives.

## 🧰 Tools Used
- nmap
- gobuster
- ftp

## 🔍 Enumeration
```bash
nmap -sV -p- target_ip
```

## 💥 Exploitation
Describe vulnerability and how you exploited it.

## 🪜 Privilege Escalation (if any)
What techniques were used?

## 🏁 Flags Captured
- User.txt: `flag{...}`
- Root.txt: `flag{...}`

## 🧠 Lessons Learned
- What worked, what didn’t?
- What would I do differently next time?
```
