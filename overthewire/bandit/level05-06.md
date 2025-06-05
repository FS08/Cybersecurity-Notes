# Bandit Level 05 → 06

## 🎯 Goal
The password for this level is stored inside a file, in a folder, somewhere on the inhere directory.
The following specifications must be followed : ``human-readable``, ``1033 bytes``, ``not executable``

## 🧰 Tools / Commands
```bash
ssh bandit5@bandit.labs.overthewire.org -p 2220
ls
cd inhere
ls
find /home/bandit5/inhere -type f -size 1033c ! -executable | xargs file | grep text
cat /maybehere07/.file2
```
Output of the ``find`` command :
```bash
bandit5@bandit:~/inhere$ find /home/bandit5/inhere -type f -size 1033c ! -executable | xargs file | grep text
/home/bandit5/inhere/maybehere07/.file2: ASCII text, with very long lines (1000)
```

## 🗝️ Password / Flag
`HWasnPhtq9AVKe0dmk45nxy20cvUa6EG`

## 🧠 Notes
- The password was inside a random folder in the inhere directory, so instead of searching 1 by 1 I checked directly ``/home/bandit5/inhere``.
- For the other parameters here is the explanation :
  - ``-type f`` : only look for regular files 
  - ``-size 1033c`` : only files that are exactly 1033 bytes in size (c = bytes)
  - ``! -executable`` : excludes files that are executable
  - ``xargs`` : takes the output of the find command and passes them as arguments to the file command
  - ``file``: analyzes the content of each file and prints its type (ex: ASCII, binary, etc...)
  - ``grep text`` : filters the output to only show lines that contain the word "text"