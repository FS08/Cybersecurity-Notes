# Bandit Level 10 → 11

## 🎯 Goal
The specialty for this level is to find the password in ``data.txt``, which contains ``base64 encoded data``.

## 🧰 Tools / Commands
```bash
ssh bandit10@bandit.labs.overthewire.org -p 2220
ls
cat data.txt
echo VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJyCg== | base64 --decode
```

Output of the ``first cat data.txt`` command :
```bash
bandit10@bandit:~$ cat data.txt 
VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJyCg==
```

Output of the ``echo & base64`` command :
```bash
bandit10@bandit:~$ echo VGhlIHBhc3N3b3JkIGlzIGR0UjE3M2ZaS2IwUlJzREZTR3NnMlJXbnBOVmozcVJyCg== | base64 --decode
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

## 🗝️ Password / Flag
`dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr`

## 🧠 Notes
- The password was encoded using base64, a common ``encoding scheme`` that represents ``binary data in ASCII format``.
- To decode it, I used the ``base64 --decode`` command. You can either echo the string into the command or decode directly from the file: ``base64 --decode data.txt``