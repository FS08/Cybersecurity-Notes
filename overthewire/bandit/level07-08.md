# Bandit Level 07 → 08

## 🎯 Goal
The password is inside a file ``data.txt`` containing multiple words and passwords associated. 
We are looking for the word ``millionth``, we will find the right password next to this word.

## 🧰 Tools / Commands
```bash
ssh bandit7@bandit.labs.overthewire.org -p 2220
ls
cat data.txt
grep "millionth" data.txt
```
Output of the ``grep`` command :
```bash
bandit7@bandit:~$ grep "millionth" data.txt 
millionth	dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

## 🗝️ Password / Flag
Flag Hash : `ace40b723a6747d96bc5696d8a9639a559fe244e51349aac17f4d1c70c888e95  -`

## 🧠 Notes
- The command grep ``(Global Regular Expression Print)`` that was used for this level, is used to ``scan a file line-wise`` and print those lines that match a given input ``ex: "millionth"``.