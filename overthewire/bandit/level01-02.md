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
Flag Hash : `78d34bcd8ea46a1053e6fab74f8857b5b33161373bae597f278f576f29751d0c  -`

## 🧠 Notes
- When a file starts or has a dash (-), we have to open it with a ./ before.