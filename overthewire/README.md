# 🧪 OverTheWire Wargames

This folder contains walkthroughs and command logs for OverTheWire games (Bandit, Narnia, etc.).

---

## 📁 Structure

```bash
overthewire/
├── bandit/
│   ├── level00.md
│   ├── level01.md
├── narnia/
│   └── level01.md
```

---

## 🧾 Template (Copy This for Each Level)

```markdown
# Bandit Level XX → Level XX+1

## 🎯 Goal
Describe what the level requires you to do.

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

> Always test in a fresh shell to verify what you learned!
```
