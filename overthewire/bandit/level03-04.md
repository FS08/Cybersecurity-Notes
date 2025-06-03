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
`2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ`

## 🧠 Notes
- When looking for hidden files use the parameter -a when using the command ls.