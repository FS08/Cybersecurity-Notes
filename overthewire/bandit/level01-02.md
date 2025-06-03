# Bandit Level 01 → 02

## 🎯 Goal
The challenge for this level is to be able to read the password that is written inside a ``file called "-"``.

## 🧰 Tools / Commands
```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
ls
cat ./-
```

## 🗝️ Password / Flag
`263JGJPfgU6LtdEvgfWU1XP5yac29mFx`

## 🧠 Notes
- When a file starts or has a dash (-), we have to open it with a ./ before.