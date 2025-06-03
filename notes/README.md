# 📚 Concept-Based Notes

This folder contains topic-based notes for cybersecurity concepts, tools, techniques, and methodologies.

## 📁 Structure

Organize notes by subject:

```bash
notes/
├── web-security/
│   ├── xss.md
│   └── sqli.md
├── privilege-escalation/
│   ├── linux.md
│   └── windows.md
├── networking/
│   ├── tcp-ip.md
│   └── dns.md
```

---

## 🧾 S.T.E.P.S. Note Template (Copy This into a New Note)

Paste this template when creating a new concept note:

````markdown
# Topic Title (e.g., SQL Injection - SQLi)

## 🧠 S — Summary
Brief overview: What is it? Why does it matter? What systems/stages does it affect?

## 🧰 T — Tools
Tools used to demonstrate or exploit the concept.

```bash
sqlmap -u "http://example.com/page?id=1" --dbs
```

## 💣 E — Exploits / Examples
Common payloads or procedures used to demonstrate the concept.

```sql
' OR 1=1 --
```

## ✏️ P — Practice Notes
Notes from personal experience or labs:
- What worked?
- What mistakes were made?
- What’s important to remember?

## 🧾 S — Scripts / Snippets
Reusable code or commands.

```python
for pwd in open("rockyou.txt"):
    if try_login("admin", pwd.strip()):
        print("Password found:", pwd)
```
````

> ✅ This format keeps notes consistent and easy to review or share with teammates.