# Bandit Level 06 → 07

## 🎯 Goal
For this level the password is stored somewhere on the server ``(location/folder unknown)``.
The following specifications must be followed : ``33 bytes``, owned by ``user bandit7``, belongs to ``group bandit6``

## 🧰 Tools / Commands
```bash
ssh bandit6@bandit.labs.overthewire.org -p 2220
find / -type f -size 33c -user bandit7 -group bandit6 ! -executable | xargs file | grep text
cat /var/lib/dpkg/info/bandit7.password 
```

Output of the ``find`` command :
```bash
bandit6@bandit:~$ find / -type f -size 33c -user bandit7 -group bandit6 ! -executable | xargs file | grep text
find: ‘/root’: Permission denied
find: ‘/proc/tty/driver’: Permission denied
find: ‘/run/user/11006/systemd/inaccessible/dir’: Permission denied
...
find: ‘/drifter/drifter14_src/axTLS’: Permission denied
find: ‘/tmp’: Permission denied
/var/lib/dpkg/info/bandit7.password: ASCII text
```

## 🗝️ Password / Flag
`morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj`

## 🧠 Notes
- The arguments ``-user`` & `` -group`` lets me search for any files owned by the specified user and group.
- Since the ``location`` of the file was ``unknown`` I had to search all the folders on the server with ``/``