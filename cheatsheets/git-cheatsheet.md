# Git Cheat Sheet — Cybersecurity-Notes

Repo: `git@github.com:FS08/Cybersecurity-Notes.git`
Workflow: **one branch per topic** → commit as `DD.MM.YY - Topic` → push → PR → merge into `main` → clean up.

---

## 0. TL;DR — the daily loop

```bash
# Start of session (any PC)
cd ~/Cybersecurity-Notes
git switch main
git pull

# New topic
git switch -c THM-Firewall-Fundamentals

# ...write notes...

git add .
git commit -m "$(date +%d.%m.%y) - THM Firewall Fundamentals"
git push -u origin THM-Firewall-Fundamentals     # first push only; afterwards just: git push

# Open PR on GitHub → merge → then locally:
git switch main
git pull
git branch -d THM-Firewall-Fundamentals
```

---

## 1. Setup on a new laptop

### 1.1 Install Git

| OS | Command |
|---|---|
| Debian / Ubuntu / Kali | `sudo apt update && sudo apt install git` |
| macOS | `xcode-select --install` (or `brew install git`) |
| Windows | `winget install --id Git.Git -e` (use **Git Bash** afterwards) |

Check: `git --version`

### 1.2 Identity (must match your GitHub account)

```bash
git config --global user.name  "FS08"
git config --global user.email "YOUR_GITHUB_EMAIL"   # or the ID+FS08@users.noreply.github.com address
git config --global init.defaultBranch main
git config --global pull.rebase false                # merge on pull (simple, predictable)
git config --global core.editor "nano"               # or "code --wait", "vim"
git config --global push.autoSetupRemote true        # first `git push` sets upstream automatically
```

Check: `git config --global --list`

> Tip: the noreply email is in GitHub → Settings → Emails. Using it keeps your real email out of public commits.

### 1.3 SSH key for GitHub (recommended over HTTPS)

```bash
# 1. Generate a key (one per machine)
ssh-keygen -t ed25519 -C "fabio@$(hostname)"
# press Enter for default path, set a passphrase

# 2. Start the agent and load the key
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# 3. Copy the PUBLIC key
cat ~/.ssh/id_ed25519.pub
```

4. GitHub → **Settings → SSH and GPG keys → New SSH key** → paste → name it after the laptop (e.g. `MacBook-2026`).
5. Test:

```bash
ssh -T git@github.com
# Expected: "Hi FS08! You've successfully authenticated..."
```

macOS — keep the key in Keychain so you don't retype the passphrase:

```bash
# ~/.ssh/config
Host github.com
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_ed25519
```

### 1.4 (Optional) Sign commits with the same SSH key → "Verified" badge on your own commits

```bash
git config --global gpg.format ssh
git config --global user.signingkey ~/.ssh/id_ed25519.pub
git config --global commit.gpgsign true
```

Then add the same public key again on GitHub, this time choosing **Key type: Signing Key**.

### 1.5 Clone the repo

```bash
cd ~
git clone git@github.com:FS08/Cybersecurity-Notes.git
cd Cybersecurity-Notes
git branch -a        # see all local + remote branches
```

### 1.6 (Optional) GitHub CLI — open/merge PRs from the terminal

```bash
# install: sudo apt install gh  |  brew install gh  |  winget install GitHub.cli
gh auth login        # choose GitHub.com → SSH → use existing key
```

### 1.7 Retiring an old laptop

GitHub → Settings → SSH and GPG keys → delete that machine's key.

---

## 2. Starting work

```bash
git status                       # where am I, what changed?
git switch main                  # go to main
git pull                         # get latest from GitHub

git switch -c Rootme-Network     # create + switch to a NEW branch
git switch Rootme-Network        # switch to an EXISTING local branch
```

### Continue a branch you started on another PC

```bash
git fetch                        # learn about new remote branches
git branch -r                    # list remote branches
git switch WifiHacking           # auto-creates local branch tracking origin/WifiHacking
git pull                         # if it already existed locally, get the latest commits
```

> Older Git equivalent: `git checkout -b WifiHacking origin/WifiHacking`

### Branch naming (current convention)

`<Platform>-<Topic>` with dashes, no spaces → `THM-Network-Concepts`, `Rootme-FTP`, `WifiHacking`.

---

## 3. Saving work (commit)

```bash
git status                               # what changed
git diff                                 # see unstaged changes line by line
git add .                                # stage everything
git add path/to/file.md                  # stage one file
git add -p                               # stage chunk by chunk (interactive)

git commit -m "11.10.26 - THM Firewall Fundamentals"
```

### Auto-date the commit message

Add this alias once:

```bash
git config --global alias.dc '!f() { git commit -m "$(date +%d.%m.%y) - $*"; }; f'
```

