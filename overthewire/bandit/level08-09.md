# Bandit Level 08 → 09

## 🎯 Goal
The password is stored again inside the file ``data.txt``, but this time it has several ``duplicate words`` inside, and the password is the only line that ``appears once``.

## 🧰 Tools / Commands
```bash
ssh bandit8@bandit.labs.overthewire.org -p 2220
ls
cat data.txt
sort data.txt | uniq -u
```

Output of the ``sort & uniq`` command :
```bash
bandit8@bandit:~$ sort data.txt | uniq -u
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```

## 🗝️ Password / Flag
`4CKMh1JI91bUIZZPXDqGanal4xvAg0JM`

## 🧠 Notes
- ``sort``: reads the lines in data.txt and sorts them alphabetically. I used sort first because the uniq command only works on consecutive duplicate lines.
- ``uniq``: filters the sorted line and shows only lines that appear exactly once, ``-u`` stands for unique (unpaired).
- The use of pipe ``|`` lets me pass the output of ``sort`` directly into ``uniq``.