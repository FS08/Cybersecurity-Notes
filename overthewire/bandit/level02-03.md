# Bandit Level 02 → 03

## 🎯 Goal
The password for this level is stored inside a ``name with spaces`` in it.
``ex: this is a filename.txt``

## 🧰 Tools / Commands
```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
ls
cat ./spaces\ in\ this\ filename
```

## 🗝️ Password / Flag
Flag Hash : `ac7f563748924c6ca8fe3e2893fa2189ab05b2a1ad731f349edcd00615fc39dc  -`

## 🧠 Notes
- Have to add \ for each separate word on the filename.