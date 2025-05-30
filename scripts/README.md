# ⚙️ Scripts for Automation

Python or Bash scripts that you write to automate recon, parsing, scanning, or alerting.

### 📁 Structure
- Name scripts clearly (e.g. `log-analyzer.py`, `brute.py`)
- Add usage instructions as comments or a separate `.md` file if complex

### 📝 What to Include
- Script functionality
- Sample input/output
- Use case and when to use it

---

### 🧾 Template (Copy This into a New Script or Comment Header)

```python
#!/usr/bin/env python3
# log-analyzer.py: Basic log parser with keyword alerts

import sys

with open(sys.argv[1]) as f:
    for line in f:
        if "ERROR" in line or "Failed" in line:
            print(line.strip())

# Usage:
# python3 log-analyzer.py /var/log/auth.log
```
