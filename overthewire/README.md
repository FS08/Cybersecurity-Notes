# 🧪 OverTheWire Wargames

This folder contains walkthroughs and command logs for OverTheWire games (Bandit, Narnia, etc.).

## 📁 Structure

Organize by wargame and level:

```bash
overthewire/
├── bandit/
│   ├── level00.md
│   ├── level01-02.md
└── narnia/
    └── level01-02.md
```

---

## 🧾 Template (Copy This for Each Level)

Paste this for any OTW level solution:

````markdown
# Bandit Level XX → XX

## 🎯 Goal
What must be done to pass this level?

## 🧰 Tools / Commands
```bash
ssh banditXX@bandit.labs.overthewire.org -p 2220
cat readme
find / -user banditXX -group banditXX -size 33c 2>/dev/null
```

## 🗝️ Password / Flag
`<paste password or flag>`

## 🧠 Notes
- Key command to remember?
- What was tricky or new?
````