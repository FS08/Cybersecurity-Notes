# Bandit Level 03 → 04

## 🎯 Goal
For this level the challenge is to read the password that is inside a ``hidden file``.

## 🧰 Tools / Commands
```bash
ssh bandit3@bandit.labs.overthewire.org -p 2220
ls
cd inhere
ls -a
cat ./...Hiding-From-You 
```

## 🗝️ Password / Flag
Flag Hash : `61160146c88cc8feee7624ef53eef495cc70dffc830f5185340a8e3da3cf0f7d  -`

## 🧠 Notes
- When looking for hidden files use the parameter -a when using the command ls.