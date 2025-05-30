# 📝 Cheatsheets

Quick-access files with commands and tool references.

### 📁 Structure
- One markdown file per tool/topic:
  - `nmap.md`
  - `burp-suite.md`
  - `wireshark.md`

### 📝 What to Include
- Common flags and what they do
- Examples of usage
- One-liners or useful scripts

---

### 🧾 Template (Copy This into a New Cheatsheet)

```markdown
# Tool Name (e.g., Nmap Cheatsheet)

## 🔍 Basic Scan
```bash
nmap target
```

## 📦 Full TCP Scan
```bash
nmap -p- -sV -T4 target
```

## 🛠 Service Detection
```bash
nmap -sV -sC -A target
```

## 🎯 Common Options
- `-T4` = faster timing
- `-sC` = default scripts
- `-sV` = version detection
```