Then:

```bash
git dc Rootme Telnet challenge
# → commit message: "11.10.26 - Rootme Telnet challenge"
```

### Fix the last commit

```bash
git commit --amend -m "11.10.26 - Correct message"   # change the message
git add forgotten-file.md
git commit --amend --no-edit                          # add a forgotten file
```

> ⚠️ Only amend commits you **haven't pushed yet**. If already pushed, you'd need `git push --force-with-lease` — fine on your own topic branch, never on `main`.

---

## 4. Pushing & merging

```bash
git push -u origin Rootme-Network     # first push of a new branch
git push                              # subsequent pushes
```

### Merge into main — option A: GitHub web (what you do now)

1. GitHub shows **"Compare & pull request"** after a push → create PR.
2. **Merge pull request** (or *Squash and merge* to collapse everything into one commit).
3. **Delete branch** button on GitHub.
4. Locally:

```bash
git switch main
git pull
git branch -d Rootme-Network
git fetch --prune            # remove references to branches deleted on GitHub
```

### Option B: GitHub CLI

```bash
gh pr create --fill --base main
gh pr merge --squash --delete-branch
git switch main && git pull
```

### Option C: merge locally, no PR

```bash
git switch main
git pull
git merge Rootme-Network
git push
git branch -d Rootme-Network
git push origin --delete Rootme-Network
```

---

## 5. Looking around

```bash
git log --oneline --graph --all --decorate   # visual history of all branches
git log -5                                   # last 5 commits
git log --oneline -- path/to/file.md         # history of one file
git show 95b7fba                             # what changed in a commit
git branch                                   # local branches (* = current)
git branch -a                                # local + remote
git branch -vv                               # local branches + what they track + ahead/behind
git remote -v                                # where the repo pushes/pulls
```

Handy alias:

```bash
git config --global alias.lg "log --oneline --graph --all --decorate"
# then: git lg
```

---

## 6. Keeping a topic branch up to date with main

If `main` moved on (e.g. you merged another topic) and you want those changes in your current branch:

```bash
git switch main && git pull
git switch THM-Firewall-Fundamentals
git merge main
```

---

## 7. "Oops" section

| Situation | Command |
|---|---|
| Discard changes to a file (not staged) | `git restore file.md` |
| Unstage a file (keep changes) | `git restore --staged file.md` |
| Discard **all** uncommitted changes | `git restore .` ⚠️ irreversible |
| Undo last commit, keep changes in files | `git reset --soft HEAD~1` |
| Undo a pushed commit safely (new "reverse" commit) | `git revert <hash>` |
| Started working on `main` by mistake (not committed) | `git switch -c Correct-Branch` — changes come with you |
| Committed on `main` by mistake (not pushed) | `git branch Correct-Branch` → `git reset --hard origin/main` → `git switch Correct-Branch` |
| Need to switch branch but have unfinished work | `git stash` → switch → come back → `git stash pop` |
| See stashes | `git stash list` |
| Renamed/moved files | `git mv old.md new/old.md` (keeps history clean) |
| Rename current branch | `git branch -m New-Name` |
| Delete local branch not merged | `git branch -D Branch-Name` ⚠️ |
| Lost a commit after a reset | `git reflog` → `git switch -c rescue <hash>` |

### Merge conflict

```bash
git status                     # shows conflicted files
# open file, look for <<<<<<< ======= >>>>>>> markers, keep what you want, delete markers
git add file.md
git commit                     # finishes the merge
# or give up:
git merge --abort
```

### Pull refuses because of local changes

```bash
git stash
git pull
git stash pop
```

---

## 8. Ignore stuff (`.gitignore`)

Useful for a notes repo (Obsidian / OS junk / captures):

```gitignore
.DS_Store
Thumbs.db
.obsidian/workspace*
.trash/
*.cap
*.pcap
*.hccapx
*.22000
```

> 🔐 Never commit real handshakes, captured hashes, cracked passwords, client data or flags you're not allowed to publish. If something slipped in: remove it, rotate anything sensitive, and remember it's still in history unless you rewrite it (`git filter-repo`).

Stop tracking a file that was already committed (keeps it on disk):

```bash
git rm --cached file.cap
echo "file.cap" >> .gitignore
git commit -m "$(date +%d.%m.%y) - Untrack capture file"
```

---

## 9. Quick reference

| I want to… | Command |
|---|---|
| Get latest | `git pull` |
| New topic branch | `git switch -c Name` |
| Change branch | `git switch Name` |
| Save | `git add .` → `git dc Topic` |
| Upload | `git push` |
| See what's going on | `git status` / `git lg` |
| Clean up after merge | `git switch main && git pull && git branch -d Name && git fetch --prune` |
