# 📝 Cheatsheets

Quick-access files with commands and tool references.

## 📁 Structure

Each file is a single tool or theme:

```bash
cheatsheets/
├── nmap.md
├── burp.md
└── wireshark.md
```

## 📝 What to Include
- Common flags and what they do
- Examples of usage
- One-liners or useful scripts

---

## 🧾 Template (Copy This into a New Cheatsheet)

Paste this for a new cheatsheet:

````markdown
# Tool Name Cheatsheet (e.g., Nmap)

## 🔍 Basic Usage
```bash
nmap target
```

## ⚙️ Common Flags

| Option | Description |
|--------|-------------|
| -sS    | SYN scan    |
| -sV    | Service detection |
| -A     | Aggressive scan |

## 🧪 Example
```bash
nmap -sV -p- -T4 10.10.10.10
```

## 💡 Notes
- Fast scanning tips
- Scripts or extras
````