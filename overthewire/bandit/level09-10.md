# Bandit Level 09 → 10

## 🎯 Goal
For this level the password is stored inside the ``data.txt`` file, in ``one of the few human-readable strings``, preceded by several ``=``characters.

## 🧰 Tools / Commands
```bash
ssh bandit9@bandit.labs.overthewire.org -p 2220
ls
cat data.txt
strings data.txt | grep ======
```

Output of the ``strings & grep`` command :
```bash
bandit9@bandit:~$ strings data.txt | grep ======
========== the
========== password{k
=========== is
========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
```

## 🗝️ Password / Flag
`FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey`

## 🧠 Notes
- ``strings``: this command looks for printable strings in a file. A string is any sequence of 4 or more printable characters.
- For this level I first used the command ``strings ===== data.txt``, which didn't quite give me the output I wished for, so then I thought on adding the ``| grep ======``, this gave me exactly all the lines with the ``=`` characters.