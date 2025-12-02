# Bandit Level 04 → 05

## 🎯 Goal
The password for the next level is stored in the ``only human-readable`` file in the inhere directory.

## 🧰 Tools / Commands
```bash
ssh bandit4@bandit.labs.overthewire.org -p 2220
ls
cd inhere
ls -a
file ./-*
cat ./-file07
```
Output of the ``file ./-*`` command :
```bash
bandit4@bandit:~/inhere$ file ./-*
./-file00: PGP Secret Sub-key -
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
bandit4@bandit:~/
```

## 🗝️ Password / Flag
Flag Hash : `0795ff104beb65750497a2a18dda509205d2530cae2501b18851f772dde1508d  -`

## 🧠 Notes
- Tip: if your terminal is messed up, try the ``reset`` command.
- The command ``file ./<filename>``, allows us to find human-readable files and see other type of files like ``data``.
