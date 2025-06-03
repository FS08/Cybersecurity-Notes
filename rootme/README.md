# 🧩 Root-Me Challenges

This folder contains notes and solutions for Root-Me challenges.

## 📁 Structure

Group files by challenge type:

```bash
rootme/
├── web-client/
│   └── js-obfuscation.md
├── web-server/
│   └── sqli-auth.md
└── cracking/
    └── hash-bypass.md
```

---

## 🧾 Template (Copy This for Each Challenge)

Paste this template for any Root-Me challenge:

````markdown
# Challenge Title - [Root-Me Challenge Link]

## 🧠 Summary
Short description of the challenge goal and category.

## 🧰 Tools Used
- CyberChef
- Burp Suite
- Python

## 💣 Exploitation / Solution
Step-by-step breakdown of how you solved it.
```bash
curl -X POST -d "user=admin&pass=' OR 1=1 --" http://target
```

## 🏁 Flag / Result
`flag{example_flag_here}`

## ✏️ Notes
- What was new or tricky?
- Any alternate paths or bypasses?
````

> Tip: Focus on your thought process and tools used, not just the answer.