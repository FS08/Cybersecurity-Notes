# ⚙️ Scripts for Automation

Python or Bash scripts that you write to automate recon, parsing, scanning, or alerting.

## 📁 Structure

Each script file includes a docstring or is paired with a `.md` file.

```bash
scripts/
├── log-analyzer.py
├── bruteforce.py
└── log-analyzer.md
```

## 📝 What to Include
- Script functionality
- Sample input/output
- Use case and when to use it

---

## 🧾 Template (Copy This into a New Script or Comment Header)

Paste this to document a script:

````markdown
# Script Name - Purpose

## 🧠 Description
What does this script do?

## 🧪 Example Usage
```bash
python3 log-analyzer.py auth.log
```

## 💻 Code Snippet
```python
#!/usr/bin/env python3

with open("logfile.txt") as f:
    for line in f:
        if "ERROR" in line:
            print(line.strip())
```
````
