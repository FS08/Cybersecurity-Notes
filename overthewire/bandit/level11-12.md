# Bandit Level 11 → 12

## 🎯 Goal
The password for the next level is stored in a file called ``data.txt``, which contains ``ROT13-encoded`` text.

## 🧰 Tools / Commands
```bash
ssh bandit11@bandit.labs.overthewire.org -p 2220
ls
cat data.txt
cat data.txt | tr 'A-Za-z' 'N-Za-Mn-za-m'
```

Output of the ``first cat data.txt`` command :
```bash
bandit11@bandit:~$ cat data.txt 
Gur cnffjbeq vf 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4
```

Output of the ``echo & base64`` command :
```bash
bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```

## 🗝️ Password / Flag
`7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4`

## 🧠 Notes  

- The file is encoded with ``ROT13``, which is a simple letter substitution cipher.
- ``ROT13`` shifts each letter ``13 positions forward`` in the alphabet. If it goes past ``Z``, it wraps back to ``A``.
  - ``Example:`` A → N, B → O, ..., M → Z, N → A, ..., Z → M.
  - Same thing applies to lowercase: a → n, b → o, ..., z → m.
- How the command works:
  - ``cat data.txt``: prints the encoded contents of the file.
  - ``tr 'A-Za-z' 'N-ZA-Mn-za-m'``: tells the system to match every letter from A-Z and a-z, and replace each letter 13 positions ahead.